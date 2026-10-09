---
title: 'ACSD-66049: Las tiendas que no están en inglés muestran precios incorrectos debido a la versión de la biblioteca de la UCI'
description: Aplique el parche ACSD-66049 para corregir el problema de Adobe Commerce donde las tiendas que no están en inglés muestran precios incorrectos debido a la discrepancia de versiones de la biblioteca de la ICU en entornos PHP más antiguos (versiones 63.1 a 74.1).
feature: Products
role: Admin, Developer
type: Troubleshooting
exl-id: e667d462-87f6-4db5-bf3f-3213edac2f09
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '364'
ht-degree: 0%
---
# ACSD-66049: Las tiendas que no están en inglés muestran precios incorrectos debido a la versión de la biblioteca de la UCI

El parche ACSD-66049 soluciona el problema de las tiendas que no están en inglés y muestran precios incorrectos debido a la discrepancia de versiones de la biblioteca ICU en entornos PHP más antiguos (versiones 63.1 a 74.1). Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. El ID del parche es ACSD-66049. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p3 - 2.4.5-p13, 2.4.7 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las tiendas que no están en inglés muestran precios incorrectos cuando se usan versiones más antiguas de la biblioteca PHP ICU (63.1 a 74.1).

<u>Pasos a seguir</u>:

1. Compruebe la versión de ICU:
   * Conéctese al servidor mediante SSH y ejecute el comando: `php -a`
   * En el mensaje, escriba: `echo INTL_ICU_VERSION;`
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale]** > **[!UICONTROL Locale Options]**. **[!UICONTROL Configure Locale]** = *[!UICONTROL Hebrew (Israel)]*.
1. Cree un producto con precio = 100.
1. Ver la página del producto en la tienda.

<u>Resultados esperados</u>:

El precio mostrado no es 0.

<u>Resultados reales</u>:

Después de aparecer brevemente como 100, el precio se actualiza inmediatamente a 0.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
