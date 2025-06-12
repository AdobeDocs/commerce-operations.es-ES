---
title: 'MDVA-40399: Las facturas parciales para el mismo pedido no se pueden crear simultáneamente mediante API'
description: El parche MDVA-40399 corrige el problema en el que las facturas parciales del mismo pedido no se pueden crear simultáneamente mediante la API de REST. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4. El ID del parche es MDVA-40399. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: REST, Invoices, Orders
role: Admin
exl-id: aa400a15-57b9-4f80-a49f-f4680b7e4705
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-40399: Las facturas parciales para el mismo pedido no se pueden crear simultáneamente mediante API

El parche MDVA-40399 corrige el problema en el que las facturas parciales del mismo pedido no se pueden crear simultáneamente mediante la API de REST. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4. El ID del parche es MDVA-40399. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se pueden crear simultáneamente facturas parciales para los mismos pedidos mediante la API de REST.

<u>Requisitos previos</u>:

Un producto configurable con al menos dos variaciones.

<u>Pasos a seguir</u>:

1. Añada ambas variantes del producto configurable al carro de compras.
1. Realice el pedido.
1. Cree dos facturas simultáneamente para el pedido a través de la API REST.

<u>Resultados esperados</u>:

* Ambas facturas deben crearse correctamente.
* `qty_invoiced` debe actualizarse para ambas facturas en la tabla `sales_order_item`.
* Ambos productos deberían tener una cantidad facturada.

<u>Resultados reales</u>:

* Ambas facturas se han creado correctamente.
* `qty_invoiced` no se ha actualizado con una de las facturas de la tabla `sales_order_item`.
* En la página **Vista de pedidos** del administrador, la cantidad de facturas solo se muestra para un producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
