---
title: "ACSD-54319: el precio del producto muestra cero en el informe *[!UICONTROL Products in Carts]*"
description: Aplique el parche ACSD-54319 para corregir el problema de Adobe Commerce donde el precio del producto muestra cero en el informe *[!UICONTROL Products in Carts]*
feature: Reporting, Products
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# ACSD-54319: el precio del producto muestra cero en el informe *[!UICONTROL Products in Carts]*

La revisión ACSD-54319 corrige el problema en el cual el precio del producto muestra cero en el informe *[!UICONTROL Products in Carts]*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.40. El ID del parche es ACSD-54319. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.5-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El precio del producto muestra cero en el informe *[!UICONTROL Products in Carts]*.

<u>Pasos a seguir</u>:

1. Establezca **[!UICONTROL Catalog Price Scope]** en **[!UICONTROL Website]** desde **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]**.
1. Crear un segundo sitio web desde **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Crear un producto a partir de **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Asigne este producto únicamente al segundo sitio web.
1. Añada un producto al carro de compras desde el segundo sitio web.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Marketing]** > **[!UICONTROL Products In Carts]** cuadrícula.
1. Compruebe la columna *[!UICONTROL Price]* en la cuadrícula *[!UICONTROL Products In Carts]*.

<u>Resultados esperados</u>:

El precio del producto no es cero en la cuadrícula del informe *[!UICONTROL Products in Carts]*.

<u>Resultados reales</u>:

El precio del producto es cero en la cuadrícula del informe *[!UICONTROL Products in Carts]*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
