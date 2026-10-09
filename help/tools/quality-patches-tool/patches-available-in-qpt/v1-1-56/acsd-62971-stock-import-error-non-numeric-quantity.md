---
title: 'ACSD-62971: la importación de orígenes de stock con valores de cantidad no numéricos da como resultado que la cantidad se establezca en 0'
description: Aplique el parche ACSD-62971 para solucionar el problema de Adobe Commerce en el que la importación de orígenes de stock con valores no numéricos en la columna "cantidad" provoca que la cantidad se establezca en 0.
feature: Data Import/Export, Inventory
role: Admin, Developer
exl-id: ece23153-4932-4ac5-b46e-49327a8e84a1
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
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
source-wordcount: '363'
ht-degree: 0%
---
# ACSD-62971: la importación de orígenes de stock con valores de cantidad no numéricos da como resultado que la cantidad se establezca en 0

El parche ACSD-62971 corrige el problema en el que la importación de orígenes de stock con valores no numéricos en la columna &quot;cantidad&quot; da como resultado que la cantidad se establezca en 0. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. El ID del parche es ACSD-62971. Tenga en cuenta que el problema estaba programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Corrige el problema en el cual la importación de orígenes de stock con valores no numéricos en la columna **[!UICONTROL Quantity]** da como resultado que la cantidad se establezca en 0.

<u>Pasos a seguir</u>:

1. Crear **[!UICONTROL Simple Product]** con cantidad=100
1. Realice una importación de **[!UICONTROL Stock Sources]** utilizando el archivo que tiene una cantidad incorrecta (&quot;abc&quot;)

   ```table
   source_code    sku    status    quantity
     default     simple    1         abc
   ```

1. Compruebe la cantidad después de la importación.

<u>Resultados esperados</u>:
La validación de los datos de importación debe fallar.

<u>Resultados reales</u>:
La cantidad de producto simple se ha convertido en 0 y el producto se ha actualizado como [!UICONTROL Out of Stock].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
