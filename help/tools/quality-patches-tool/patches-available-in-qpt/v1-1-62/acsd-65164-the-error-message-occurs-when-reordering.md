---
title: 'ACSD-65164: Mensaje de error al reordenar el producto configurable con una sola opción personalizada de casilla de verificación seleccionada'
description: Aplique el parche ACSD-65164 para solucionar el problema de Adobe Commerce donde aparece el mensaje de error *Algunas de las opciones del elemento seleccionado no están disponibles actualmente* al reordenar un producto configurable con una sola opción personalizada de casilla de verificación seleccionada.
feature: Products, Orders
role: Admin, Developer
exl-id: 22b72d24-4852-45ba-ac98-df9565f94539
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-65164: Mensaje de error al reordenar el producto configurable con una sola opción personalizada de casilla de verificación seleccionada

El parche ACSD-65164 corrige el problema en el que el mensaje de error *Algunas de las opciones del elemento seleccionado no están disponibles actualmente* se produce al reordenar un producto configurable con una única opción personalizada de casilla de verificación seleccionada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62. El ID del parche es ACSD-65164. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al reordenar un producto configurable con una única opción personalizada de casilla de verificación seleccionada, el sistema devuelve un mensaje de error: *Algunas de las opciones de elementos seleccionadas no están disponibles en este momento*.

### Pasos para replicar:

1. En el panel de administración, vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Simple Product]**.
1. En **[!UICONTROL Customizable Options]**, agregue una opción *Casilla de verificación*.
   * Establezca la opción de casilla de verificación como *Requerido*.
   * Agregue dos valores de opción.
1. Vaya a la Tienda e inicie sesión como cliente registrado.
1. Añadir el producto al carro de compras con una opción de casilla de verificación seleccionada.
1. Vaya a **[!UICONTROL Cart]** > **[!UICONTROL Proceed to Checkout]** > **[!UICONTROL Place an Order]**.
1. Vaya a **[!UICONTROL My Account]** > **[!UICONTROL Orders]** > **[!UICONTROL Reorder]** para agregar el mismo producto.

**Resultados esperados:**

El producto debe añadirse correctamente al carro de compras.

**Resultados reales:**

Se muestra un mensaje de error:

*No se pudo agregar el producto con SKU &quot;24-MB01&quot; al carro de compras: algunas de las opciones del elemento seleccionado no están disponibles en este momento.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
