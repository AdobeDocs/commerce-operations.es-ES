---
title: 'ACSD-51431: el estado del indizador es *[!UICONTROL Working]* aunque no haya entradas en el registro de cambios'
description: Aplique el parche ACSD-51431 para corregir el problema de Adobe Commerce en el que el estado del indexador es *[!UICONTROL Working]* aunque no haya entradas en el registro de cambios.
feature: Logs, Price Indexer
role: Admin
exl-id: c87c059b-f435-468d-a7fe-e6786fdba1f8
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 3c398179-d35a-51ba-b317-6c5b95feef5e
    internal-label: Logs
  - id: b0d35b91-b9b0-5983-b37c-f35bd2650b53
    internal-label: Price Indexer
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '381'
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
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
