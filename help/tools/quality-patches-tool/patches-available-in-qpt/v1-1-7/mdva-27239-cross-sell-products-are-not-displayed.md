---
title: 'MDVA-27239: No se muestran los productos de venta cruzada'
description: El parche MDVA-27239 soluciona el problema de que no se muestran los productos de venta cruzada. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.6.
feature: Products
role: Admin
exl-id: ab8fe64d-adbe-4756-be43-1a35ba6b4123
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-27239: No se muestran los productos de venta cruzada

El parche MDVA-27239 soluciona el problema de que no se muestran los productos de venta cruzada. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.4, 2.4.0

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.3.5-p2, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos de venta cruzada no se muestran en el bloque de venta cruzada de la página del carro de compras.

<u>Requisitos previos</u>:

1. Deshabilite el módulo Magento_TargetRule o elimínelo del bloque de diseño Magento\TargetRule\Block\Checkout\Cart\Crosssell.
1. Crear producto 1.
1. Cree una actualización de programación para el producto 1, de modo que los productos recién creados tengan un row_id diferente de entity_id.
1. Cree Product 2, Product 3 y Product 4.
1. Establezca el Producto 3 como venta cruzada para el Producto 4.
1. Establezca el Producto 4 como venta cruzada para el Producto 2.

<u>Pasos a seguir</u>:

1. Agregue los productos Product 4 y Product 2 al carro de compras.
1. Consulte la página del carro de compras.

<u>Resultados esperados</u>:

El producto 3 se muestra en el bloque de venta cruzada.

<u>Resultados reales</u>:

El bloque de venta cruzada está vacío.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
