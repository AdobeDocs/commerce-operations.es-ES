---
title: Consumidores de cola de mensajes
description: Obtenga información acerca de los consumidores de colas de mensajes de Adobe Commerce y Magento Open Source, incluidas las funciones y las opciones de configuración del sistema asociadas a ellos.
source-git-commit: 1006a5761849b1d455469c6dfcb79a66cb90ec40
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 0%

---


# Consumidores de cola de mensajes

La siguiente tabla identifica a todos los consumidores de colas de mensajes, describe lo que hacen e identifica las opciones de configuración del sistema de administración asociadas a ellos:

| Consumidor y descripción | Adobe Commerce | Adobe Commerce con B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Crea mensajes para cada tarea individual de un [operación en masa](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), como importar o exportar artículos, cambiar los precios a escala masiva y asignar productos a un almacén. Necesario cuando el [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) se establece en **[!UICONTROL Run asynchronously]**en los ajustes de configuración del sistema de administración. |  |  |  |
| `codegeneratorProcessor` | + | + | + |
| Genera cupones de forma asíncrona en segundo plano. Necesario para utilizar [generación de cupones por lotes](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) función. |  |  |  |
| `exportProcessor` | + | + | + |
| Evita los tiempos de espera de conexión durante [exportar](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) de grandes conjuntos de datos (por ejemplo, 200 000 productos). |  |  |  |
| `inventoryQtyCounter` | + | + |  |
| Corrige de forma asíncrona el índice de existencias después de realizar un pedido o de eliminar un producto. Necesario cuando el [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) está activada en las opciones de configuración de administración. Consulte [Prácticas recomendadas de rendimiento](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |  |  |  |
| `inventory.source.items.cleanup` | + | + | + |
| Elimina de forma asíncrona los elementos de origen por SKU de producto cuando se elimina un producto. Necesario cuando el [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) La opción de stock está activada en las opciones de configuración del sistema de administración. |  |  |  |
| `inventory.mass.update` | + | + | + |
| Procesa de forma asíncrona elementos de stock heredados, actualiza elementos de stock heredados, actualiza elementos de origen predeterminados y reindexa el inventario para SKU de producto específicas. Necesario cuando el [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) la operación masiva está habilitada en las opciones de configuración del sistema de administración. |  |  |  |
| `inventory.reservations.cleanup` | + | + | + |
| Elimina de forma asíncrona las reservas por SKU de producto después de eliminar un producto. Necesario cuando el [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) La opción de stock está activada en las opciones de configuración del sistema de administración. |  |  |  |
| `inventory.reservations.update` | + | + | + |
| Actualiza de forma asíncrona las reservas por SKU del producto después de eliminar un producto. Necesario cuando el [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) La opción de stock está activada en las opciones de configuración del sistema de administración. |  |  |  |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Actualiza de forma asíncrona la cantidad vendible de cada producto asignado a un stock. Este consumidor siempre debe estar en funcionamiento si está utilizando [!DNL Inventory Management]. |  |  |  |
| `inventory.indexer.sourceItem` | + | + | + |
| Reindexa los elementos de origen de forma asíncrona. Necesario cuando el [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) se configura como &quot;[!UICONTROL asynchronous]&quot; en los ajustes de configuración del sistema de administración. |  |  |  |
| `inventory.indexer.stock` | + | + | + |
| Reindexa las existencias de forma asíncrona. Necesario cuando el [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) se configura como &quot;[!UICONTROL asynchronous]&quot; en los ajustes de configuración del sistema de administración. |  |  |  |
| `matchCustomerSegmentProcessor` | + | + |  |
| Crea una tabla de base de datos temporal, mueve cada una [segmento de cliente](https://docs.magento.com/user-guide/marketing/customer-segments.html) En él, elimina todos los segmentos que coinciden con el ID de segmento y los copia en los segmentos del cliente utilizando el ID de segmento como indicador. Todo esto se realiza en una transacción para que, si algo falla, se revierta la transacción a lo que era antes de ejecutarla. Después de una transacción, el consumidor cierra la tabla temporal. |  |  |  |
| `media.content.synchronization` | + | + | + |
| Garantiza que los vínculos a los medios asignados para productos, categorías, bloques de CMS y páginas de CMS se asignen correctamente al recurso. Elimina los recursos antiguos que ya no se utilizan. |  |  |  |
| `media.gallery.renditions.update` | + | + | + |
| Genera y valida rutas de recursos de medios. La ruta absoluta a un recurso viene determinada por su ubicación en el servidor desde el directorio multimedia. Se cambia el tamaño de las imágenes (si es necesario) y se copian en el directorio de medios dentro de la ruta generada. |  |  |  |
| `media.gallery.synchronization` | + | + | + |
| Importa archivos de imagen a `media_gallery_asset` tabla de base de datos. |  |  |  |
| `media.storage.catalog.image.resize` | + | + | + |
| Asíncronamente [redimensiona](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) imágenes de catálogo. |  |  |  |
| `negotiableQuotePriceUpdate` |  | + |  |
| Actualiza los precios de las ofertas negociables. Necesario cuando el [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) está activada en las opciones de configuración del sistema de administración. |  |  |  |
| `placeOrderProcessor` | + | + |  |
| Asíncronamente [procesa pedidos](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), que marca los pedidos como recibidos, los coloca en la cola de mensajes y los procesa en orden de llegada. Se considera un [práctica recomendada](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) para mejorar el número de pedidos que se pueden procesar porque los clientes no necesitan esperar a que se completen los procesos backend antes de ver un mensaje de éxito. |  |  |  |
| `product_action_attribute.update` | + | + | + |
| Escribe de forma asíncrona cambios en los atributos del producto en la base de datos después de usar el administrador para [realizar actualizaciones](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_action_attribute.website.update` | + | + | + |
| Escribe de forma asíncrona cambios en los atributos de producto para una vista de almacén específica en la base de datos después de usar el administrador para lo siguiente [realizar actualizaciones](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_alert` | + | + | + |
| Envía correos electrónicos de notificación a los clientes sobre los cambios en el precio del producto y en el inventario. Obligatorio cuando el valor de Requerido cuando [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) está activada en las opciones de configuración del sistema de administración. |  |  |  |
| `purchaseorder.toorder` |  | + |  |
| Convierte el pedido de compra en [pedido](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). Necesario cuando el [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está activada en las opciones de configuración del sistema de administración. |  |  |  |
| `purchaseorder.transactional.email` |  | + |  |
| Envía correos electrónicos de pedidos de compra. Necesario cuando el [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está activada en las opciones de configuración del sistema de administración. |  |  |  |
| `purchaseorder.validation` |  | + |  |
| Valida el pedido de compra con los datos relevantes [reglas de aprobación](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). Necesario cuando el [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está activada en las opciones de configuración del sistema de administración. |  |  |  |
| `sales.rule.update.coupon.usage` | + | + | + |
| Evita la [problema](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) donde los cupones de un solo uso pueden utilizarse varias veces. |  |  |  |
| `sharedCatalogUpdateCategoryPermissions` |  | + |  |
| Actualiza las categorías asignadas a una categoría de catálogo compartido. Necesario cuando el [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) está activada en las opciones de configuración del sistema de administración. |  |  |  |
| `sharedCatalogUpdatePrice` |  | + |  |
| Actualiza el precio de cada producto en un catálogo compartido. Necesario cuando el [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) está activada en las opciones de configuración del sistema de administración. |  |  |  |
| `quoteItemCleaner` | + | + |  |
| Elimina las ofertas de precios no válidas o inactivas cuando un producto se elimina del catálogo o del carro de compras. Necesario cuando el [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) está activada en las opciones de configuración del sistema de administración. |  |  |  |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Actualiza los carros de compras activos para reflejar los cambios en la regla de precios del carro de compras. Necesario al actualizar [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |  |  |  |

{style="table-layout:auto"}
