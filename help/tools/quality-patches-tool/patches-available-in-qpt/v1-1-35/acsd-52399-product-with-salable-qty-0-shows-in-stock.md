---
title: 'ACSD-52399: Producto con cantidad salable 0 muestra en stock'
description: Aplique el parche ACSD-52399 para solucionar el problema de Adobe Commerce donde la opción de producto configurable con una cantidad escalable de 0 muestra *En stock* en la página del producto.
feature: Products, Configuration
role: Admin, Developer
exl-id: 7b7332bb-15ae-44b6-a347-38ac7c9001db
source-git-commit: f6abbbb28a3077f7bf26a393388c5059fcd8c599
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-52399: Producto con cantidad salable 0 muestra en stock

El parche ACSD-52399 corrige el problema en el que la opción de producto configurable con una cantidad comercializable de cero (0) muestra *En existencia* en la página de producto. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.35. El ID del parche es ACSD-52399. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La opción de producto configurable con una cantidad vendible de cero (0) muestra *En existencia* en la página del producto.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con la opción de producto de cantidad vendible cero (0).
1. Vaya a la página del producto en la tienda y seleccione el producto configurable para comprobar una variación o configuración.
1. Seleccione **[!UICONTROL Add to Cart]**.

<u>Resultados esperados</u>:

El botón *[!UICONTROL Add to Cart]* no está disponible al seleccionar la configuración del producto *Agotado*.

<u>Resultados reales</u>:

Las variaciones configurables están disponibles en la tienda y puede seleccionarlas y agregarlas al carro de compras.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
