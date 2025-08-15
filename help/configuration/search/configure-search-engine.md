---
title: Configuración del motor de búsqueda
description: Configure un motor de búsqueda para implementaciones locales de Adobe Commerce.
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# Configuración del motor de búsqueda

En esta sección se analiza la configuración mínima que debe elegir para probar Elasticsearch o OpenSearch con implementaciones locales de Adobe Commerce.

>[!TIP]
>
>En las versiones 2.4.4 y 2.4.3-p2, todos los campos etiquetados como **Elasticsearch** también se aplican a OpenSearch.
>>Cuando se introdujo la compatibilidad con Elasticsearch 8.x en la versión 2.4.6, se crearon nuevas etiquetas para distinguir entre las configuraciones de Elasticsearch y OpenSearch.

Para obtener más información sobre cómo configurar el motor de búsqueda, consulta la [Guía del usuario](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html).

## Configure el motor de búsqueda desde Admin

>[!TIP]
>
>Para obtener instrucciones sobre cómo actualizar a una nueva versión de motor de búsqueda, consulte [requisitos previos de actualización](../../upgrade/prepare/prerequisites.md).

Para configurar el sistema para que utilice Elasticsearch u OpenSearch:

1. Inicie sesión en el administrador como administrador.
1. Haga clic en **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. En la lista **[!UICONTROL Search Engine]**, seleccione la versión correspondiente del motor de búsqueda.

   En la tabla siguiente se enumeran las opciones necesarias para configurar y probar la conexión con Commerce. A menos que cambie la configuración del servidor del motor de búsqueda, los valores predeterminados deberían funcionar. Pasar al paso siguiente.

   | Opción | Descripción |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | Introduzca el nombre de host completo o la dirección IP del equipo que ejecuta Elasticsearch o OpenSearch.<br>Adobe Commerce en la infraestructura de la nube: obtenga este valor de su sistema de integración. |
   | **[!UICONTROL Server Port]** | Introduzca el puerto proxy del servidor web. El valor predeterminado es 9200<br>Adobe Commerce en la infraestructura en la nube: obtenga este valor de su sistema de integración. |
   | **[!UICONTROL Index Prefix]** | Introduzca el prefijo de índice del motor de búsqueda. Si utiliza una sola instancia para más de una instalación de Commerce (entornos de ensayo y producción), debe especificar un prefijo único para cada instalación. De lo contrario, puede utilizar el prefijo predeterminado magento2. |
   | **[!UICONTROL Enable HTTP Auth]** | Haga clic en **[!UICONTROL Yes]** solo si habilitó la autenticación para el servidor del motor de búsqueda. Si es así, proporcione un nombre de usuario y una contraseña en los campos proporcionados. |
   | **[!UICONTROL Server Timeout]** | Especifique la cantidad de tiempo (en segundos) de espera al intentar establecer una conexión con el servidor de Elasticsearch o OpenSearch. |

1. Haga clic en **[!UICONTROL Test Connection]**.

   Respuesta de ejemplo:

   ![éxito](../../assets/configuration/elastic_test-success.png)

   Continúe con:

   - [Configuración de Apache para el motor de búsqueda](../../installation/prerequisites/search-engine/configure-apache.md)
   - [Configuración de nginx para el motor de búsqueda](../../installation/prerequisites/search-engine/configure-nginx.md)

   o verá:

   ![error](../../assets/configuration/elastic_test-fail.png)

Si es así, intente lo siguiente:

- Asegúrese de que el servidor del motor de búsqueda se esté ejecutando.
- Si el servidor se encuentra en un host diferente al de Commerce, inicie sesión en el servidor de Commerce y haga ping en el host del motor de búsqueda. Resuelva los problemas de conectividad de red y vuelva a probar la conexión.
- Examine la ventana de comandos en la que inició Elasticsearch u OpenSearch para buscar los seguimientos de pila y las excepciones. Debe resolverlos antes de continuar. En particular, asegúrese de iniciar el motor de búsqueda como usuario con privilegios de `root`.
- Asegúrese de que [Firewall de UNIX y SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) estén deshabilitados, o configure reglas para permitir que el motor de búsqueda y Commerce se comuniquen entre sí.
- Compruebe el valor del campo **[!UICONTROL Server Hostname]**. Asegúrese de que el servidor esté disponible. En su lugar, puede probar la dirección IP del servidor.
- Utilice el comando `netstat -an | grep <listen-port>` para comprobar que el puerto especificado en el campo **[!UICONTROL Server Port]** no está siendo utilizado por otro proceso.

  Por ejemplo, para ver si el motor de búsqueda se está ejecutando en el puerto predeterminado, utilice el siguiente comando:

  ```bash
  netstat -an | grep 9200
  ```

  Si se ejecuta en el puerto 9200, se muestra de forma similar a la siguiente:

  ```
  `tcp        0      0 :::9200            :::-         LISTEN`
  ```

## Reindexe la búsqueda en el catálogo y actualice la caché de la página completa

Después de cambiar la configuración del motor de búsqueda, debe reindexar el índice de búsqueda del catálogo y actualizar la caché de la página completa mediante la línea de comandos Admin o.

Para actualizar la caché con el administrador:

1. En el Administrador, haga clic en **[!UICONTROL System]** > **[!UICONTROL Cache Management]**.
1. Seleccione la casilla que está junto a **[!UICONTROL Page Cache]**.
1. En la lista **[!UICONTROL Actions]** de la esquina superior derecha, haga clic en **Actualizar**.

   ![administración de caché](../../assets/configuration/refresh-cache.png)

Para limpiar la caché mediante la línea de comandos: [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

Para reindexar con la línea de comandos:

1. Inicie sesión en el servidor de Commerce como [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md) o cambie a él.
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
   >A diferencia de la caché, los indexadores se actualizan mediante un trabajo cron. Asegúrese de que [cron esté habilitado](../cli/configure-cron-jobs.md) antes de empezar a usar el motor de búsqueda.
