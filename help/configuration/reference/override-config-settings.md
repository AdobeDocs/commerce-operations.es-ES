---
title: Anular configuración
description: Aprenda a utilizar variables de entorno para anular los ajustes de configuración.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 0%

---


# Anular configuración

En este tema se explica cómo derivar un nombre de variable de entorno a través de una ruta de configuración. Puede anular los ajustes de configuración de Adobe Commerce mediante variables de entorno. Por ejemplo, puede anular el valor de la URL activa de un procesador de pagos en su sistema de producción.

Puede anular el valor de _any_ configuración mediante variables de entorno; sin embargo, Adobe recomienda mantener una configuración coherente utilizando el archivo de configuración compartido, `config.php`y el archivo de configuración específico del sistema, `env.php`, tal como se explica en [Información general sobre la implementación](../deployment/overview.md).

>[!TIP]
>
>Consulte la [Configuración de entornos](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) en el _Guía de Commerce on Cloud Infrastructure_.

## Variables de entorno

Un nombre de variable de entorno consta de su ámbito seguido de su ruta de configuración en un formato determinado. En las secciones siguientes se explica cómo determinar un nombre de variable con más detalle.

Puede utilizar variables para cualquiera de las siguientes opciones:

- [Valores confidenciales](config-reference-sens.md) debe configurarse mediante variables de entorno o mediante la variable [`magento config:sensitive:set`](../cli/set-configuration-values.md) comando.
- Los valores específicos del sistema deben establecerse utilizando:

   - Variables de entorno
   - La variable [`magento config:set`](../cli/set-configuration-values.md) command
   - El administrador seguido del [`magento app:config:dump` command](../cli/export-configuration.md)

Las rutas de configuración se encuentran en:

- [Referencia de rutas de configuración confidenciales y específicas del sistema](config-reference-sens.md)
- [Referencia de rutas de configuración de pago](config-reference-payment.md)
- [Referencia de rutas de configuración de la extensión B2B de comercio](config-reference-b2b.md)
- [Otras referencias de rutas de configuración](config-reference-general.md)

### Nombres de variable

El formato general de los nombres de las variables de configuración del sistema es el siguiente:

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` puede ser:

- Alcance global (es decir, la configuración global para _all_ ámbitos)

   Las variables de ámbito globales tienen el siguiente formato:

   `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Un ámbito específico (es decir, la configuración solo afecta a una vista de tienda o sitio web especificados)

   Las variables de ámbito de vista de almacén, por ejemplo, tienen el siguiente formato:

   `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

   Para obtener más información sobre los ámbitos, consulte:

   - [Paso 1: Busque el valor del ámbito del sitio web o de la vista de tienda](#step-1-find-the-website-or-store-view-scope-value)
   - [Tema de la Guía del usuario de Commerce sobre el ámbito](https://docs.magento.com/user-guide/configuration/scope.html)
   - [Referencia rápida del ámbito](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` es la ruta de configuración con caracteres de guion bajo doble sustituidos por `/`. Para obtener más información, consulte [Paso 2: Establecer variables del sistema](#step-2-set-global-website-or-store-view-variables).

### Formato de variable

`<SCOPE>` está separado de `<SYSTEM__VARIABLE__NAME>` por dos caracteres de guion bajo.

`<SYSTEM__VARIABLE__NAME>` se deriva de una configuración de _ruta de configuración_, que es un `/` cadena delimitada que identifica de forma exclusiva una configuración determinada. Reemplazar cada `/` en la ruta de configuración con dos caracteres de guion bajo para crear la variable del sistema.

Si una ruta de configuración contiene un carácter de guion bajo, el carácter de guion bajo permanece en la variable .

Puede encontrar una lista completa de las rutas de configuración en:

- [Referencia de rutas de configuración confidenciales y específicas del sistema](config-reference-sens.md)
- [Referencia de rutas de configuración de pago](config-reference-payment.md)
- [Referencia de rutas de configuración de la extensión B2B de Commerce Enterprise](config-reference-b2b.md)
- [Otras referencias de rutas de configuración](config-reference-general.md)

## Paso 1: Busque el valor del ámbito del sitio web o de la vista de tienda

Esta sección explica cómo puede encontrar y establecer los valores de configuración del sistema por _scope_ (vista de tienda o sitio web). Para establecer variables de ámbito globales, consulte [Paso 2: Establecer variables globales, de sitio web o de vista de tienda](#step-2-set-global-website-or-store-view-variables).

Los valores de ámbito proceden de `store`, `store_group`y `store_website` tablas.

- La variable `store` la tabla especifica nombres y códigos de vistas de almacén
- La variable `store_website` la tabla especifica nombres y códigos de sitios web

También puede encontrar los valores de código mediante el Administrador.

Cómo leer la tabla:

- `Path in Admin` column

   Los valores anteriores a la coma son rutas en la navegación de Administración. Los valores posteriores a la coma son opciones del panel derecho.

- `Variable name` es el nombre de la variable de entorno correspondiente.

   Si lo desea, puede especificar valores del sistema para estos parámetros de configuración como variables de entorno.

   - El nombre completo de la variable siempre es ALL CAPS
   - Inicie un nombre de variable con `CONFIG__` (nota dos caracteres de guion bajo)
   - Puede encontrar la variable `<STORE_VIEW_CODE>` o `<WEBSITE_CODE>` de un nombre de variable en la base de datos Administración o Comercio, como se indica en las secciones siguientes.
   - Puede encontrar `<SYSTEM__VARIABLE__NAME>` tal como se describe en [Paso 2: Establecer variables globales, de sitio web o de vista de tienda](#step-2-set-global-website-or-store-view-variables).

### Busque un sitio web o el ámbito de vista de tienda en el Administrador

La siguiente tabla resume cómo encontrar el valor de vista de sitio web o tienda en el Administrador.

| Descripción | Ruta en administración | Nombre de variable |
|--------------|--------------|----------------------|
| Crear, editar y eliminar vistas de tiendas | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Crear, editar, eliminar sitios web | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

Por ejemplo, para encontrar un sitio web o almacenar el valor del ámbito de vista en el Administrador:

1. Inicie sesión en el administrador como usuario autorizado para ver sitios web.
1. Haga clic en **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Haga clic en el nombre de un sitio web o vista de tienda.

   El panel derecho se muestra similar al siguiente.

   ![Buscar el código de sitio web](../../assets/configuration/website-code.png)

1. El nombre del ámbito se muestra en la sección **[!UICONTROL Code]** campo .
1. Continuar con [Paso 2: Establecer variables globales, de sitio web o de vista de tienda](#step-2-set-global-website-or-store-view-variables).

### Buscar un sitio web o el ámbito de vista de tienda en la base de datos

Para obtener estos valores de la base de datos:

1. Inicie sesión en su sistema de desarrollo como [propietario del sistema de archivos](https://glossary.magento.com/magento-file-system-owner) si aún no lo ha hecho.
1. Introduzca el siguiente comando:

   ```bash
   mysql -u <database-username> -p
   ```

1. En el `mysql>` , introduzca los siguientes comandos en el orden que se muestra:

   ```shell
   use <database-name>;
   ```

1. Utilice las siguientes consultas SQL para encontrar los valores relevantes:

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   A continuación se muestra una muestra:

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

1. Utilice el valor de la variable `code` como nombre del ámbito, no como `name` valor.

   Por ejemplo, para configurar una variable de configuración para el sitio web de prueba, utilice el siguiente formato:

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   donde `<SYSTEM__VARIABLE__NAME>` procede de la siguiente sección.

## Paso 2: Establecer variables globales, de sitio web o de vista de tienda

En esta sección se explica cómo configurar variables del sistema.

- Para establecer valores para el ámbito global (es decir, todos los sitios web, tiendas y vistas de tiendas), comience el nombre de la variable con `CONFIG__DEFAULT__`.

- Para establecer un valor para una vista de tienda o sitio web en particular, inicie el nombre de la variable tal como se describe en [Paso 1: Buscar el valor del ámbito](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- La última parte del nombre de la variable es la ruta de configuración, que es única para cada configuración.

[Vea algunos ejemplos](#examples).

La tabla siguiente muestra algunas variables de muestra.

| Descripción | Ruta en administración (omitiendo **Almacenes** > **Configuración** > **Configuración**) | Nombre de variable |
|--------------|--------------|----------------------|
| nombre de host del servidor Elasticsearch | Catálogo > **Catálogo**, **Nombre de host del servidor Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| puerto del servidor Elasticsearch | Catálogo > **Catálogo**, **Puerto del servidor Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Origen del país de envío | Ventas > **Configuración de envío** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| Dirección URL de administración personalizada | Avanzado > **Administrador** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Ruta de administración personalizada | Avanzado > **Administrador** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Ejemplos

Esta sección muestra cómo encontrar valores de algunas variables de muestra.

### nombre de host del servidor Elasticsearch

Para encontrar el nombre de la variable para la minificación de HTML globales:

1. Determine el ámbito.

   Es el ámbito global, por lo que el nombre de la variable empieza por `CONFIG__DEFAULT__`

1. El resto del nombre de la variable es `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Resultado**: El nombre de la variable es `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Origen del país de envío

Para encontrar el nombre de la variable para el origen del país de envío:

1. Determine el ámbito.

   Busque el ámbito en la variable [base de datos](#find-a-website-or-store-view-scope-in-the-database) tal como se explica en el paso 1: Busque el valor del ámbito del sitio web o de la vista de tienda. (También puede encontrar el valor en el Administrador , tal como se muestra en la [en el paso 2: Establecer variables globales, de sitio web o de vista de tienda](#step-2-set-global-website-or-store-view-variables.

   Por ejemplo, el ámbito podría ser `CONFIG__WEBSITES__DEFAULT`.

1. El resto del nombre de la variable es `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Resultado**: El nombre de la variable es `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Cómo usar variables de entorno

Configure los valores de configuración como variables usando PHP [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) asocia matriz. Puede establecer los valores en cualquier script PHP que se ejecute cuando Commerce se ejecute.

>[!TIP]
>
>Configuración de valores de variables en `index.php` o `pub/index.php` no siempre funciona como se espera, ya que se pueden utilizar diferentes puntos de entrada de aplicación en función de la configuración del servidor web. Colocando `$_ENV` las `app/bootstrap.php` , independientemente de los diferentes puntos de entrada de la aplicación, la variable `$_ENV` las directivas siempre se ejecutan porque `app/bootstrap.php` carga de archivos como parte de la arquitectura de comercio.

Un ejemplo de configuración de dos `$_ENV` Los valores son los siguientes:

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Se muestra un ejemplo paso a paso en [Definir valores de configuración mediante variables de entorno](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- Para utilizar los valores que se establecen en la variable `$_ENV` matriz, debe configurar `variables_order = "EGPCS"`(Entorno, Obtener, Publicar, Cookie y Servidor) en su `php.ini` archivo. Para obtener más información, consulte [Documentación de PHP](https://www.php.net/manual/en/ini.core.php).
>
>- Para Adobe Commerce en la infraestructura de nube, si intenta anular los ajustes de configuración utilizando la variable [Interfaz web del proyecto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project), debe anteponer el nombre de la variable con `env:`. Por ejemplo:
>
>![Ejemplo de variable de entorno](../../assets/configuration/cloud-console-envvariable.png)
