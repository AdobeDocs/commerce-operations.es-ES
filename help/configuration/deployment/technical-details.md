---
title: Detalles técnicos
description: Obtenga información sobre los detalles técnicos de la implementación de canalización, los tipos de configuraciones y los flujos de trabajo recomendados.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 0%

---


# Detalles técnicos

En este tema se tratan los detalles de implementación técnica sobre la implementación de canalizaciones en Commerce 2.2 y posteriores. Las mejoras se pueden dividir en las siguientes áreas:

- [Administración de configuración](#configuration-management)
- [Cambios en la administración](#changes-in-the-admin)
- [Instalar y quitar cron](#install-and-remove-cron)

En este tema también se analiza el [flujo de trabajo recomendado](#recommended-workflow) para la implementación de canalizaciones y proporciona algunos ejemplos para ayudarle a comprender cómo funciona.

Antes de comenzar, revise la [Requisitos previos para los sistemas de desarrollo, compilación y producción](../deployment/prerequisites.md).

## Administración de configuración

Para permitirle sincronizar y mantener la configuración de sus sistemas de desarrollo y producción, utilice el siguiente esquema de anulación.

![Cómo se determinan los valores de las variables de configuración](../../assets/configuration/override-flow-diagram.png)

Como se muestra en el diagrama, los valores de configuración se utilizan en el siguiente orden:

1. Las variables de entorno, si existen, anulan todos los demás valores.
1. Desde los archivos de configuración compartidos `env.php` y `config.php`. Valores en `env.php` anular valores en `config.php`.
1. A partir de los valores almacenados en la base de datos.
1. Si no existe ningún valor en ninguno de esos orígenes, se utiliza el valor predeterminado o NULL.

### Administrar la configuración compartida

La configuración compartida se almacena en `app/etc/config.php`, que debería estar en el control de código fuente.

Establezca la configuración compartida en Admin en su desarrollo (o Adobe Commerce en la infraestructura de nube) _integración_) y escribir la configuración en `config.php` usando la variable [`magento app:config:dump` command](../cli/export-configuration.md).

### Administrar la configuración específica del sistema

La configuración específica del sistema se almacena en `app/etc/env.php`, que debería _not_ estar en control de código fuente.

Establezca la configuración específica del sistema en el Administrador del sistema de desarrollo (o Adobe Commerce en la integración de la infraestructura de nube) y escriba la configuración en `env.php` usando la variable [`magento app:config:dump` command](../cli/export-configuration.md).

Este comando también escribe la configuración confidencial en `env.php`.

### Administrar la configuración confidencial

La configuración confidencial también se almacena en `app/etc/env.php`.

Puede administrar la configuración confidencial de cualquiera de estas formas:

- Variables de entorno
- Guarde la configuración confidencial en `env.php` en su sistema de producción utilizando [`magento config:set:sensitive` command](../cli/set-configuration-values.md)

### Ajustes de configuración bloqueados en el Administrador

Cualquier configuración de `config.php` o `env.php` están bloqueados en el Administrador; es decir, esa configuración no se puede cambiar en Admin.
Utilice la variable [`magento config:set` o `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) para cambiar la configuración de la variable `config.php` o `env.php` archivos.

## El administrador de comercio

El administrador muestra el siguiente comportamiento mientras está en modo de producción:

- No se pueden habilitar ni deshabilitar los tipos de caché en el Administrador
- La configuración del desarrollador no está disponible (**Almacenes** > Configuración > **Configuración** > Avanzado > **Desarrollador**), incluido:

   - Minimizar CSS, JavaScript y HTML
   - Combinación de CSS y JavaScript
   - Compilación LESS del lado del servidor o del lado del cliente
   - Traducciones en línea
   - Como se ha comentado anteriormente, cualquier configuración de `config.php` o `env.php` está bloqueado y no se puede editar en el administrador.
   - Solo puede cambiar la configuración regional de administración a los idiomas utilizados por los temas implementados

      La siguiente figura muestra un ejemplo de **Configuración de la cuenta** > **Configuración regional de la interfaz** en la lista Administración que muestra solo dos configuraciones regionales implementadas:

      ![Solo puede cambiar la configuración regional de administración a configuraciones regionales implementadas](../../assets/configuration/split-deploy-admin-locale.png)

- No puede cambiar las configuraciones regionales para ningún ámbito mediante el administrador.

   Se recomienda realizar estos cambios antes de cambiar al modo Producción.

   Aún puede configurar la configuración regional mediante variables de entorno o la variable `config:set` Comando CLI con la ruta `general/locale/code`.

## Instalar y quitar cron

En la versión 2.2 por primera vez, le ayudamos a configurar su trabajo cron proporcionando la variable [`magento cron:install` command](../cli/configure-cron-jobs.md). Este comando configura un crontab como el usuario que ejecuta el comando.

Además, puede quitar la crontab utilizando la variable `magento cron:remove` comando.

## Flujo de trabajo de implementación de canalización recomendado

El diagrama siguiente muestra cómo se recomienda utilizar la implementación de canalización para administrar la configuración.

![Flujo de trabajo de implementación de canalización recomendado](../../assets/configuration/split-deploy-workflow.png)

### Sistema de desarrollo

En el sistema de desarrollo, realice cambios de configuración en Admin y genere la configuración compartida. `app/etc/config.php` y la configuración específica del sistema, `app/etc/env.php`. Compruebe el código de comercio y la configuración compartida en el control de código fuente y colóquelo en el servidor de compilación.

También debe instalar extensiones y personalizar el código de comercio en el sistema de desarrollo.

En el sistema de desarrollo:

1. Establezca la configuración en Administración.

1. Utilice la variable `magento app:config:dump` para escribir la configuración en el sistema de archivos.

   - `app/etc/config.php` es la configuración compartida, que contiene todos los ajustes _except_ ajustes confidenciales y específicos del sistema. Este archivo debe estar en el control de código fuente.
   - `app/etc/env.php` es la configuración específica del sistema, que contiene configuraciones que son únicas para un sistema en particular (por ejemplo, nombres de host y números de puerto). Este archivo debe _not_ estar en control de código fuente.

1. Añada el código modificado y la configuración compartida al control de código fuente.

1. Para eliminar el código php generado y los archivos de recursos estáticos durante el desarrollo, ejecute los siguientes comandos:

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

Después de ejecutar los comandos para borrar los recursos, Commerce genera archivos de trabajo.

>[!WARNING]
>
>Tenga cuidado con el enfoque anterior. Al eliminar `.htacces`en el `generated` o `pub` puede causar problemas.

### Generar sistema

El sistema de compilación compila código y genera archivos de vista estáticos para los temas registrados en Commerce. No necesita una conexión con la base de datos de Commerce; solo necesita el código base de comercio.

En el sistema de compilación:

1. Extraiga el archivo de configuración compartida del control de código fuente.
1. Utilice la variable `magento setup:di:compile` para compilar código.
1. Utilice la variable `magento setup:static-content:deploy -f` para actualizar los archivos estáticos de vista de archivos.
1. Compruebe las actualizaciones en el control de código fuente.

>[!INFO]
>
>Consulte [Estrategias de implementación para archivos de vista estáticos](../cli/static-view-file-strategy.md).

### Sistema de producción

En su sistema de producción (es decir, su almacén activo), extraiga los recursos generados y las actualizaciones de código del control de código fuente y establezca los ajustes de configuración sensibles y específicos del sistema utilizando la línea de comandos o las variables de entorno.

En el sistema de producción:

1. Inicie el modo de mantenimiento.
1. Extraiga las actualizaciones de código y configuración del control de código fuente.
1. Si utiliza Adobe Commerce, detenga a los trabajadores de la cola.
1. Utilice la variable `magento app:config:import` para importar los cambios de configuración en el sistema de producción.
1. Si ha instalado componentes que han cambiado el esquema de la base de datos, ejecute `magento setup:upgrade --keep-generated` para actualizar el esquema y los datos de la base de datos, preservando los archivos estáticos generados.
1. Para definir la configuración específica del sistema, utilice la variable `magento config:set` variables de entorno o comando.
1. Para definir la configuración confidencial, utilice la variable `magento config:sensitive:set` variables de entorno o comando.
1. Limpio (también denominado _flush_) la caché.
1. Fin del modo de mantenimiento.

## Comandos de administración de configuración

Proporcionamos los siguientes comandos para ayudarle a administrar la configuración:

- [`magento app:config:dump`](../cli/export-configuration.md) para escribir los ajustes de configuración de administración en `config.php` y `env.php` (excepto para la configuración sensible)
- [`magento config:set`](../cli/set-configuration-values.md) para establecer los valores de configuración específica del sistema en el sistema de producción.

   Utilice el `--lock` para bloquear la opción en Admin (es decir, hacer que la configuración sea ineditable). Si una configuración ya está bloqueada, use la `--lock` para cambiar la configuración.

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) para establecer los valores de configuración confidencial en el sistema de producción.
- [`magento app:config:import`](../cli/import-configuration.md) para importar los cambios de configuración desde `config.php` y `env.php` al sistema de producción.

## Ejemplos de administración de configuración

Esta sección muestra ejemplos de administración de la configuración para que pueda ver cómo se realizan los cambios en `config.php` y `env.php`.

### Cambiar la configuración regional predeterminada

Esta sección muestra los cambios realizados en `config.php` cuando cambie la unidad de peso predeterminada mediante el administrador (**Almacenes** > Configuración > **Configuración** > General > **General** > **Opciones de configuración regional**).

Después de realizar el cambio en Administración, ejecute `bin/magento app:config:dump` escribir el valor en `config.php`. El valor se escribe en la variable `general` matriz bajo `locale` como el siguiente fragmento de código de `config.php` muestra:

```php
'general' =>
    array (
        'locale' =>
        array (
            'code' => 'en_US',
            'timezone' => 'America/Chicago',
            'weight_unit' => 'kgs'
        )
    )
```

### Cambiar varias opciones de configuración

Esta sección trata sobre cómo realizar los siguientes cambios de configuración:

- Adición de un sitio web, tienda y vista de tienda (**Almacenes** > Configuración > **Todas las tiendas**)
- Cambio del dominio de correo electrónico predeterminado (**Almacenes** > Configuración > **Configuración** > Clientes > **Configuración del cliente**)
- Configuración del nombre de usuario y la contraseña de API de PayPal (**Almacenes** > Configuración > **Configuración** > Ventas > **Métodos de pago** > **PayPal** > **Configuración requerida de PayPal**)

Después de realizar el cambio en Administración, ejecute `bin/magento app:config:dump` en su sistema de desarrollo. Esta vez, no todos los cambios están escritos en `config.php`; de hecho, solo el sitio web, la tienda y la vista de tienda se escriben en ese archivo como se muestra en los siguientes fragmentos.

### config.php

`config.php` contiene:

- Cambios en el sitio web, la tienda y la vista de tienda.
- Configuración del motor de búsqueda no específica del sistema
- Configuración de PayPal no sensible
- Comentarios que le informan de configuraciones sensibles que se omitieron en `config.php`

`websites` matriz:

```php
      'new' =>
      array (
        'website_id' => '2',
        'code' => 'new',
        'name' => 'New website',
        'sort_order' => '0',
        'default_group_id' => '2',
        'is_default' => '0',
      ),
```

`groups` matriz:

```php
      2 =>
      array (
        'group_id' => '2',
        'website_id' => '2',
        'code' => 'newstore',
        'name' => 'New store',
        'root_category_id' => '2',
        'default_store_id' => '2',
      ),
```

`stores` matriz:

```php
     'newview' =>
      array (
        'store_id' => '2',
        'code' => 'newview',
        'website_id' => '2',
        'group_id' => '2',
        'name' => 'New store view',
        'sort_order' => '0',
        'is_active' => '1',
      ),
```

`payment` matriz:

```php
      'payment' =>
      array (
        'paypal_express' =>
        array (
          'active' => '0',
          'in_context' => '0',
          'title' => 'PayPal Express Checkout',
          'sort_order' => NULL,
          'payment_action' => 'Authorization',
          'visible_on_product' => '1',
          'visible_on_cart' => '1',
          'allowspecific' => '0',
          'verify_peer' => '1',
          'line_items_enabled' => '1',
          'transfer_shipping_options' => '0',
          'solution_type' => 'Mark',
          'require_billing_address' => '0',
          'allow_ba_signup' => 'never',
          'skip_order_review_step' => '1',
        ),
```

### env.php

La configuración predeterminada específica del sistema de dominio de correo electrónico se escribe en `app/etc/env.php`.

La configuración de PayPal no está escrita en ningún archivo porque la variable `bin/magento app:config:dump` no escribe la configuración confidencial. Debe configurar la configuración de PayPal en el sistema de producción mediante los siguientes comandos:

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
