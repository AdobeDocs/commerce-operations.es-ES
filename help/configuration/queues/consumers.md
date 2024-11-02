---
title: Consumidores de cola de mensajes
description: Obtenga información acerca de los consumidores de colas de mensajes de Adobe Commerce, incluidas las funciones y las opciones de configuración del sistema asociadas a ellos.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---

# Consumidores de cola de mensajes

La siguiente tabla identifica a todos los consumidores de colas de mensajes, describe lo que hacen e identifica las opciones de configuración del sistema de administración asociadas a ellos:

| Consumidor y descripción | Adobe Commerce | Adobe Commerce con B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Crea mensajes para cada tarea individual de una [operación masiva](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), como importar o exportar artículos, cambiar precios a escala masiva y asignar productos a un almacén. Necesario cuando la opción [**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) está establecida en **[!UICONTROL Run asynchronously]**en las opciones de configuración del sistema de administración. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Genera cupones de forma asíncrona en segundo plano. Necesario para utilizar la característica [generación de cupones por lotes](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons). |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Comprueba eventos que se han registrado como prioritarios en [Eventos de Adobe I/O para Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Evita tiempos de espera de conexión durante la [exportación](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) de grandes conjuntos de datos (por ejemplo, 200 000 productos). |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Corrige de forma asíncrona el índice de existencias después de realizar un pedido o de eliminar un producto. Necesario cuando la opción [**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#product-stock-options) está habilitada en las opciones de configuración de administración. Consulte [Prácticas recomendadas de rendimiento](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Elimina de forma asíncrona los elementos de origen por SKU de producto cuando se elimina un producto. Necesario cuando la opción de existencias [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) está habilitada en las opciones de configuración del sistema de administración. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Procesa de forma asíncrona elementos de stock heredados, actualiza elementos de stock heredados, actualiza elementos de origen predeterminados y reindexa el inventario para SKU de producto específicas. Necesario cuando la operación masiva [**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) está habilitada en las opciones de configuración del sistema de administración. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Elimina de forma asíncrona las reservas por SKU de producto después de eliminar un producto. Necesario cuando la opción de existencias [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) está habilitada en las opciones de configuración del sistema de administración. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Actualiza de forma asíncrona las reservas por SKU del producto después de eliminar un producto. Necesario cuando la opción de existencias [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) está habilitada en las opciones de configuración del sistema de administración. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Actualiza de forma asíncrona la cantidad vendible de cada producto asignado a un stock. Este consumidor siempre debe estar en funcionamiento si está usando [!DNL Inventory Management]. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Reindexa los elementos de origen de forma asíncrona. Necesario cuando [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) está establecido en &quot;[!UICONTROL asynchronous]&quot; en la configuración del sistema de administración. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Reindexa las existencias de forma asíncrona. Necesario cuando [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) está establecido en &quot;[!UICONTROL asynchronous]&quot; en la configuración del sistema de administración. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Crea una tabla de base de datos temporal, mueve cada [segmento de cliente](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments) a ella, elimina todos los segmentos que coinciden con el ID de segmento y los copia en los segmentos del cliente utilizando el ID de segmento como indicador. Todo esto se realiza en una transacción para que, si algo falla, se revierta la transacción a lo que era antes de ejecutarla. Después de una transacción, el consumidor cierra la tabla temporal. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Garantiza que los vínculos a los medios asignados para productos, categorías, bloques de CMS y páginas de CMS se asignen correctamente al recurso. Elimina los recursos antiguos que ya no se utilizan. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Genera y valida rutas de recursos de medios. La ruta absoluta a un recurso viene determinada por su ubicación en el servidor desde el directorio multimedia. Se cambia el tamaño de las imágenes (si es necesario) y se copian en el directorio de medios dentro de la ruta generada. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Importa archivos de imagen a la tabla de base de datos `media_gallery_asset`. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| [cambia el tamaño de las imágenes del catálogo](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) de forma asincrónica. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Actualiza los precios de las ofertas negociables. Necesario cuando la opción [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) está habilitada en las opciones de configuración del sistema de administración. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| [procesa de forma asíncrona pedidos](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), que marcan los pedidos como recibidos, los coloca en la cola de mensajes y los procesa en orden de entrada y de salida. Se considera una [práctica recomendada](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) para mejorar el número de pedidos que se pueden procesar porque los clientes no necesitan esperar a que se completen los procesos back-end antes de ver un mensaje de éxito. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| Escribe de forma asíncrona cambios en los atributos del producto en la base de datos después de usar el administrador para [realizar actualizaciones](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| Escribe de forma asíncrona cambios en los atributos de producto para una vista de almacén específica en la base de datos después de usar el administrador para [realizar actualizaciones](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_alert` | + | + | + |
| Envía correos electrónicos de notificación a los clientes sobre los cambios en el precio del producto y en el inventario. Necesario cuando la opción Necesario cuando la opción [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) está habilitada en las opciones de configuración del sistema de administración. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Convierte el pedido de compra en [pedido](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules). Necesario cuando la opción [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está habilitada en las opciones de configuración del sistema de administración. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Envía correos electrónicos de pedidos de compra. Necesario cuando la opción [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está habilitada en las opciones de configuración del sistema de administración. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Valida el pedido de compra con [reglas de aprobación](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules) relevantes. Necesario cuando la opción [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está habilitada en las opciones de configuración del sistema de administración. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| Guarda asincrónicamente los cambios de configuración del almacén colocando los trabajos de guardado en una cola de mensajes, lo que puede mejorar el rendimiento en implementaciones que contienen un gran número de configuraciones de nivel de almacén. Requerido para usar el módulo [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save). |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Evita el [problema](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) en el que los cupones de un solo uso se pueden usar varias veces. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Actualiza las categorías asignadas a una categoría de catálogo compartido. Necesario cuando la opción [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) está habilitada en las opciones de configuración del sistema de administración. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Actualiza el precio de cada producto en un catálogo compartido. Necesario cuando la opción [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) está habilitada en las opciones de configuración del sistema de administración. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Elimina las ofertas de precios no válidas o inactivas cuando un producto se elimina del catálogo o del carro de compras. Necesario cuando la opción [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) está habilitada en las opciones de configuración del sistema de administración. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Actualiza los carros de compras activos para reflejar los cambios en la regla de precios del carro de compras. Requerido al actualizar [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
