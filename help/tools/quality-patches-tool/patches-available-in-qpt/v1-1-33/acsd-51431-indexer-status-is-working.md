---
title: "ACSD-51431: el estado del indizador es *[!UICONTROL Working]* aunque no haya entradas en el registro de cambios"
description: Aplique el parche ACSD-51431 para corregir el problema de Adobe Commerce en el que el estado del indexador es *[!UICONTROL Working]* aunque no haya entradas en el registro de cambios.
feature: Logs, Price Indexer
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-51431: el estado del indizador es *[!UICONTROL Working]* aunque no haya entradas en el registro de cambios

El parche ACSD-51431 corrige el problema de rendimiento en el que el estado del indizador es *[!UICONTROL Working]* aunque no haya entradas en el registro de cambios. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.33. El ID del parche es ACSD-51431. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado del indizador es *[!UICONTROL Working]* aunque no haya entradas en el registro de cambios.

<u>Pasos a seguir</u>:

1. Establezca **[!UICONTROL indexers]** en [!UICONTROL Update on Schedule].
1. Configure el trabajo cron para que se ejecute cada minuto.
1. Guarde los cambios en diferentes productos simultáneamente.
1. Ejecutar `bin/magento indexer:status` en un par de minutos.

<u>Resultados esperados</u>:

Los cambios se procesan y los indizadores se encuentran en estado *[!UICONTROL Ready]*. El estado de *[!UICONTROL Schedule]* es *[!UICONTROL idle (0 in the backlog)]*.

<u>Resultados reales</u>:

Los cambios se procesan y los indizadores se encuentran en estado *[!UICONTROL Ready]*. Sin embargo, el estado *[!UICONTROL Schedule]* muestra *[!UICONTROL working (0 in the backlog)]*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
