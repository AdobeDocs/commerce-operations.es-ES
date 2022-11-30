---
title: Configuración del motor de búsqueda
description: Configure un motor de búsqueda con Adobe Commerce y Magento Open Source.
source-git-commit: 66681f06c15907a5d25e71005c27785f0745ed63
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Configuración del motor de búsqueda

En esta sección se describen las configuraciones mínimas que debe elegir para probar el Elasticsearch o OpenSearch con Adobe Commerce y el Magento Open Source. En las versiones 2.4.4 y 2.4.3-p2, todos los campos están etiquetados **Elasticsearch** también se aplican a OpenSearch.

Para obtener más información sobre la configuración del motor de búsqueda, consulte la [Guía del usuario](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html).

## Configure el motor de búsqueda desde el administrador

Para configurar el sistema para que utilice Elasticsearch o OpenSearch:

1. Inicie sesión en Admin como administrador.
1. Haga clic en **Almacenes** > Configuración > **Configuración** > **Catálogo** > **Catálogo** > **Buscar en el catálogo**.
1. En el **Motor de búsqueda** seleccione la versión correspondiente de su motor de búsqueda Si está utilizando OpenSearch, debe seleccionar Elasticsearch7.

   En la tabla siguiente se enumeran las opciones de configuración necesarias para configurar y probar la conexión con Commerce.
A menos que cambie la configuración del servidor del motor de búsqueda, los valores predeterminados deberían funcionar. Pasa al siguiente paso.

   | Opción | Descripción |
   |--- |--- |
   | **Nombre de host del servidor Elasticsearch** | Introduzca el nombre de host o la dirección IP completa del equipo que ejecuta el Elasticsearch o OpenSearch.<br>Adobe Commerce en infraestructura de nube: Obtenga este valor de su sistema de integración. |
   | **Puerto del servidor Elasticsearch** | Introduzca el puerto proxy del servidor web. El valor predeterminado es 9200<br>Adobe Commerce en infraestructura de nube: Obtenga este valor de su sistema de integración. |
   | **Prefijo de índice del Elasticsearch** | Introduzca el prefijo de índice del motor de búsqueda. Si utiliza una sola instancia para más de una instalación de Commerce (entornos de ensayo y producción), debe especificar un prefijo único para cada instalación. De lo contrario, puede utilizar el prefijo predeterminado magento2. |
   | **Habilitar autenticación HTTP del Elasticsearch** | Haga clic en **Sí** solo si ha activado la autenticación en el servidor de motor de búsqueda. Si es así, proporcione un nombre de usuario y una contraseña en los campos proporcionados. |

1. Haga clic en **Probar conexión**.

   Respuesta de ejemplo:

   ![success](../../assets/configuration/elastic_test-success.png)

   Continúe con:

   - [Configurar Apache para su motor de búsqueda](../../installation/prerequisites/search-engine/configure-apache.md)
   - [Configure nginx en su motor de búsqueda](../../installation/prerequisites/search-engine/configure-nginx.md)

   o verá:

   ![failed](../../assets/configuration/elastic_test-fail.png)

Si es así, pruebe lo siguiente:

- Asegúrese de que el servidor del motor de búsqueda se esté ejecutando.
- Si el servidor se encuentra en un host diferente de Commerce, inicie sesión en el servidor de Commerce y haga ping en el host del motor de búsqueda. Resuelva los problemas de conectividad de red y vuelva a probar la conexión.
- Examine la ventana de comandos en la que inició Elasticsearch o OpenSearch para detectar rastros y excepciones de pila. Debe resolverlos antes de continuar. En concreto, asegúrese de que inició su motor de búsqueda como usuario con `root` privilegios.
- Asegúrese de que [Firewall UNIX y SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) están deshabilitadas o configuran reglas para permitir que su motor de búsqueda y Comercio se comuniquen entre sí.
- Compruebe el valor de la variable **Nombre de host del servidor Elasticsearch** campo . Asegúrese de que el servidor esté disponible. Puede probar la dirección IP del servidor en su lugar.
- Utilice la variable `netstat -an | grep <listen-port>` para verificar que el puerto especificado en la variable **Puerto del servidor Elasticsearch** no se está utilizando en otro proceso.

   Por ejemplo, para ver si el motor de búsqueda se está ejecutando en su puerto predeterminado, utilice el siguiente comando:

   ```bash
   netstat -an | grep 9200
   ```

   Si se está ejecutando en el puerto 9200, se muestra similar a lo siguiente:

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## Reindexación de la búsqueda en el catálogo y actualización de la caché de página completa

Después de cambiar la configuración del motor de búsqueda, debe reindexar el índice de búsqueda del catálogo y actualizar la caché de página completa mediante la línea de comandos o el administrador.

Para actualizar la caché mediante el administrador:

1. En el Administrador, haga clic en **Sistema** > **Administración de caché**.
1. Seleccione la casilla de verificación situada junto a **Caché de página**.
1. En el **Acciones** en la lista superior derecha, haga clic en **Actualizar**.

   ![administración de caché](../../assets/configuration/refresh-cache.png)

Para limpiar la caché con la línea de comandos: [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

Para reindexar usando la línea de comandos:

1. Inicie sesión en el servidor de Commerce como, o cambie a [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Introduzca cualquiera de los siguientes comandos:

   Introduzca el siguiente comando para reindexar solo el índice de búsqueda del catálogo:

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   Introduzca el siguiente comando para reindexar todos los indexadores:

   ```bash
   bin/magento indexer:reindex
   ```

1. Espere hasta que se complete la reindexación.

   >[!INFO]
   >
   >A diferencia de la caché, los indexadores se actualizan mediante un trabajo cron. Asegúrese de [cron está habilitado](../cli/configure-cron-jobs.md) antes de empezar a utilizar el motor de búsqueda.

