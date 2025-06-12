---
title: 'ACSD-54739: *[!UICONTROL Product Stock]* estado no aplicado para *[!UICONTROL Related Product Rules]*'
description: Aplique el parche ACSD-54739 para corregir el problema de Adobe Commerce en el que el estado *[!UICONTROL Product Stock]* no se aplica a *[!UICONTROL Related Product Rules]*.
feature: Products
role: Admin, Developer
exl-id: d6d3b25d-b10e-4ccb-a9c4-b5c1c7773eb6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACSD-54739: el estado de *[!UICONTROL Product stock]* no se aplicó a *[!UICONTROL Related Product Rules]*

El parche ACSD-54739 corrige el problema en el que el estado *[!UICONTROL Product stock]* no se aplica a *[!UICONTROL Related Product Rules]*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43. El ID del parche es ACSD-54739. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado *[!UICONTROL Product stock]* no se ha aplicado a *[!UICONTROL Related Product Rules]*.

<u>Pasos a seguir</u>:

1. Establezca la configuración de **[!UICONTROL Display Out of Stock Products]** en *Sí*.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]** y establezca *Sí* para la condición de regla de promoción.
1. Cree la regla de producto relacionada. Vaya a **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > Agregar una condición con cantidad de atributo (seleccione en stock/sin existencias).
1. Compruebe los productos en la parte delantera.

<u>Resultados esperados</u>:

El producto en existencia/sin existencias coincide con *[!UICONTROL Related Product Rules]*.

<u>Resultados reales</u>:

El producto en existencia/sin existencias no coincide con *[!UICONTROL Related Product Rules]*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
