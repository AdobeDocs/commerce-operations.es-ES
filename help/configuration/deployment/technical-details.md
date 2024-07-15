---
title: Detalles técnicos
description: Obtenga información sobre los detalles técnicos de la implementación de la canalización, los tipos de configuraciones y los flujos de trabajo recomendados.
exl-id: a396d241-f895-4414-92af-3abf3511e62a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 0%

---

# Detalles técnicos

En este tema se tratan los detalles de implementación técnica de la canalización en Commerce 2.2 y versiones posteriores. Las mejoras se pueden dividir en las siguientes áreas:

- [Administración de configuración](#configuration-management)
- [Cambios en la administración](#changes-in-the-admin)
- [Instalar y eliminar cron](#install-and-remove-cron)

En este tema también se describe el [flujo de trabajo recomendado](#recommended-workflow) para la implementación de canalizaciones y se proporcionan algunos ejemplos para ayudarle a comprender cómo funciona.

Antes de comenzar, revise los [requisitos previos para sus sistemas de desarrollo, compilación y producción](../deployment/prerequisites.md).

## Administración de configuración

Para permitirle sincronizar y mantener la configuración de sus sistemas de desarrollo y producción, utilice el siguiente esquema de anulación.

![Cómo se determinan los valores de las variables de configuración](../../assets/configuration/override-flow-diagram.png)

Como se muestra en el diagrama, los valores de configuración se utilizan en el siguiente orden:

1. Las variables de entorno, si existen, anulan todos los demás valores.
1. De los archivos de configuración compartidos `env.php` y `config.php`. Los valores de `env.php` anulan los valores de `config.php`.
1. A partir de los valores almacenados en la base de datos.
1. Si no existe ningún valor en ninguno de estos orígenes, se utiliza el valor predeterminado o NULL.

### Administrar la configuración compartida

La configuración compartida se almacena en `app/etc/config.php`, que debe estar en el control de código fuente.

Establezca la configuración compartida en Admin en su sistema de desarrollo (o Adobe Commerce en la infraestructura en la nube _integration_) y escriba la configuración en `config.php` mediante el comando [`magento app:config:dump`](../cli/export-configuration.md).

### Administrar la configuración específica del sistema

La configuración específica del sistema está almacenada en `app/etc/env.php`, que debería _no_ estar en el control de código fuente.

Establezca la configuración específica del sistema en el administrador del sistema de desarrollo (o Adobe Commerce en la integración de la infraestructura en la nube) y escriba la configuración en `env.php` mediante el comando [`magento app:config:dump`](../cli/export-configuration.md).

Este comando también escribe la configuración confidencial en `env.php`.

### Administrar la configuración confidencial

La configuración confidencial también se almacena en `app/etc/env.php`.

Puede administrar la configuración confidencial de cualquiera de las siguientes maneras:

- Variables de entorno
- Guarde la configuración confidencial en `env.php` en el sistema de producción mediante el comando [`magento config:set:sensitive` ](../cli/set-configuration-values.md)

### Ajustes de configuración bloqueados en el administrador

Cualquier configuración de `config.php` o `env.php` está bloqueada en el administrador; es decir, dicha configuración no se puede cambiar en el administrador.
Use el comando [`magento config:set` o `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) para cambiar la configuración de los archivos `config.php` o `env.php`.

## El administrador de Commerce

El administrador muestra el siguiente comportamiento mientras está en modo de producción:

- No puede habilitar ni deshabilitar los tipos de caché en el Administrador
- La configuración de desarrollador no está disponible (**Tiendas** > Configuración > **Configuración** > Avanzada > **Desarrollador**), e incluye:

   - Minimizar CSS, JavaScript y HTML
   - Combinar CSS y JavaScript
   - Compilación LESS del lado del servidor o del lado del cliente
   - Traducciones en línea
   - Como se mencionó anteriormente, cualquier configuración en `config.php` o `env.php` está bloqueada y no se puede editar en el Administrador.
   - Puede cambiar la configuración regional del administrador solo a los idiomas utilizados por las temáticas implementadas

     La siguiente figura muestra un ejemplo de la lista **Configuración de cuenta** > **Configuración regional de la interfaz** en el Administrador que muestra solo dos configuraciones regionales implementadas:

     ![Solo puede cambiar la configuración regional del administrador a configuraciones regionales implementadas](../../assets/configuration/split-deploy-admin-locale.png)

- No puede cambiar las configuraciones de configuración regional de ningún ámbito mediante el Administrador.

  Se recomienda realizar estos cambios antes de cambiar al modo de producción.

  Puede seguir configurando la configuración regional mediante variables de entorno o el comando CLI `config:set` con la ruta de acceso `general/locale/code`.

## Instalar y eliminar cron

En la versión 2.2 por primera vez, le ayudamos a configurar su trabajo cron proporcionando el comando [`magento cron:install` ](../cli/configure-cron-jobs.md). Este comando configura un crontab como el usuario que ejecuta el comando.

Además, puede quitar el crontab mediante el comando `magento cron:remove`.

## Flujo de trabajo de implementación de canalización recomendado

El diagrama siguiente muestra cómo se recomienda utilizar la implementación de canalización para administrar la configuración.

![Flujo de trabajo de implementación de canalización recomendado](../../assets/configuration/split-deploy-workflow.png)

### Sistema de desarrollo

En el sistema de desarrollo, realice cambios de configuración en el Administrador y genere la configuración compartida `app/etc/config.php` y la configuración específica del sistema `app/etc/env.php`. Compruebe el código Commerce y la configuración compartida en el control de código fuente y empújelo al servidor de compilación.

También debe instalar extensiones y personalizar el código de Commerce en el sistema de desarrollo.

En su sistema de desarrollo:

1. Establezca la configuración en el Administrador de.

1. Utilice el comando `magento app:config:dump` para escribir la configuración en el sistema de archivos.

   - `app/etc/config.php` es la configuración compartida, que contiene todas las opciones de configuración _excepto_ las opciones confidenciales y específicas del sistema. Este archivo debe estar en el control de código fuente.
   - `app/etc/env.php` es la configuración específica del sistema, que contiene opciones exclusivas de un sistema concreto (por ejemplo, nombres de host y números de puerto). Este archivo debería _no_ estar en el control de código fuente.

1. Agregue el código modificado y la configuración compartida al control de código fuente.

1. Para eliminar el código php generado y los archivos de recursos estáticos mientras se encuentra en desarrollo, ejecute los siguientes comandos:

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

Después de ejecutar los comandos para borrar los recursos, Commerce genera archivos de trabajo.

>[!WARNING]
>
>Tenga cuidado con el enfoque anterior. Eliminar el archivo `.htacces`s en la carpeta `generated` o `pub` puede causar problemas.

### Sistema de compilación

El sistema de generación compila código y genera archivos de vista estática para las temáticas registradas en Commerce. No necesita una conexión a la base de datos de Commerce; solo necesita el código base de Commerce.

En su sistema de compilación:

1. Extraer el archivo de configuración compartida del control de código fuente.
1. Utilice el comando `magento setup:di:compile` para compilar el código.
1. Utilice el comando `magento setup:static-content:deploy -f` para actualizar los archivos de vista de archivos estáticos.
1. Comprobar las actualizaciones en el control de código fuente.

>[!INFO]
>
>Vea [Estrategias de implementación para archivos de vista estática](../cli/static-view-file-strategy.md).

### Sistema de producción

En el sistema de producción (es decir, en la tienda activa) se extraen los recursos generados y las actualizaciones de código del control de código fuente y se establecen los valores de configuración específicos del sistema y confidenciales mediante la línea de comandos o las variables de entorno.

En su sistema de producción:

1. Inicie el modo de mantenimiento.
1. Extraer actualizaciones de código y configuración del control de código fuente.
1. Si utiliza Adobe Commerce, detenga los trabajadores en cola.
1. Utilice el comando `magento app:config:import` para importar los cambios de configuración en el sistema de producción.
1. Si instaló componentes que cambiaron el esquema de la base de datos, ejecute `magento setup:upgrade --keep-generated` para actualizar el esquema y los datos de la base de datos, conservando los archivos estáticos generados.
1. Para establecer la configuración específica del sistema, use el comando `magento config:set` o las variables de entorno.
1. Para establecer la configuración confidencial, use el comando `magento config:sensitive:set` o las variables de entorno.
1. Limpiar (también conocido como _vaciar_) la caché.
1. Finalizar modo de mantenimiento.

## Comandos de administración de configuración

Proporcionamos los siguientes comandos para ayudarle a administrar la configuración:

- [`magento app:config:dump`](../cli/export-configuration.md) para escribir las opciones de configuración de administración en `config.php` y `env.php` (excepto para las opciones confidenciales)
- [`magento config:set`](../cli/set-configuration-values.md) para establecer los valores de la configuración específica del sistema en el sistema de producción.

  Utilice la opción opcional `--lock` para bloquear la opción en el Administrador (es decir, hacer que la configuración no se pueda editar). Si una configuración ya está bloqueada, use la opción `--lock` para cambiarla.

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) para establecer los valores de la configuración confidencial en el sistema de producción.
- [`magento app:config:import`](../cli/import-configuration.md) para importar los cambios de configuración de `config.php` y `env.php` al sistema de producción.

## Ejemplos de administración de configuración

Esta sección muestra ejemplos de cómo administrar la configuración para que pueda ver cómo se realizan los cambios en `config.php` y `env.php`.

### Cambiar la configuración regional predeterminada

En esta sección se muestra el cambio realizado en `config.php` al cambiar la unidad de peso predeterminada mediante el Administrador (**Almacenes** > Configuración > **Configuración** > General > **General** > **Opciones de configuración regional**).

Después de realizar el cambio en el administrador, ejecute `bin/magento app:config:dump` para escribir el valor en `config.php`. El valor se escribe en la matriz `general` en `locale`, como se muestra en el siguiente fragmento de `config.php`:

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

En esta sección se explica cómo realizar los siguientes cambios en la configuración:

- Agregando un sitio web, tienda y vista de tienda (**Tiendas** > Configuración > **Todas las tiendas**)
- Cambiando el dominio de correo electrónico predeterminado (**Tiendas** > Configuración > **Configuración** > Clientes > **Configuración del cliente**)
- Estableciendo el nombre de usuario y la contraseña de la API de PayPal (**Tiendas** > Configuración > **Configuración** > Ventas > **Métodos de pago** > **PayPal** > **Ajustes de PayPal requeridos**)

Después de realizar el cambio en el Administrador, ejecute `bin/magento app:config:dump` en el sistema de desarrollo. Esta vez, no todos los cambios se escriben en `config.php`; de hecho, sólo el sitio web, la tienda y la vista de la tienda se escriben en ese archivo como se muestra en los siguientes fragmentos.

### config.php

`config.php` contiene:

- Cambios en el sitio web, tienda y vista de tienda.
- Configuración de motor de búsqueda no específica del sistema
- Configuración de PayPal no confidencial
- Comentarios que le informan de la configuración confidencial que se omitió en `config.php`

Matriz `websites`:

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

Matriz `groups`:

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

Matriz `stores`:

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

Matriz `payment`:

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

La configuración predeterminada específica del sistema del dominio de correo electrónico se escribe en `app/etc/env.php`.

La configuración de PayPal no se escribe en ninguno de los archivos porque el comando `bin/magento app:config:dump` no escribe la configuración confidencial. Debes establecer la configuración de PayPal en el sistema de producción mediante los siguientes comandos:

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
