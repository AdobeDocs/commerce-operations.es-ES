---
title: "ACSD-47704: El producto agrupado muestra el precio de solo productos en stock"
description: Aplique el parche ACSD-47704 para corregir el problema de Adobe Commerce en el que un producto agrupado muestra solo el precio de los productos en stock.
feature: Admin Workspace, Customer Service, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# ACSD-47704: el producto agrupado muestra solo el precio de los productos en stock

El parche ACSD-47704 corrige el problema de que los precios de los segmentos de los clientes se almacenan incorrectamente en caché entre grupos de clientes. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28. El ID del parche es ACSD-47704. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El precio de un producto agrupado con la asignación de precios dinámica activada es incorrecto debido a que solo se incluyen los artículos en stock.

<u>Pasos a seguir</u>:

1. Vaya al panel de administración de Commerce.
1. Vaya a **[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]**.
1. Establezca **[!UICONTROL Dynamic Price]** en **[!UICONTROL Yes]**.
1. Elementos de paquete:
   * Establecer **[!UICONTROL Ship bundle items]** en **[!UICONTROL Together]**
   * Seleccionar **[!UICONTROL Add Option]**
      * **[!UICONTROL Title]** = o1
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Marcar casilla de verificación requerida
      * Añada cualquier producto sencillo que esté en stock; por ejemplo, Bolsa de lona Joust SKU 24-MB01. Antes de añadir el producto, anota su precio: $34
   * Cantidad predeterminada: 1
   * Seleccionar **[!UICONTROL Add Option]**
      * **[!UICONTROL Option Title]** = o2
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Marcar casilla de verificación requerida
      * Añada cualquier producto simple que esté en stock, diferente del producto añadido en el paso anterior; por ejemplo: Strive Shoulder Pack 24-MB04. Antes de añadir el producto, anota su precio: $32
      * Cantidad predeterminada: 1
1. Guardar producto.
1. Vaya a la tienda y busque el producto creado en los pasos anteriores. Anote su precio: 66 dólares
(66 = 32 + 34).
Actualmente, el precio del producto del paquete es igual a la suma de los precios de sus opciones.
1. Vaya al panel de administración de Commerce. Ir a **[!UICONTROL CATALOG]** > **[!UICONTROL Products]**.
1. Busque uno de los productos simples asignados como opción al producto del paquete anteriormente:
SKU 24-MB01 y precio de 34 $.
1. Cambie su cantidad a 0.
1. Guarde el producto.
1. Vaya a la tienda y busque el producto del paquete creado en los pasos anteriores. Note abajo su precio - $32. Anteriormente tenía un precio de 66 $, lo que equivalía a la suma de 34 $ del SKU 24-MB01 y 32 $ del SKU 24-MB04. Ahora que el producto 24-MB01 está agotado, el precio del paquete aparece como $32. Es el precio del otro producto, que es una opción en stock.

<u>Resultados esperados</u>:

El precio de los productos agrupados con precios dinámicos activados se calcula de forma coherente, independientemente de si las opciones están en stock o agotadas.

<u>Resultados reales</u>:

Se ha calculado mal el precio del paquete de productos con la asignación de precios dinámica habilitada. Solo tiene en cuenta las opciones que están en stock, lo que da como resultado una cantidad mostrada menor que la real cuando una de las opciones está sin existencias.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
