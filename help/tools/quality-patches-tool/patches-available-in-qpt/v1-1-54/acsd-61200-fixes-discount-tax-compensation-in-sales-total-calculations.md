---
title: 'ACSD-61200: corrige la compensación de impuestos de descuento en los cálculos totales de ventas'
description: Aplique el parche ACSD-61200 para corregir el problema de Adobe Commerce en el que faltan *[!UICONTROL Discount Tax Compensation Amount]* y *[!UICONTROL Shipping Discount Tax Compensation Amount]* en los cálculos de totales de ventas, lo que provoca discrepancias entre los datos de pedidos de ventas y los datos del informe de cupones.
feature: Reporting, Taxes
role: Admin, Developer
exl-id: eb908827-de29-4b2c-b094-b5db0931cd52
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: f42e0a1a-0d79-488d-a83f-f2c30672b137
    internal-label: Reporting
  - id: 42e094d8-211b-5acf-b52f-d8979151ab30
    internal-label: Taxes
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 13%
---
# ACSD-61200: corrige la compensación de impuestos de descuento en los cálculos totales de ventas

La revisión ACSD-61200 corrige el problema en el que *[!UICONTROL Discount Tax Compensation Amount]* y *[!UICONTROL Shipping Discount Tax Compensation Amount]* no aparecen en los cálculos *[!UICONTROL Total Amount]* y *[!UICONTROL Total Amount Actual]*, lo que da como resultado discrepancias entre los datos de los pedidos de ventas y los datos del informe de cupones. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. El ID del parche es ACSD-61200. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.8 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

- Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

- Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Imprecisiones en los datos del informe de cupones y pedidos de ventas debido a que faltan *[!UICONTROL Discount Tax Compensation Amount]* y *[!UICONTROL Shipping Discount Tax Compensation Amount]* en los cálculos de totales de ventas.

<u>Pasos a seguir</u>:

1. Crear un [!UICONTROL Tax Zone] y un [!UICONTROL Tax Rule].
1. Defina las siguientes configuraciones de impuestos:
   - **[!UICONTROL Tax Class for Shipping]** = [!UICONTROL Taxable Goods]
   - **[!UICONTROL Catalog Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Shipping Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Apply Discount on Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Product Prices in Catalog]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Prices]** = [!UICONTROL Including Tax]
1. Actualice la siguiente configuración de visualización para pedidos, facturas y notas de abono:
   - **[!UICONTROL Display Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Subtotal]**= [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Amount]** = [!UICONTROL Including Tax]
1. Crea un [!UICONTROL Cart Price Rule] con un cupón para obtener un descuento del 10%.
1. Complete un pedido con el cupón y genere una factura y un envío.
1. Vaya a **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Coupons]** y genere un informe.
1. Compare los datos del resumen del pedido con los del informe.

<u>Resultados esperados</u>:

Los cálculos *[!UICONTROL Total Amount]* y *[!UICONTROL Total Amount Actual]* incluyen *[!UICONTROL Discount Tax Compensation Amount]* y *[!UICONTROL Shipping Discount Tax Compensation Amount]*, lo que hace coincidir el resumen del pedido con los datos del informe.

<u>Resultados reales</u>:

Los datos del pedido de ventas y del informe de cupones no coinciden porque *[!UICONTROL Discount Tax Compensation Amount]* y *[!UICONTROL Shipping Discount Tax Compensation Amount]* no aparecen en los cálculos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

- Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
- Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

[[!DNL Quality Patches Tool] publicado: una nueva herramienta para aplicar parches de calidad de autoservicio](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
