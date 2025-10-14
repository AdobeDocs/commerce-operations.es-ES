---
title: 'ACSD-51036: Las condiciones de carrera durante las llamadas simultáneas a la API de REST resultan en una sobrescritura del estado de envío'
description: Aplique el parche ACSD-51036 para corregir el problema de Adobe Commerce donde hay condiciones de carrera durante las llamadas simultáneas a la API de REST, lo que provoca una sobrescritura del estado de envío en la tabla de artículos pedidos.
feature: REST, Orders, Shipping/Delivery
role: Admin
exl-id: 6150d072-05fe-4010-b31b-8ccde9cab656
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '394'
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
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
