---
title: Administrar la caché
description: Administre los tipos de caché y vea el estado de la caché.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 0%

---


# Administrar la caché

{{file-system-owner}}

## Tipos de caché

Commerce 2 tiene los siguientes tipos de caché:

| Nombre &quot;práctico&quot; de tipo caché | Nombre de código de tipo de caché | Descripción |
|--- |--- |--- |
| Configuración | config | Commerce recopila la configuración de todos los módulos, la combina y guarda el resultado combinado en la caché. Esta caché también contiene configuraciones específicas del almacén almacenadas en el sistema de archivos y la base de datos. Limpie o vacíe este tipo de caché después de modificar los archivos de configuración. |
| Diseño | layout | Presentaciones de página compiladas (es decir, los componentes de diseño de todos los componentes). Limpie o vacíe este tipo de caché después de modificar los archivos de diseño. |
| Salida del HTML de bloque | block_html | HTML de fragmentos de página por bloque. Limpie o vacíe este tipo de caché después de modificar la capa de vista. |
| Datos de colecciones | colecciones | Resultados de consultas de base de datos. Si es necesario, Commerce limpia esta caché automáticamente, pero los desarrolladores de terceros pueden colocar cualquier dato en cualquier segmento de la caché. Limpie o vacíe este tipo de caché si su módulo personalizado utiliza una lógica que genere entradas de caché que Commerce no pueda limpiar. |
| DDL | db_ddl | Esquema de base de datos. Si es necesario, Commerce limpia esta caché automáticamente, pero los desarrolladores de terceros pueden colocar cualquier dato en cualquier segmento de la caché. Limpie o vacíe este tipo de caché después de realizar cambios personalizados en el esquema de la base de datos. (En otras palabras, actualizaciones que Commerce no se hace a sí mismo). Una forma de actualizar el esquema de la base de datos automáticamente es utilizando la variable `magento setup:db-schema:upgrade` comando. |
| Configuración compilada | compile_config | Configuración de compilación |
| Valor de atributo de entidad (EAV) | eav | Metadatos relacionados con atributos EAV (por ejemplo, etiquetas de tienda, vínculos a código PHP relacionado, renderización de atributos, configuración de búsqueda, etc.). Normalmente no es necesario limpiar o vaciar este tipo de caché. |
| Caché de página | full_page | Generó páginas HTML. Si es necesario, Commerce limpia esta caché automáticamente, pero los desarrolladores de terceros pueden colocar cualquier dato en cualquier segmento de la caché. Limpie o vacíe este tipo de caché después de modificar el nivel de código que afecta a la salida del HTML. Se recomienda mantener esta caché habilitada porque el HTML de almacenamiento en caché mejora significativamente el rendimiento. |
| Reflejo | reflejo | Elimina una dependencia entre el módulo Webapi y el módulo Cliente. |
| Traducciones | translate | Después de combinar las traducciones de todos los módulos, se limpiará la caché de fusión. |
| Configuración de integración | config_integration | Integraciones compiladas. Limpie o vacíe esta caché después de cambiar o agregar integraciones. |
| Configuración de la API de integración | config_integration_api | Configuración de las API de integración compiladas de las integraciones de la tienda. |
| Configuración de servicios web | config_webservice | Almacenamiento en caché de la estructura de la API web. |
| Notificación al cliente | customer_notification | Notificaciones temporales que aparecen en la interfaz de usuario. |

## Ver el estado de la caché

Para ver el estado de la caché, introduzca

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

A continuación se muestra una muestra:

```terminal
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
                           eav: 1
         customer_notification: 1
                     full_page: 1
            config_integration: 1
        config_integration_api: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

## Habilitar o deshabilitar tipos de caché

Este comando le permite habilitar o deshabilitar todos los tipos de caché o solo los que especifique. Deshabilitar tipos de caché es útil durante el desarrollo, ya que puede ver los resultados de los cambios sin tener que vaciar la caché; sin embargo, deshabilitar los tipos de caché tiene un efecto adverso en el rendimiento.

>[!INFO]
>
>A partir de la versión 2.2, solo puede habilitar o deshabilitar los tipos de caché mediante la línea de comandos mientras ejecuta Commerce en modo de producción. Si ejecuta Commerce en modo de desarrollador, puede habilitar o deshabilitar los tipos de caché mediante la línea de comandos o manualmente. Antes de hacerlo, debe realizar manualmente `<magento_root>/app/etc/env.php` grabable por el [propietario del sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html).

Puede limpiar (también denominado _flush_ o _actualizar_) tipos de caché que utilizan la línea de comandos o el administrador.

Opciones de comando:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Donde omita `[type]` habilita o deshabilita todos los tipos de caché al mismo tiempo. La variable `type` es una lista de tipos de caché separados por espacios.

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

Para enumerar los tipos de caché y su estado:

```bash
bin/magento cache:status
```

Por ejemplo, para deshabilitar la caché de página completa y la caché de DDL:

```bash
bin/magento cache:disable db_ddl full_page
```

Resultado de la muestra:

```terminal
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>Al habilitar un tipo de caché, se borra automáticamente ese tipo de caché.

>[!INFO]
>
>A partir de la versión 2.3.4, Commerce almacena en caché todos los atributos EAV del sistema a medida que se recuperan. El almacenamiento en caché de los atributos EAV de esta manera mejora el rendimiento, ya que disminuye la cantidad de solicitudes de inserción/selección a la base de datos. Sin embargo, también aumenta el tamaño de la red de caché. Los desarrolladores pueden almacenar en caché atributos EAV personalizados ejecutando el `bin/magento config:set dev/caching/cache_user_defined_attributes 1` comando. Esto también se puede hacer desde el administrador mientras se [Modo de desarrollador](../bootstrap/application-modes.md) estableciendo **Almacenes** > Configuración **Configuración** > **Avanzadas** > **Desarrollador** > **Configuración de almacenamiento en caché** > **Atributos definidos por el usuario de caché** a **Sí**.

## Limpiar y vaciar tipos de caché

Para purgar elementos obsoletos de la caché, puede _clean_ o _flush_ tipos de caché:

- Al limpiar un tipo de caché, se eliminan todos los elementos únicamente de los tipos de caché de Commerce habilitados. En otras palabras, esta opción no afecta a otros procesos o aplicaciones porque limpia solamente la caché que utiliza Commerce.

   Los tipos de caché deshabilitados no se limpian.

   >[!TIP]
   >
   >Limpie siempre la caché después de actualizar las versiones de Magento Open Source o Adobe Commerce, actualizar de Magento Open Source a Adobe Commerce o instalar B2B para Adobe Commerce o cualquier módulo.

- Al vaciar un tipo de caché, se purga el almacenamiento de caché, lo que podría afectar a otras aplicaciones de procesos que estén utilizando el mismo almacenamiento.

Vaciar tipos de caché si ya ha intentado limpiar la caché y sigue teniendo problemas que no puede aislar.

Uso de comandos:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Donde `[type]` es una lista de tipos de caché separados por espacios. Omisión `[type]` limpia o descarga todos los tipos de caché al mismo tiempo. Por ejemplo, para vaciar todos los tipos de caché, escriba

```bash
   bin/magento cache:flush
```

Resultado de la muestra:

```terminal
   Flushed cache types:
   config
   layout
   block_html
   collections
   reflection
   db_ddl
   compiled_config
   eav
   customer_notification
   config_integration
   config_integration_api
   full_page
   config_webservice
   translate
```

>[!TIP]
>
>También puede limpiar y vaciar tipos de caché en Admin. Vaya a **Sistema** > **Herramientas** > **Administración de caché**. **Almacenamiento de caché de vaciado** es equivalente a `bin/magento cache:flush`. **Vaciar caché del Magento** es equivalente a `bin/magento cache:clean`.
