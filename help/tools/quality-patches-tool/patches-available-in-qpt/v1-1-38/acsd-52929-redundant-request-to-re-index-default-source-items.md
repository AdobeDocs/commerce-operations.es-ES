---
title: "ACSD-52929: Solicitud redundante para reindexar elementos de origen predeterminados"
description: Aplique el parche ACSD-52929 para corregir el problema de Adobe Commerce en el que hay una solicitud redundante para reindexar los elementos de origen predeterminados cuando el indexador de inventario está configurado en modo asincrónico.
feature: Configuration, Inventory
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-52929: Solicitud redundante para reindexar elementos de origen predeterminados

El parche ACSD-52929 corrige el problema en el que hay una redundancia de solicitudes para reindexar elementos de origen predeterminados cuando el indexador de inventario está configurado en modo asincrónico. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.38. El ID del parche es ACSD-52929. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Hay una redundancia de solicitudes para reindexar los elementos de origen predeterminados cuando el indexador de inventario está configurado en modo asincrónico.

<u>Pasos a seguir</u>:

1. Configurar [!DNL RabbitMQ].
1. Para habilitar la estrategia de reindexación asincrónica, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Inventory Indexer Setting]** y establezca **[!UICONTROL Stock/Source reindex strategy]=[!UICONTROL Asynchronous]**.
1. Crear un origen de inventario personalizado.
1. Inicie sesión en el tablero [!DNL RabbitMQ] y vaya a la ficha colas.
1. Compruebe la cola `inventory.indexer.sourceItem` y asegúrese de que no contenga mensajes.
1. Abra un producto simple desde el backend y agregue *[!UICONTROL stock only]* al origen personalizado y guarde el producto.
1. Cargue la cola `inventory.indexer.sourceItem` en el panel [!DNL RabbitMQ] y, a continuación, compruebe los mensajes.

<u>Resultados esperados</u>:

Solo hay un mensaje en la cola para el origen personalizado.

<u>Resultados reales</u>:

Se muestran dos mensajes en la cola: uno para el origen predeterminado y otro para el origen personalizado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
