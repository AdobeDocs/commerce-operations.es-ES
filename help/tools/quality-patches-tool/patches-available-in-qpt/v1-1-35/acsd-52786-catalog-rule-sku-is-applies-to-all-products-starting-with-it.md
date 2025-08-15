---
title: 'ACSD-52786: la regla de catálogo *[!UICONTROL SKU is]* se aplica a todos los productos que comienzan con el SKU'
description: Aplique el parche ACSD-52786 para corregir el problema de Adobe Commerce en el que la condición de regla de catálogo *[!UICONTROL SKU is]* se aplica a todos los productos que comienzan con el SKU determinado.
feature: Price Rules
role: Admin
exl-id: 668d5f16-18a9-4054-aa6e-1fb8fa211373
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52786: La regla de catálogo &quot;*[!UICONTROL SKU is]*&quot; se aplica a todos los productos que comienzan con el SKU

El parche ACSD-52786 corrige el problema en el que la condición de regla de catálogo *[!UICONTROL SKU is]* se aplica a todos los productos que comienzan con el SKU determinado. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.35. El ID del parche es ACSD-52786. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La condición de regla de catálogo *[!UICONTROL SKU is]* se aplica a todos los productos que comienzan con el SKU determinado.

<u>Pasos a seguir</u>:

1. Cree dos productos, uno con el SKU &quot;24&quot; y otro con el SKU &quot;24-MB01&quot;.
1. Vaya a **[!UICONTROL Marketing]** > **[!UICONTROL Catalog Price Rule]** > **[!UICONTROL Add New Rule]**.
1. Aplique la siguiente condición:
   * *[!UICONTROL If **&#x200B; TODAS &#x200B;** de estas condiciones son **&#x200B; VERDADERAS &#x200B;**]*: *[!UICONTROL SKU is 24]*
1. Defina cualquier importe de descuento en las acciones.
1. Haga clic en **[!UICONTROL Save and Apply]**.
1. Vaciar caché.
1. Vaya a la tienda y compruebe el precio de 24 MB01.

<u>Resultados esperados</u>:

La regla de catálogo solo se aplica a un único producto con SKU igual a 24.

<u>Resultados reales</u>:

La condición de regla de catálogo *[!UICONTROL SKU is]* se aplica a todos los productos que comienzan con el SKU determinado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
