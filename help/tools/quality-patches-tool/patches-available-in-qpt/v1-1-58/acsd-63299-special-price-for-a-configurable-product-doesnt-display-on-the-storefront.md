---
title: 'ACSD-63299: El precio especial de un producto configurable no se muestra en la tienda'
description: Aplique el parche ACSD-63299 para solucionar el problema de Adobe Commerce en el que el atributo de precio especial ya no afecta a la visualización de precios especiales para productos configurables.
feature: Catalog Management
Role: Admin, Developer
source-git-commit: 238d3fa6d7729f729aeb79c98ae28db331ad7509
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-63299: El precio especial de un producto configurable no se muestra en la tienda

El parche ACSD-63299 corrige el problema en el que el atributo de precio especial ya no afecta a la visualización de precios especiales para productos configurables. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. El ID del parche es ACSD-63299. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

En [!DNL Adobe Commerce], cambiar el valor *Utilizado en la lista de productos* para el atributo de precio especial ya no afecta a la forma en que se muestran los precios especiales para los productos configurables.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Products]**.
1. Busque el atributo ***[!UICONTROL special_price]*** y vaya a **[!UICONTROL Storefront Properties]**.
1. Cambie ***[!UICONTROL Used in Product Listing]*** a ***[!UICONTROL No]***.
1. Cree un producto configurable con un elemento secundario:
   * Nombre y SKU: prueba
   * Precio: 159,00 $
   * Generar opción basada en el color. Añadir un nuevo color: Azul
   * Guardar
1. Abra el producto secundario y siga estos pasos:
   * Establece un precio especial de $99.90 en **[!UICONTROL Advanced Pricing]**
   * Cambiar [!UICONTROL Visibility] a **[!UICONTROL Catalog, Search]**.
1. Abra la página de producto simple y confirme que el precio especial está visible.
1. Abra la página de producto configurable.
1. Seleccione el producto azul.

<u>Resultados esperados</u>:

Precio especial es visible de la misma manera que lo es para el producto simple.

<u>Resultados reales</u>:

1. El precio completo se muestra cuando se selecciona un producto configurable.
1. Hay un desajuste entre las secciones *Tan bajo como...* ($99.90) y el precio real ($99.90 + $59.10 = $159.00).

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
