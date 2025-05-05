---
title: '"ACSD-53176: La regla de producto con "es una de" condición no coincide"'
description: Aplique el parche ACSD-53176 para solucionar el problema de Adobe Commerce donde la regla de producto relacionada &grave;is one of&grave; no funciona correctamente para "Productos que coinciden".
feature: Marketing Tools
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-53176: La regla de producto con la condición `is one of` no coincide

El parche ACSD-53176 corrige el problema en el que la condición de regla de producto `is one of` relacionada no funciona correctamente para **Productos que coinciden**. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.36. El ID del parche es ACSD-53176. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La condición de regla de producto `is one of` relacionada no funciona correctamente para que **Productos coincidan**.

<u>Pasos a seguir</u>:

1. Cree de 3 a 4 productos.
1. Cree una nueva regla de producto relacionada.

   Configure la regla para que coincida con dos o más productos:
   * `SKU is one of "S1,S2".`

   Configure la regla para que muestre dos o más elementos:
   * `Product SKU is one of constant value "S2,S3".`

1. Abra el producto S1 en la Tienda.

<u>Resultados esperados</u>:

Los productos relacionados &quot;S2&quot; y &quot;S3&quot; se muestran en las páginas de productos &quot;S1&quot; y &quot;S2&quot;.

<u>Resultados reales</u>:

Los productos relacionados no se muestran en las páginas de productos de.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
