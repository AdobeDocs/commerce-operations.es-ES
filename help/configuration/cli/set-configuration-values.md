---
title: Definir valores de configuración
description: Obtenga información sobre cómo establecer valores de configuración y cambiar valores que están bloqueados en Administración.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---


# Definir valores de configuración

{{file-system-owner}}

En este tema se tratan los comandos de configuración avanzada que puede utilizar para:

- Establecer cualquier opción de configuración desde la línea de comandos
- Si lo desea, bloquee cualquier opción de configuración para que su valor no se pueda cambiar en el Administrador
- Cambiar una opción de configuración que esté bloqueada en el Administrador

Puede utilizar estos comandos para configurar la configuración de Commerce manualmente o utilizando secuencias de comandos. Las opciones de configuración se definen mediante un _ruta de configuración_, que es un `/`cadena delimitada por caracteres -que identifica de forma exclusiva esa opción de configuración. Puede encontrar rutas de configuración en las siguientes referencias:

- [Referencia de rutas de configuración confidenciales y específicas del sistema](../reference/config-reference-sens.md)
- [Referencia de rutas de configuración de pago](../reference/config-reference-payment.md)
- [Referencia de rutas de configuración generales](../reference/config-reference-general.md)
- [Referencia de rutas de configuración de la extensión B2B de Commerce Enterprise](../reference/config-reference-b2b.md)

Puede establecer valores en los siguientes momentos:

- Antes de instalar Commerce, puede establecer valores de configuración solo para el ámbito predeterminado, ya que es el único ámbito válido.

- Después de instalar Commerce, puede establecer valores de configuración para cualquier sitio web o ámbito de vista de tienda.

Utilice los siguientes comandos:

- `bin/magento config:set` establece cualquier valor de configuración no sensible según su ruta de configuración
- `bin/magento config:sensitive:set` establece cualquier valor de configuración confidencial según su ruta de configuración
- `bin/magento config:show` muestra los valores de configuración guardados; los valores de configuración cifrada se muestran como asteriscos

## Requisitos previos

Para establecer un valor de configuración, debe conocer al menos una de las siguientes opciones:

- La ruta de configuración
- Para establecer un valor de configuración para un ámbito en particular, debe conocer el código de ámbito.

   Para establecer un valor de configuración para el ámbito predeterminado, no es necesario que haga nada.

### Buscar la ruta de configuración

Consulte las siguientes referencias:

- [Referencia de rutas de configuración confidenciales y específicas del sistema](../reference/config-reference-sens.md)
- [Referencia de rutas de configuración de pago](../reference/config-reference-payment.md)
- [Otras referencias de rutas de configuración](../reference/config-reference-general.md)
- [Referencia de rutas de configuración de la extensión B2B de Commerce Enterprise](../reference/config-reference-b2b.md)

### Buscar el código de ámbito

Puede encontrar el código de ámbito en la base de datos de comercio o en el administrador de comercio.

**Para buscar el código de ámbito en el administrador**:

1. Inicie sesión en el administrador como usuario que puede ver sitios web y almacenar vistas.
1. Haga clic en **[!UICONTROL Stores]** > Configuración > **[!UICONTROL All Stores]**.
1. En el panel derecho, haga clic en el nombre del sitio web o de la vista de tienda para ver su código.

   La siguiente figura muestra un ejemplo de código de sitio web.

   ![Obtener un sitio web o almacenar código de vista desde el administrador](../../assets/configuration/website-code.png)

1. Continuar con [Definir valores](#set-values).

**Búsqueda del código de ámbito en la base de datos**:

Los códigos de ámbito de los sitios web y las vistas de tienda se almacenan en la base de datos de comercio de la variable `store_website` y `store` tablas, respectivamente.

1. Conéctese a la base de datos de Commerce.

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. Introduzca los siguientes comandos:

   ```shell
   use <Commerce database name>;
   ```

   ```shell
   SELECT * FROM store;
   ```

   ```shell
   SELECT * FROM store_website;
   ```

   A continuación se muestra un resultado de muestra:

   ```terminal
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   Utilice el valor en la variable `code` para abrir el Navegador.

1. Continúe con la siguiente sección.

## Definir valores

**Para establecer valores de configuración específicos del sistema**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**Para establecer valores de configuración confidenciales**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

La tabla siguiente describe el `set` parámetros de comando:

| Parámetro | Descripción |
| --- | --- |
| `--scope` | El ámbito de la configuración. Los valores posibles son `default`, `website`o `store`. El valor predeterminado es `default`. |
| `--scope-code` | El código de ámbito de configuración (código de sitio web o código de vista de tienda) |
| `-e or --lock-env` | Bloquea el valor para que no se pueda editar en el Administrador o cambia un valor que ya está bloqueado en el Administrador. El comando escribe el valor en la variable `<Commerce base dir>/app/etc/env.php` archivo. |
| `-c or --lock-config` | Bloquea el valor para que no se pueda editar en el Administrador o cambia un valor que ya está bloqueado en el Administrador. El comando escribe el valor en la variable `<Commerce base dir>/app/etc/config.php` archivo. La variable `--lock-config` sobrescrituras de opciones `--lock-env` si especifica ambas opciones. |
| `path` | _Requerido_. La ruta de configuración |
| `value` | _Requerido_. El valor de la configuración |

>[!INFO]
>
>A partir de Commerce 2.2.4, la variable `--lock-env` y `--lock-config` reemplace el `--lock` .
>
>Si usa la variable `--lock-env` o `--lock-config` para establecer o cambiar un valor, debe utilizar la opción [`bin/magento app:config:import` command](../cli/import-configuration.md) para importar la configuración antes de acceder al administrador o tienda.

Si introduce una ruta de configuración incorrecta, este comando devuelve un error

```text
The "wrong/config/path" does not exist
```

Consulte una de las secciones siguientes para obtener más información:

- [Establezca los valores de configuración que se pueden editar en el Administrador](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Establezca los valores de configuración que no se pueden editar en el Administrador](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Establezca los valores de configuración que se pueden editar en el Administrador

Uso `bin/magento config:set` _without_ `--lock-env` o `--lock-config` para escribir el valor en la base de datos. Los valores que defina de esta forma se pueden editar en el Administrador.

A continuación se muestran algunos ejemplos de configuración de una URL de base de tienda:

Establezca la URL base para el ámbito predeterminado:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Defina la dirección URL base para la variable `base` sitio web:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Defina la dirección URL base para la variable `test` vista de tienda:

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Establezca los valores de configuración que no se pueden editar en el Administrador

Si usa la variable `--lock-env`  como se indica a continuación, el comando guarda el valor de configuración en `<Commerce base dir>/app/etc/env.php` y deshabilita el campo para editar este valor en Admin.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Puede usar la variable `--lock-env` para establecer los valores de configuración si Commerce no está instalado. Sin embargo, solo puede establecer valores para el ámbito predeterminado.

>[!INFO]
>
>La variable `env.php` es específico del sistema. No debe transferirlo a otro sistema. Puede utilizarla para sobrescribir los valores de configuración de la base de datos. Por ejemplo, puede tomar un volcado de base de datos de otro sistema y sobrescribir el `base_url` y otros valores para no tener que modificar la base de datos.

Si usa la variable `--lock-config` como se indica a continuación, el valor de configuración se guarda en `<Commerce base dir>/app/etc/config.php`. El campo para editar este valor en Admin está desactivado.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Puede usar `--lock-config` para establecer los valores de configuración si Commerce no está instalado. Sin embargo, solo puede establecer valores para el ámbito predeterminado.

>[!INFO]
>
>Puede transferir `config.php` a otro sistema para usar los mismos valores de configuración allí. Por ejemplo, si tiene un sistema de prueba, use el mismo `config.php` significa que no tiene que volver a establecer los mismos valores de configuración.

## Mostrar el valor de los ajustes de configuración

Opciones de comando:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

donde

- `--scope` es el ámbito de configuración (predeterminado, sitio web, tienda). El valor predeterminado es `default`
- `--scope-code` es el código de ámbito de configuración (código de sitio web o código de vista de tienda)
- `path` es la ruta de configuración en formato first_part/Second_part/third_part/etc (_obligatorio_)

>[!INFO]
>
>La variable `bin/magento config:show` muestra los valores de cualquier [valores cifrados](../reference/config-reference-sens.md) como una serie de asteriscos: `******`.

### Ejemplos

**Para mostrar todas las configuraciones guardadas**:

```bash
bin/magento config:show
```

Resultado:

```terminal
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**Para mostrar todas las configuraciones guardadas para la variable `base` sitio web**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Resultado:

```terminal
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**Para mostrar la URL base para el ámbito predeterminado**:

```bash
bin/magento config:show web/unsecure/base_url
```

Resultado:

```terminal
web/unsecure/base_url - http://example.com/
```

**Para mostrar la dirección URL base de la variable `base` sitio web**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Resultado:

```terminal
web/unsecure/base_url - http://example-for-website.com/
```

**Para mostrar la dirección URL base de la variable `default` almacenar**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Resultado:

```terminal
web/unsecure/base_url - http://example-for-store.com/
```
