---
title: Establecer valores de configuración
description: Obtenga información sobre cómo establecer valores de configuración y cambiar valores que están bloqueados en el Administrador.
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 78a7e99ecaba6a6f7982123f5bd67efc740ec2ef
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---

# Establecer valores de configuración

{{file-system-owner}}

En este tema se describen los comandos de configuración avanzada que se pueden utilizar para:

- Establezca cualquier opción de configuración desde la línea de comandos
- Si lo desea, bloquee cualquier opción de configuración para que su valor no se pueda cambiar en el Administrador
- Cambie una opción de configuración que esté bloqueada en el Administrador

Puede utilizar estos comandos para establecer la configuración de Commerce manualmente o mediante scripts. Las opciones de configuración se establecen mediante una _ruta de configuración_, que es un `/`Cadena delimitada por caracteres que identifica de forma exclusiva esa opción de configuración. Puede encontrar rutas de configuración en las siguientes referencias:

- [Referencia de rutas de configuración confidenciales y específicas del sistema](../reference/config-reference-sens.md)
- [Referencia de rutas de configuración de pago](../reference/config-reference-payment.md)
- [Referencia de rutas de configuración generales](../reference/config-reference-general.md)
- [Referencia de rutas de configuración de la extensión Commerce Enterprise B2B](../reference/config-reference-b2b.md)

Puede definir valores en los momentos siguientes:

- Antes de instalar Commerce, puede establecer los valores de configuración solo para el ámbito predeterminado, ya que es el único ámbito válido.

- Después de instalar Commerce, puede establecer los valores de configuración de cualquier sitio web o ámbito de vista de la tienda.

Utilice los siguientes comandos:

- `bin/magento config:set` establece cualquier valor de configuración no confidencial por su ruta de configuración
- `bin/magento config:sensitive:set` establece cualquier valor de configuración confidencial por su ruta de configuración
- `bin/magento config:show` muestra los valores de configuración guardados; los valores de configuración cifrados se muestran como asteriscos

## Requisitos previos

Para establecer un valor de configuración, debe conocer al menos una de las siguientes opciones:

- La ruta de configuración
- Para establecer un valor de configuración para un ámbito en particular, debe conocer el código de ámbito.

  Para establecer un valor de configuración para el ámbito predeterminado, no es necesario que haga nada.

### Buscar la ruta de configuración

Consulte las siguientes referencias:

- [Referencia de rutas de configuración confidenciales y específicas del sistema](../reference/config-reference-sens.md)
- [Referencia de rutas de configuración de pago](../reference/config-reference-payment.md)
- [Referencia de otras rutas de configuración](../reference/config-reference-general.md)
- [Referencia de rutas de configuración de la extensión Commerce Enterprise B2B](../reference/config-reference-b2b.md)

### Buscar el código de ámbito

Puede encontrar el código de ámbito en la base de datos de Commerce o en el Administrador de Commerce.

**Para buscar el código de ámbito en el Administrador**:

1. Inicie sesión en el administrador como un usuario que puede ver sitios web y almacenar vistas.
1. Clic **[!UICONTROL Stores]** > Configuración > **[!UICONTROL All Stores]**.
1. En el panel derecho, haga clic en el nombre del sitio web o de la vista de tienda para ver su código.

   La siguiente figura muestra un ejemplo de código de sitio web.

   ![Obtenga un sitio web o código de vista de tienda del administrador](../../assets/configuration/website-code.png)

1. Continuar con [Establecer valores](#set-values).

**Para buscar el código de ámbito en la base de datos**:

Los códigos de ámbito de los sitios web y las vistas de tiendas se almacenan en la base de datos de Commerce en `store_website` y `store` , respectivamente.

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

   A continuación se muestra un ejemplo:

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

   Utilice el valor en `code` columna.

1. Continúe con la siguiente sección.

## Establecer valores

**Para establecer valores de configuración específicos del sistema**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**Para establecer valores de configuración confidenciales**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

En la tabla siguiente se describe la `set` parámetros de comando:

| Parámetro | Descripción |
| --- | --- |
| `--scope` | El ámbito de la configuración. Los valores posibles son `default`, `website`, o `store`. El valor predeterminado es `default`. |
| `--scope-code` | El código de ámbito de la configuración (código de sitio web o código de vista de tienda) |
| `-e or --lock-env` | Bloquea el valor para que no se pueda editar en el Administrador o cambia una configuración que ya está bloqueada en el Administrador. El comando escribe el valor en `<Commerce base dir>/app/etc/env.php` archivo. |
| `-c or --lock-config` | Bloquea el valor para que no se pueda editar en el Administrador o cambia una configuración que ya está bloqueada en el Administrador. El comando escribe el valor en `<Commerce base dir>/app/etc/config.php` archivo. El `--lock-config` sobrescribe la opción `--lock-env` si especifica ambas opciones. |
| `path` | _Requerido_. La ruta de configuración |
| `value` | _Requerido_. El valor de la configuración |

>[!INFO]
>
>A partir de Commerce 2.2.4, la `--lock-env` y `--lock-config` Las opciones de reemplazan a `--lock` opción.
>
>Si usa el `--lock-env` o `--lock-config` para establecer o cambiar un valor, debe utilizar la opción [`bin/magento app:config:import` mando](../cli/import-configuration.md) para importar la configuración antes de acceder al administrador o tienda.

Si escribe una ruta de configuración incorrecta, este comando devuelve un error

```text
The "wrong/config/path" does not exist
```

Consulte una de las siguientes secciones para obtener más información:

- [Establezca los valores de configuración que se pueden editar en el Administrador](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Establezca valores de configuración que no se puedan editar en el Administrador](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Establezca los valores de configuración que se pueden editar en el Administrador

Uso `bin/magento config:set` _sin_ `--lock-env` o `--lock-config` para escribir el valor en la base de datos. Los valores que configure de esta manera se pueden editar en el Administrador.

A continuación se muestran algunos ejemplos de configuración de una URL base de tienda:

Establezca la dirección URL base para el ámbito predeterminado:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Establezca la dirección URL base para `base` sitio web:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Establezca la dirección URL base para `test` vista de tienda:

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Establezca valores de configuración que no se puedan editar en el Administrador

Si usa el `--lock-env`  como se indica a continuación, el comando guarda el valor de configuración en `<Commerce base dir>/app/etc/env.php` y deshabilita el campo para editar este valor en Admin.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Puede usar el complemento `--lock-env` para establecer los valores de configuración si Commerce no está instalado. Sin embargo, solo puede establecer valores para el ámbito predeterminado.

>[!INFO]
>
>El `env.php` es específico del sistema. No debe transferirlo a otro sistema. Puede utilizarlo para sobrescribir los valores de configuración de la base de datos. Por ejemplo, puede tomar un volcado de la base de datos de otro sistema y sobrescribir el `base_url` y otros valores para que no tenga que modificar la base de datos.

Si usa el `--lock-config` como se indica a continuación, el valor de configuración se guarda en `<Commerce base dir>/app/etc/config.php`. El campo para editar este valor en Admin está desactivado.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Puede utilizar `--lock-config` para establecer los valores de configuración si Commerce no está instalado. Sin embargo, solo puede establecer valores para el ámbito predeterminado.

>[!INFO]
>
>Puede transferir `config.php` a otro sistema para utilizar los mismos valores de configuración allí. Por ejemplo, si tiene un sistema de prueba, utilizando el mismo `config.php` significa que no tiene que volver a establecer los mismos valores de configuración.

## Mostrar el valor de las opciones de configuración

Opciones de comando:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

donde

- `--scope` es el ámbito de configuración (predeterminado, sitio web, tienda). El valor predeterminado es `default`
- `--scope-code` es el código de ámbito de la configuración (código de sitio web o código de vista de tienda)
- `path` es la ruta de configuración con el formato first_part/second_part/third_part/etc (_obligatorio_)

>[!INFO]
>
>El `bin/magento config:show` El comando muestra los valores de cualquier [valores cifrados](../reference/config-reference-sens.md) como una serie de asteriscos: `******`.

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

**Para mostrar todas las configuraciones guardadas de `base` sitio web**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Resultado:

```terminal
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**Para mostrar la dirección URL base del ámbito predeterminado**:

```bash
bin/magento config:show web/unsecure/base_url
```

Resultado:

```terminal
web/unsecure/base_url - http://example.com/
```

**Para mostrar la dirección URL base de `base` sitio web**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Resultado:

```terminal
web/unsecure/base_url - http://example-for-website.com/
```

**Para mostrar la dirección URL base de `default` almacenar**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Resultado:

```terminal
web/unsecure/base_url - http://example-for-store.com/
```
