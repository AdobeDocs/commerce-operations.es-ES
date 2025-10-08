---
title: Establecer valores de configuración
description: Obtenga información sobre cómo establecer valores de configuración y cambiar valores de administración bloqueados en Adobe Commerce. Descubra los comandos y las técnicas de configuración avanzada.
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 0%

---

# Establecer valores de configuración

{{file-system-owner}}

En este tema se describen los comandos de configuración avanzada que se pueden utilizar para:

- Establezca cualquier opción de configuración desde la línea de comandos
- Si lo desea, bloquee cualquier opción de configuración para que su valor no se pueda cambiar en el Administrador
- Cambie una opción de configuración que esté bloqueada en el Administrador

Puede utilizar estos comandos para establecer la configuración de Commerce manualmente o mediante scripts. Las opciones de configuración se establecen mediante una _ruta de configuración_, que es una cadena delimitada por `/` que identifica de forma exclusiva esa opción de configuración. Puede encontrar rutas de configuración en las siguientes referencias:

- [Referencia de rutas de configuración confidenciales y específicas del sistema](../reference/config-reference-sens.md)
- [Referencia de rutas de configuración de pago](../reference/config-reference-payment.md)
- [Referencia de rutas de configuración generales](../reference/config-reference-general.md)
- [Referencia de rutas de configuración de la extensión Commerce Enterprise B2B](../reference/config-reference-b2b.md)

Puede definir valores en los momentos siguientes:

- Antes de instalar Commerce, puede establecer valores de configuración solo para el ámbito predeterminado, ya que es el único ámbito válido.

- Después de instalar Commerce, puede establecer los valores de configuración de cualquier sitio web o ámbito de vista de la tienda.

Utilice los siguientes comandos:

- `bin/magento config:set` establece cualquier valor de configuración no confidencial por su ruta de configuración
- `bin/magento config:sensitive:set` establece cualquier valor de configuración confidencial por su ruta de configuración
- `bin/magento config:show` muestra valores de configuración guardados; los valores de configuración cifrada se muestran como asteriscos

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

**Para encontrar el código de ámbito en Admin**:

1. Inicie sesión en el administrador como un usuario que puede ver sitios web y almacenar vistas.
1. Haga clic en **[!UICONTROL Stores]** > Configuración > **[!UICONTROL All Stores]**.
1. En el panel derecho, haga clic en el nombre del sitio web o de la vista de tienda para ver su código.

   La siguiente figura muestra un ejemplo de código de sitio web.

   ![Obtener un sitio web o código de vista de tienda del administrador](../../assets/configuration/website-code.png)

1. Continuar con [Establecer valores](#set-values).

**Para encontrar el código de ámbito en la base de datos**:

Los códigos de ámbito de los sitios web y las vistas de tienda se almacenan en la base de datos de Commerce en las tablas `store_website` y `store`, respectivamente.

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

   ```
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   Use el valor de la columna `code`.

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

En la tabla siguiente se describen los parámetros de comando `set`:

| Parámetro | Descripción |
| --- | --- |
| `--scope` | El ámbito de la configuración. Los valores posibles son `default`, `website` o `store`. El valor predeterminado es `default`. |
| `--scope-code` | El código de ámbito de la configuración (código de sitio web o código de vista de tienda) |
| `-e or --lock-env` | Bloquea el valor para que no se pueda editar en el Administrador o cambia una configuración que ya está bloqueada en el Administrador. El comando escribe el valor en el archivo `<Commerce base dir>/app/etc/env.php`. |
| `-c or --lock-config` | Bloquea el valor para que no se pueda editar en el Administrador o cambia una configuración que ya está bloqueada en el Administrador. El comando escribe el valor en el archivo `<Commerce base dir>/app/etc/config.php`. La opción `--lock-config` sobrescribe `--lock-env` si especifica ambas opciones. |
| `path` | _Requerido_. La ruta de configuración |
| `value` | _Requerido_. El valor de la configuración |

>[!INFO]
>
>A partir de Commerce 2.2.4, las opciones `--lock-env` y `--lock-config` reemplazan la opción `--lock`.
>
>Si usa la opción `--lock-env` o `--lock-config` para establecer o cambiar un valor, debe usar el comando [`bin/magento app:config:import` &#x200B;](../cli/import-configuration.md) para importar la configuración antes de tener acceso al administrador o a la tienda.

Si escribe una ruta de configuración incorrecta, este comando devuelve un error

```text
The "wrong/config/path" does not exist
```

Consulte una de las siguientes secciones para obtener más información:

- [Establezca los valores de configuración que se pueden editar en el Administrador](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Establezca valores de configuración que no se puedan editar en el Administrador](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Establezca los valores de configuración que se pueden editar en el Administrador

Use `bin/magento config:set` _sin_ `--lock-env` o `--lock-config` para escribir el valor en la base de datos. Los valores que configure de esta manera se pueden editar en el Administrador.

A continuación se muestran algunos ejemplos de configuración de una URL base de tienda:

Establezca la dirección URL base para el ámbito predeterminado:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Establecer la dirección URL base del sitio web `base`:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Establecer la dirección URL base para la vista del almacén `test`:

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Establezca valores de configuración que no se puedan editar en el Administrador

Si usa la opción `--lock-env` de la siguiente manera, el comando guarda el valor de configuración en `<Commerce base dir>/app/etc/env.php` y deshabilita el campo para editar este valor en el Administrador.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

Puede usar la opción `--lock-env` para establecer los valores de configuración si Commerce no está instalado. Sin embargo, solo puede establecer valores para el ámbito predeterminado.

>[!INFO]
>
>El archivo `env.php` es específico del sistema. No debe transferirlo a otro sistema. Puede utilizarlo para sobrescribir los valores de configuración de la base de datos. Por ejemplo, puede tomar un volcado de la base de datos de otro sistema y sobrescribir `base_url` y otros valores para no tener que modificar la base de datos.

Si usa la opción `--lock-config` de la siguiente manera, el valor de configuración se guarda en `<Commerce base dir>/app/etc/config.php`. El campo para editar este valor en Admin está desactivado.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

Puede usar `--lock-config` para establecer los valores de configuración si Commerce no está instalado. Sin embargo, solo puede establecer valores para el ámbito predeterminado.

>[!INFO]
>
>Puede transferir `config.php` a otro sistema para utilizar allí los mismos valores de configuración. Por ejemplo, si tiene un sistema de prueba, el uso del mismo `config.php` significa que no tiene que volver a establecer los mismos valores de configuración.

## Mostrar el valor de las opciones de configuración

Opciones de comando:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

donde

- `--scope` es el ámbito de configuración (predeterminado, sitio web, tienda). El valor predeterminado es `default`
- `--scope-code` es el código de ámbito de configuración (código de sitio web o código de vista de tienda)
- `path` es la ruta de configuración con el formato first_part/second_part/third_part/etc (_obligatorio_)

>[!INFO]
>
>El comando `bin/magento config:show` muestra los valores de cualquier [valor cifrado](../reference/config-reference-sens.md) como una serie de asteriscos: `**&#x200B;**&#x200B;**`.

### Ejemplos

**Para mostrar todas las configuraciones guardadas**:

```bash
bin/magento config:show
```

Resultado:

```
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**Para mostrar todas las configuraciones guardadas para el sitio web `base`**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Resultado:

```
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**Para mostrar la dirección URL base del ámbito predeterminado**:

```bash
bin/magento config:show web/unsecure/base_url
```

Resultado:

```
web/unsecure/base_url - http://example.com/
```

**Para mostrar la dirección URL base del sitio web `base`**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Resultado:

```
web/unsecure/base_url - http://example-for-website.com/
```

**Para mostrar la dirección URL base del almacén `default`**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Resultado:

```
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>El código de ámbito solo puede incluir letras (a-z o A-Z), números (0-9) y guiones bajos (_). Además, el primer carácter debe ser una letra. Si se utilizan mayúsculas o minúsculas al crear un sitio web o una vista de tienda, internamente la coincidencia no distingue entre mayúsculas y minúsculas para dar cabida a la anulación de los ajustes de configuración mediante variables de entorno. Consulte [Usar variables de entorno para anular las opciones de configuración](../reference/override-config-settings.md#environment-variables).

