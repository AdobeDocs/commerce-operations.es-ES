---
title: Administrar la caché
description: Administrar tipos de caché y ver su estado.
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: 5c316ade0619603eafa7ece8a7cd8c1595dee713
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---

# Administrar la caché

{{file-system-owner}}

## Tipos de caché

Commerce 2 tiene los siguientes tipos de caché:

| Nombre &quot;descriptivo&quot; del tipo de caché | Nombre de código de tipo de caché | Descripción |
|--- |--- |--- |
| Configuración | config | Commerce recopila la configuración de todos los módulos, la combina y guarda el resultado combinado en la caché. Esta caché también contiene la configuración específica del almacén almacenada en el sistema de archivos y en la base de datos. Limpie o vacíe este tipo de caché después de modificar los archivos de configuración. |
| Diseño | layout | Diseños de página compilados (es decir, los componentes de diseño de todos los componentes). Limpie o vacíe este tipo de caché después de modificar los archivos de diseño. |
| Bloquear salida del HTML | block_html | Fragmentos de página del HTML por bloque. Limpie o vacíe este tipo de caché después de modificar la capa de visualización. |
| Datos de colecciones | colecciones | Resultados de consultas de base de datos. Si es necesario, Commerce limpia esta caché automáticamente, pero los desarrolladores de terceros pueden colocar cualquier dato en cualquier segmento de la caché. Limpie o vacíe este tipo de caché si el módulo personalizado utiliza una lógica que genere entradas de caché que Commerce no pueda limpiar. |
| DDL | db_ddl | Esquema de base de datos. Si es necesario, Commerce limpia esta caché automáticamente, pero los desarrolladores de terceros pueden colocar cualquier dato en cualquier segmento de la caché. Limpie o vacíe este tipo de caché después de realizar cambios personalizados en el esquema de la base de datos. (En otras palabras, actualizaciones que Commerce no se hace a sí mismo). Una forma de actualizar el esquema de la base de datos automáticamente es utilizar `magento setup:db-schema:upgrade` comando. |
| Configuración compilada | compilation_config | Configuración de compilación |
| Valor de atributo de entidad (EAV) | alero | Metadatos relacionados con atributos EAV (por ejemplo: etiquetas de tienda, vínculos a código PHP relacionado, renderización de atributos, configuración de búsqueda, etc.). Normalmente, no es necesario limpiar ni vaciar este tipo de caché. |
| Caché de página | full_page | Páginas de HTML generadas. Si es necesario, Commerce limpia esta caché automáticamente, pero los desarrolladores de terceros pueden colocar cualquier dato en cualquier segmento de la caché. Limpie o vacíe este tipo de caché después de modificar el nivel de código que afecta a la salida del HTML. Se recomienda mantener esta caché habilitada porque el HTML de almacenamiento en caché mejora significativamente el rendimiento. |
| Reflexión | reflexión | Elimina una dependencia entre el módulo Webapi y el módulo Cliente. |
| Traducciones | traducir | Después de combinar las traducciones de todos los módulos, la caché de la fusión se limpiará. |
| Configuración de integración | config_integration | Integraciones compiladas. Limpie o vacíe esta caché después de cambiar o agregar integraciones. |
| Configuración de API de integración | config_integration_api | Configuración de las API de integración compiladas de las integraciones de la tienda. |
| Configuración de servicios web | config_webservice | Almacenar en caché la estructura de la API web. |
| Notificación al cliente | customer_notification | Notificaciones temporales que aparecen en la interfaz de usuario. |

## Ver el estado de la caché

Para ver el estado de la caché, introduzca.

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

A continuación se muestra un ejemplo:

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

Este comando permite habilitar o deshabilitar todos los tipos de caché o sólo los especificados. Deshabilitar los tipos de caché resulta útil durante el desarrollo porque se ven los resultados de los cambios sin tener que vaciar la caché; sin embargo, deshabilitar los tipos de caché tiene un efecto adverso en el rendimiento.

>[!INFO]
>
>A partir de la versión 2.2, solo puede habilitar o deshabilitar los tipos de caché mediante la línea de comandos mientras ejecuta Commerce en modo de producción. Si ejecuta Commerce en modo de desarrollador, puede activar o desactivar los tipos de caché mediante la línea de comandos o manualmente. Antes de hacerlo, debe realizar manualmente lo siguiente `<magento_root>/app/etc/env.php` escribible por el [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).

Puede limpiar (también denominado _vaciar_ o _actualizar_) tipos de caché utilizando la línea de comandos o el administrador.

Opciones de comando:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Dónde omitir `[type]` habilita o deshabilita todos los tipos de caché al mismo tiempo. El `type` es una lista de tipos de caché separados por espacios.

<!-- `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md#bootstrap-parameters) and values. -->

Para enumerar los tipos de caché y su estado:

```bash
bin/magento cache:status
```

Por ejemplo, para deshabilitar la memoria caché de la página completa y la memoria caché DDL:

```bash
bin/magento cache:disable db_ddl full_page
```

Resultado de muestra:

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
>A partir de la versión 2.3.4, Commerce almacena en caché todos los atributos EAV del sistema a medida que se recuperan. El almacenamiento en caché de atributos de EAV de esta manera mejora el rendimiento, ya que disminuye la cantidad de solicitudes de inserción/selección a la base de datos. Sin embargo, también aumenta el tamaño de la red de la caché. Los desarrolladores pueden almacenar en caché los atributos personalizados de EAV ejecutando el `bin/magento config:set dev/caching/cache_user_defined_attributes 1` comando. Esto también se puede hacer desde el administrador mientras se encuentra en [Modo de desarrollador](../bootstrap/application-modes.md) por configuración **Tiendas** > Configuración **Configuración** > **Avanzadas** > **Desarrollador** > **Configuración de almacenamiento en caché** > **Atributos definidos por el usuario de caché** hasta **Sí**.

## Limpiar y vaciar tipos de caché

>[!NOTE]
>
>La caché de varias páginas se puede invalidar simultánea y automáticamente **_sin_** estas entidades están editando. Por ejemplo, cuando cualquier producto del catálogo se asigna a una categoría o cuando [!UICONTROL related product rule] se ha modificado.

Para eliminar de la caché elementos que no estén actualizados, puede _limpio_ o _vaciar_ tipos de caché:

- Al limpiar un tipo de caché, se eliminan todos los elementos de los tipos de caché de Commerce habilitados únicamente. En otras palabras, esta opción no afecta a otros procesos o aplicaciones porque limpia únicamente la caché que utiliza Commerce.

  Los tipos de caché deshabilitados no se limpian.

  >[!TIP]
  >
  >Limpie siempre la caché después de actualizar versiones de Magento Open Source o Adobe Commerce, actualizar de Magento Open Source a Adobe Commerce o instalar B2B para Adobe Commerce o cualquier módulo.

- Al vaciar un tipo de caché, se depura el almacenamiento de caché, lo que podría afectar a otros procesos y aplicaciones que estén utilizando el mismo almacenamiento.

Vaciar tipos de caché si ya ha intentado limpiar la caché y aún tiene problemas que no puede aislar.

Uso de comandos:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Donde `[type]` es una lista de tipos de caché separados por espacios. Omitir `[type]` limpia o vacía todos los tipos de caché al mismo tiempo. Por ejemplo, para vaciar todos los tipos de caché, introduzca

```bash
   bin/magento cache:flush
```

Resultado de muestra:

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
>También puede limpiar y vaciar tipos de caché en el Administrador. Ir a **Sistema** > **Herramientas** > **Administración de caché**. **Vaciar almacenamiento de caché** es equivalente a `bin/magento cache:flush`. **Vaciar caché del Magento** es equivalente a `bin/magento cache:clean`.
