---
title: 'ACSD-51036: Las condiciones de carrera durante las llamadas simultáneas a la API de REST resultan en una sobrescritura del estado de envío'
description: Aplique el parche ACSD-51036 para corregir el problema de Adobe Commerce donde hay condiciones de carrera durante las llamadas simultáneas a la API de REST, lo que provoca una sobrescritura del estado de envío en la tabla de artículos pedidos.
feature: REST, Orders, Shipping/Delivery
role: Admin
exl-id: 6150d072-05fe-4010-b31b-8ccde9cab656
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%
---
# ACSD-51036: Las condiciones de carrera durante las llamadas simultáneas a la API de REST resultan en una sobrescritura del estado de envío en la tabla de artículos pedidos

El parche ACSD-51036 corrige el problema en el que las condiciones de carrera durante las llamadas simultáneas a la API de REST dan como resultado una sobrescritura del estado de envío en la tabla de artículos pedidos. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.31. El ID del parche es ACSD-51036. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las condiciones de carrera durante las llamadas simultáneas a la API de REST dan como resultado una sobrescritura del estado de envío en la tabla de artículos pedidos.

<u>Pasos a seguir</u>:

1. Cree un pedido con dos elementos.
1. Artículo de Factura A.
1. Envía una solicitud de reembolso para el artículo A a través de la API de REST simultáneamente mientras envías una solicitud de envío para el artículo B.
1. Ir al pedido en **[!UICONTROL Admin Panel]**.

<u>Resultados esperados</u>

El estado *[!UICONTROL Shipped 1]* debe estar presente para el elemento B en la tabla ordenada *[!UICONTROL Items]*.

<u>Resultados reales</u>

El estado *[!UICONTROL Shipped 1]* no está presente para el elemento B en la tabla ordenada *[!UICONTROL Items]*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
