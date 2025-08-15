---
title: Administrar la caché
description: Administre los tipos de caché y vea el estado de la caché desde la línea de comandos utilizando la CLI de Commerce
exl-id: bbd76c00-727b-412e-a8e5-1e013a83a29a
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Administrar la caché

{{file-system-owner}}

## Tipos de caché

Puede utilizar el sistema de administración de caché de Adobe Commerce para mejorar el rendimiento del sitio. En este tema se explica cómo los administradores de sistemas o los desarrolladores con acceso al servidor de aplicaciones de Commerce pueden administrar las cachés desde la línea de comandos.

>[!NOTE]
>
>
>Los administradores del sitio de Commerce pueden administrar la caché desde el Administrador mediante la herramienta Cache Management System (Sistema de administración de caché). Consulte [Administración de caché](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) en la _Guía de sistemas de administración_.


## Ver el estado de la caché

Desde la línea de comandos del servidor de aplicaciones de Commerce, vea el estado de la caché mediante el comando CLI de Commerce `cache:status`.

```bash
   bin/magento cache:status
```

<!-- where `--bootstrap=` is a URL-encoded associative array of Commerce [application bootstrap parameters](../bootstrap/set-parameters.md) and values. -->

A continuación se muestra un ejemplo:

```
Current status:
                        config: 1
                        layout: 1
                    block_html: 1
                   collections: 1
                    reflection: 1
                        db_ddl: 1
               compiled_config: 1
             webhooks_response: 1
                           eav: 1
         customer_notification: 1
 graphql_query_resolver_result: 1
            config_integration: 1
        config_integration_api: 1
                  admin_ui_sdk: 1
                     full_page: 1
                   target_rule: 1
             config_webservice: 1
                     translate: 1
```

>[!TIP]
>
>Para obtener una descripción detallada de los tipos de caché predeterminados admitidos por Adobe Commerce, consulte [Cachés](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#caches) en la _Guía de sistemas de administración_.


## Habilitar o deshabilitar tipos de caché

Este comando permite habilitar o deshabilitar todos los tipos de caché o sólo los especificados. Deshabilitar los tipos de caché resulta útil durante el desarrollo porque se ven los resultados de los cambios sin tener que vaciar la caché; sin embargo, deshabilitar los tipos de caché tiene un efecto adverso en el rendimiento.

>[!INFO]
>
>A partir de la versión 2.2, solo puede habilitar o deshabilitar los tipos de caché mediante la línea de comandos mientras ejecuta Commerce en modo de producción. Si ejecuta Commerce en modo de desarrollador, puede habilitar o deshabilitar los tipos de caché mediante la línea de comandos o manualmente. Antes de hacerlo, debe hacer que `<magento_root>/app/etc/env.php` sea editable manualmente por el [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).

Puede limpiar los tipos de caché (también conocidos como _flush_ o _refresh_) usando la línea de comandos o el administrador.

Opciones de comando:

```bash
bin/magento cache:enable [type] ... [type]
```

```bash
bin/magento cache:disable [type] ... [type]
```

Donde omitir `[type]` habilita o deshabilita todos los tipos de caché al mismo tiempo. La opción `type` es una lista de tipos de caché separados por espacios.

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

```
   Changed cache status:
       db_ddl: 1 -> 0
    full_page: 1 -> 0
```

>[!INFO]
>
>Al habilitar un tipo de caché, se borra automáticamente ese tipo de caché.

>[!INFO]
>
>En la versión 2.3.4, Commerce almacena en caché todos los atributos EAV del sistema a medida que se recuperan. El almacenamiento en caché de atributos de EAV de esta manera mejora el rendimiento, ya que disminuye la cantidad de solicitudes de inserción/selección a la base de datos. Sin embargo, también aumenta el tamaño de la red de la caché. Los desarrolladores pueden almacenar en caché atributos EAV personalizados ejecutando el comando `bin/magento config:set dev/caching/cache_user_defined_attributes 1`. Esto también se puede hacer desde el administrador mientras se está en [modo de desarrollador](../bootstrap/application-modes.md), configurando **Tiendas** > Configuración **Configuration** > **Advanced** > **Developer** > **Configuración de almacenamiento en caché** > **Atributos definidos por el usuario de la caché** en **Yes**.

## Limpiar y vaciar tipos de caché

>[!NOTE]
>
>La caché de varias páginas se puede invalidar simultáneamente y **_automáticamente sin_** estas entidades editando. Por ejemplo, cuando se asigna cualquier producto del catálogo a cualquier categoría o cuando se modifica cualquier [!UICONTROL related product rule].

Para purgar elementos obsoletos de la caché, puede _limpiar_ o _vaciar_ tipos de caché:

- Al limpiar un tipo de caché, se eliminan todos los elementos de los tipos de caché de Commerce habilitados únicamente. En otras palabras, esta opción no afecta a otros procesos o aplicaciones porque limpia únicamente la caché que utiliza Commerce.

  Los tipos de caché deshabilitados no se limpian.

  >[!TIP]
  >
  >Limpie siempre la caché después de actualizar versiones de Adobe Commerce, actualizar de Magento Open Source a Adobe Commerce o instalar B2B para Adobe Commerce o cualquier módulo.

- Al vaciar un tipo de caché, se depura el almacenamiento de caché, lo que podría afectar a otros procesos y aplicaciones que estén utilizando el mismo almacenamiento.

Vaciar tipos de caché si ya ha intentado limpiar la caché y aún tiene problemas que no puede aislar.

Uso de comandos:

```bash
   bin/magento cache:clean [type] ... [type]
```

```bash
   bin/magento cache:flush [type] ... [type]
```

Donde `[type]` es una lista de tipos de caché separados por espacios. Al omitir `[type]`, se limpian o vacían todos los tipos de caché al mismo tiempo. Por ejemplo, para vaciar todos los tipos de caché, introduzca

```bash
   bin/magento cache:flush
```

Resultado de muestra:

```
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
   graphql_query_resolver_results
   config_webservice
   translate
```

>[!TIP]
>
>También puede limpiar y vaciar tipos de caché en el Administrador. Vaya a **Sistema** > **Herramientas** > **Administración de caché**. **Vaciar almacenamiento de caché** equivale a `bin/magento cache:flush`. **Vaciar la caché de Magento** equivale a `bin/magento cache:clean`.
