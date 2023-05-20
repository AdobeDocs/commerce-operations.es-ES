---
title: Anular los ajustes de configuración
description: Aprenda a utilizar variables de entorno para anular los ajustes de configuración.
exl-id: 788fd3cd-f8c1-4514-8141-547fed36e9ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 0%

---

# Anular los ajustes de configuración

En este tema se explica cómo derivar un nombre de variable de entorno que conozca una ruta de configuración. Puede anular los ajustes de configuración de Adobe Commerce mediante variables de entorno. Por ejemplo, puede anular el valor de la URL activa de un procesador de pagos en su sistema de producción.

Puede anular el valor de _cualquiera_ configuración mediante variables de entorno; sin embargo, Adobe recomienda mantener una configuración coherente mediante el archivo de configuración compartida, `config.php`y el archivo de configuración específico del sistema, `env.php`, tal como se describe en [Información general sobre la implementación](../deployment/overview.md).

>[!TIP]
>
>Consulte la [Configuración de entornos](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) tema en la _Guía de Commerce en infraestructura en la nube_.

## Variables de entorno

El nombre de una variable de entorno consiste en su ámbito seguido de su ruta de configuración en un formato concreto. En las secciones siguientes se explica cómo determinar el nombre de una variable con más detalle.

Puede utilizar variables para cualquiera de las siguientes opciones:

- [Valores confidenciales](config-reference-sens.md) debe configurarse mediante variables de entorno o la variable [`magento config:sensitive:set`](../cli/set-configuration-values.md) comando.
- Los valores específicos del sistema deben configurarse con:

   - Variables de entorno
   - El [`magento config:set`](../cli/set-configuration-values.md) mando
   - El administrador seguido de [`magento app:config:dump` mando](../cli/export-configuration.md)

Las rutas de configuración se encuentran en:

- [Referencia de rutas de configuración confidenciales y específicas del sistema](config-reference-sens.md)
- [Referencia de rutas de configuración de pago](config-reference-payment.md)
- [Referencia de rutas de configuración de la extensión Commerce B2B](config-reference-b2b.md)
- [Referencia de otras rutas de configuración](config-reference-general.md)

### Nombres de variables

El formato general de los nombres de las variables de configuración del sistema es el siguiente:

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` puede ser:

- Ámbito global (es decir, la configuración global para _todo_ ámbitos)

   Las variables de ámbito global tienen el formato siguiente:

   `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Un ámbito específico (es decir, la configuración solo afecta a una vista de tienda o sitio web especificados)

   Las variables de ámbito de vista de tienda, por ejemplo, tienen el formato siguiente:

   `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

   Para obtener más información sobre los ámbitos, consulte:

   - [Paso 1: Encuentre el valor de ámbito de vista del sitio web o tienda](#step-1-find-the-website-or-store-view-scope-value)
   - [Tema de la Guía del usuario de Commerce sobre el ámbito](https://docs.magento.com/user-guide/configuration/scope.html)
   - [Referencia rápida del ámbito](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` es la ruta de configuración con caracteres de subrayado doble sustituidos para `/`. Para obtener más información, consulte [Paso 2: Establecer variables del sistema](#step-2-set-global-website-or-store-view-variables).

### Formato variable

`<SCOPE>` está separado de `<SYSTEM__VARIABLE__NAME>` por dos caracteres de subrayado.

`<SYSTEM__VARIABLE__NAME>` se deriva de la configuración de _ruta de configuración_, que es un `/` cadena delimitada que identifica de forma exclusiva una configuración determinada. Reemplazar cada `/` en la ruta de configuración con dos caracteres de guion bajo para crear la variable del sistema.

Si una ruta de configuración contiene un carácter de guion bajo, este permanece en la variable.

Puede encontrar una lista completa de las rutas de configuración en:

- [Referencia de rutas de configuración confidenciales y específicas del sistema](config-reference-sens.md)
- [Referencia de rutas de configuración de pago](config-reference-payment.md)
- [Referencia de rutas de configuración de la extensión Commerce Enterprise B2B](config-reference-b2b.md)
- [Referencia de otras rutas de configuración](config-reference-general.md)

## Paso 1: Encuentre el valor de ámbito de vista del sitio web o tienda

En esta sección se explica cómo buscar y establecer valores de configuración del sistema para _ámbito_ (vista de tienda o sitio web). Para establecer variables de ámbito global, consulte [Paso 2: Establecer variables de vista globales, de sitio web o de tienda](#step-2-set-global-website-or-store-view-variables).

Los valores de ámbito proceden del `store`, `store_group`, y `store_website` tablas.

- El `store` especifica los nombres y códigos de la vista de tienda
- El `store_website` especifica nombres y códigos de sitios web

También puede encontrar los valores del código usando el Administrador.

Cómo leer la tabla:

- `Path in Admin` columna

   Los valores anteriores a la coma son rutas en la navegación del administrador. Los valores después de la coma son opciones del panel derecho.

- `Variable name` es el nombre de la variable de entorno correspondiente.

   Si lo desea, tiene la opción de especificar los valores del sistema para estos parámetros de configuración como variables de entorno.

   - El nombre completo de la variable siempre está en MAYÚSCULAS
   - Iniciar un nombre de variable con `CONFIG__` (nota dos caracteres de subrayado)
   - Puede encontrar el `<STORE_VIEW_CODE>` o `<WEBSITE_CODE>` de un nombre de variable en la base de datos de administración o de comercio, como se indica en las secciones siguientes.
   - Puede encontrar `<SYSTEM__VARIABLE__NAME>` tal como se discute en [Paso 2: Establecer variables de vista globales, de sitio web o de tienda](#step-2-set-global-website-or-store-view-variables).

### Busque un sitio web o un ámbito de vista de tienda en el Administrador de

La siguiente tabla resume cómo buscar un sitio web o almacenar valores de visualización en el administrador.

| Descripción | Ruta en el administrador | Nombre de variable |
|--------------|--------------|----------------------|
| Crear, editar o eliminar vistas de tiendas | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Creación, edición y eliminación de sitios web | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

Por ejemplo, para buscar un sitio web o almacenar el valor de ámbito de vista en el Administrador:

1. Inicie sesión en Admin como usuario autorizado para ver sitios web.
1. Clic **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Haga clic en el nombre de un sitio web o una vista de tienda.

   El panel derecho se muestra de forma similar al siguiente.

   ![Buscar un código de sitio web](../../assets/configuration/website-code.png)

1. El nombre del ámbito se muestra en la **[!UICONTROL Code]** field.
1. Continuar con [Paso 2: Establecer variables de vista globales, de sitio web o de tienda](#step-2-set-global-website-or-store-view-variables).

### Buscar un sitio web o un ámbito de vista de tienda en la base de datos

Para obtener estos valores de la base de datos:

1. Inicie sesión en el sistema de desarrollo como propietario del sistema de archivos si aún no lo ha hecho.
1. Introduzca el siguiente comando:

   ```bash
   mysql -u <database-username> -p
   ```

1. En el `mysql>` , introduzca los siguientes comandos en el orden mostrado:

   ```shell
   use <database-name>;
   ```

1. Utilice las siguientes consultas SQL para buscar los valores relevantes:

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   A continuación se muestra un ejemplo:

   ```shell
   mysql> SELECT * FROM STORE_WEBSITE;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

1. Utilice el valor del `code` como el nombre del ámbito, no la columna `name` valor.

   Por ejemplo, para establecer una variable de configuración para el sitio web de prueba, utilice el siguiente formato:

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   donde `<SYSTEM__VARIABLE__NAME>` proviene de la siguiente sección.

## Paso 2: Establecer variables de vista globales, de sitio web o de tienda

En esta sección se explica cómo establecer variables del sistema.

- Para establecer valores para el ámbito global (es decir, todos los sitios web, tiendas y vistas de tiendas), inicie el nombre de la variable con `CONFIG__DEFAULT__`.

- Para establecer un valor para una vista de tienda o sitio web en particular, inicie el nombre de la variable como se describe en [Paso 1: Buscar el valor de ámbito](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- La última parte del nombre de la variable es la ruta de configuración, que es única para cada ajuste de configuración.

[Consulte algunos ejemplos](#examples).

La siguiente tabla muestra algunas variables de ejemplo.

| Descripción | Ruta en administración (omitir) **Tiendas** > **Configuración** > **Configuración**) | Nombre de variable |
|--------------|--------------|----------------------|
| nombre de host del servidor Elasticsearch | Catálogo > **Catálogo**, **Nombre de host del servidor Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Puerto del servidor del Elasticsearch | Catálogo > **Catálogo**, **Puerto del servidor Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Origen del país de envío | Ventas > **Configuración de envío** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| URL de administración personalizada | Avanzadas > **Administrador** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Ruta de administración personalizada | Avanzadas > **Administrador** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Ejemplos

Esta sección muestra cómo buscar valores de algunas variables de ejemplo.

### nombre de host del servidor Elasticsearch

Para buscar el nombre de la variable para la minificación de HTML global:

1. Determine el ámbito.

   Es el ámbito global, por lo que el nombre de la variable empieza por `CONFIG__DEFAULT__`

1. El resto del nombre de la variable es `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Resultado**: el nombre de la variable es `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Origen del país de envío

Para buscar el nombre de variable del origen del país de envío:

1. Determine el ámbito.

   Busque el ámbito en la [database](#find-a-website-or-store-view-scope-in-the-database) como se explica en el paso 1: Encuentre el valor de ámbito del sitio web o de la vista de tienda. (También puede encontrar el valor en el Administrador, como se muestra en la [en el paso 2: establecer variables de vista globales, de sitio web o de tienda](#step-2-set-global-website-or-store-view-variables.

   Por ejemplo, el ámbito podría ser `CONFIG__WEBSITES__DEFAULT`.

1. El resto del nombre de la variable es `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Resultado**: el nombre de la variable es `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Cómo utilizar variables de entorno

Establecer valores de configuración como variables usando PHP [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) matriz asociada. Puede establecer los valores en cualquier script PHP que se ejecute cuando se ejecute Commerce.

>[!TIP]
>
>Configuración de valores de variables en `index.php` o `pub/index.php` no siempre funciona como se espera, ya que se pueden utilizar diferentes puntos de entrada de aplicación según la configuración del servidor web. Al colocar `$_ENV` directivas en la `app/bootstrap.php` , independientemente de los diferentes puntos de entrada de la aplicación, `$_ENV` Las directivas de siempre se ejecutan ya que `app/bootstrap.php` se carga como parte de la arquitectura de Commerce.

Ejemplo de configuración de dos `$_ENV` valores siguientes:

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Se muestra un ejemplo paso a paso en [Establecer valores de configuración mediante variables de entorno](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- Para utilizar los valores que ha configurado en la variable `$_ENV` matriz, debe establecer `variables_order = "EGPCS"`(Entorno, Obtener, Publicar, Cookie y Servidor) en su `php.ini` archivo. Para obtener más información, consulte [Documentación de PHP](https://www.php.net/manual/en/ini.core.php).
>
>- Para Adobe Commerce en la infraestructura en la nube, si intenta anular los ajustes de configuración utilizando [Interfaz web de Project](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project), debe anteponer el nombre de la variable con `env:`. Por ejemplo:
>
>![Ejemplo de variable de entorno](../../assets/configuration/cloud-console-envvariable.png)
