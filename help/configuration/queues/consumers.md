---
title: Clientes de cola de mensajes
description: Obtenga información sobre los consumidores de cola de mensajes de Adobe Commerce y Magento Open Source, incluidas las funciones y los ajustes de configuración del sistema asociados a ellos.
source-git-commit: 2eecaab32b090cfd3c1a8e8832027d3531cf0edc
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 0%

---


# Clientes de cola de mensajes

La siguiente tabla identifica a todos los consumidores de cola de mensajes, describe lo que hacen e identifica los ajustes de configuración del sistema de administración asociados a ellos:

| Consumidor y descripción | Adobe Commerce | Adobe Commerce con B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Crea mensajes para cada tarea individual de una [operación masiva](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), como importar o exportar artículos, cambiar precios a escala masiva y asignar productos a un almacén. Necesario cuando la variable [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) está configurada en **[!UICONTROL Run asynchronously]**en los ajustes de configuración del sistema de administración. |  |  |  |
| `codegeneratorProcessor` | + | + | + |
| Genera cupones de forma asíncrona en segundo plano. Necesario para usar la variable [generación de cupones por lotes](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) función. |  |  |  |
| `exportProcessor` | + | + | + |
| Evita que se agote el tiempo de espera de la conexión durante el [exportar](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) de grandes conjuntos de datos (por ejemplo, 200 000 productos). |  |  |  |
| `inventoryQtyCounter` | + | + |  |
| Corrige asincrónicamente el índice de existencias después de realizar un pedido o de eliminar un producto. Necesario cuando la variable [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) está activada en la configuración de administración. Consulte [Prácticas recomendadas de rendimiento](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |  |  |  |
| `inventory.source.items.cleanup` | + | + | + |
| Elimina asincrónicamente los elementos de origen por SKU de producto cuando se elimina un producto. Necesario cuando la variable [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) la opción stock está activada en los ajustes de configuración del sistema de administración. |  |  |  |
| `inventory.mass.update` | + | + | + |
| Procesa asincrónicamente los elementos de existencias heredados, actualiza los elementos de existencias heredados, los artículos de origen predeterminados y reindexa el inventario para SKU de producto específicos. Necesario cuando la variable [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) la operación masiva está habilitada en los ajustes de configuración del sistema de administración. |  |  |  |
| `inventory.reservations.cleanup` | + | + | + |
| Elimina de forma asíncrona las reservas por SKU de producto después de eliminar un producto. Necesario cuando la variable [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) la opción stock está activada en los ajustes de configuración del sistema de administración. |  |  |  |
| `inventory.reservations.update` | + | + | + |
| Actualiza asincrónicamente las reservas por SKU de producto después de eliminar un producto. Necesario cuando la variable [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) la opción stock está activada en los ajustes de configuración del sistema de administración. |  |  |  |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Actualiza asincrónicamente la cantidad vendible de cada producto asignado a una existencias. Este consumidor siempre debe estar en funcionamiento si utiliza [!DNL Inventory Management]. |  |  |  |
| `inventory.indexer.sourceItem` | + | + | + |
| Reindexa asincrónicamente los elementos de origen. Necesario cuando la variable [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) se configura como &quot;[!UICONTROL asynchronous]&quot; en los ajustes de configuración del sistema de administración. |  |  |  |
| `inventory.indexer.stock` | + | + | + |
| Reindexa las existencias. Necesario cuando la variable [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) se configura como &quot;[!UICONTROL asynchronous]&quot; en los ajustes de configuración del sistema de administración. |  |  |  |
| `matchCustomerSegmentProcessor` | + | + |  |
| Crea una tabla de base de datos temporal, mueve cada [segmento de cliente](https://docs.magento.com/user-guide/marketing/customer-segments.html) en él, elimina todos los segmentos que coinciden con el ID de segmento y los copia en los segmentos de cliente usando el ID de segmento como indicador. Todo esto se hace en una transacción para que si algo falla, devuelva la transacción a lo que era antes de que se ejecutara. Después de una transacción, el consumidor descarta la tabla temporal. |  |  |  |
| `media.content.synchronization` | + | + | + |
| Garantiza que los vínculos a medios asignados para productos, categorías, bloques de CMS y páginas de CMS se asignen correctamente al recurso. Elimina los activos antiguos que ya no se utilizan. |  |  |  |
| `media.gallery.renditions.update` | + | + | + |
| Genera y valida rutas de recursos multimedia. La ruta absoluta a un recurso viene determinada por su ubicación en el servidor desde el directorio de medios. Las imágenes se cambian de tamaño (si es necesario) y se copian en el directorio de medios dentro de la ruta generada. |  |  |  |
| `media.gallery.synchronization` | + | + | + |
| Importa archivos de imagen a la variable `media_gallery_asset` tabla de base de datos. |  |  |  |
| `media.storage.catalog.image.resize` | + | + | + |
| Asíncronamente [redimensionados](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) catálogo de imágenes. |  |  |  |
| `negotiableQuotePriceUpdate` |  | + |  |
| Actualiza los precios de las cotizaciones negociables. Necesario cuando la variable [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) está activada en la configuración del sistema de administración. |  |  |  |
| `placeOrderProcessor` | + | + |  |
| Asíncronamente [órdenes de procesamiento](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), que marcan los pedidos como recibidos, los coloca en la cola de mensajes y los procesa por primera vez. Se considera un [prácticas recomendadas](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) para mejorar el número de pedidos que se pueden procesar porque los clientes no necesitan esperar a que se completen los procesos del servidor antes de ver un mensaje de éxito. |  |  |  |
| `product_action_attribute.update` | + | + | + |
| Escribe asincrónicamente cambios en los atributos del producto en la base de datos después de usar el administrador para [hacer actualizaciones](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_action_attribute.website.update` | + | + | + |
| Escribe asincrónicamente cambios en los atributos del producto para una vista de tienda específica en la base de datos después de usar el administrador para [hacer actualizaciones](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_alert` | + | + | + |
| Envía correos electrónicos de notificación a los clientes sobre los cambios en el precio del producto y en el inventario. Necesario cuando el valor de requerido es [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) está activada en la configuración del sistema de administración. |  |  |  |
| `purchaseorder.toorder` |  | + |  |
| Convierte el pedido de compra a [pedido](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). Necesario cuando la variable [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está activada en la configuración del sistema de administración. |  |  |  |
| `purchaseorder.transactional.email` |  | + |  |
| Envía correos electrónicos de orden de compra. Necesario cuando la variable [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está activada en la configuración del sistema de administración. |  |  |  |
| `purchaseorder.validation` |  | + |  |
| Valida el pedido de compra con respecto a [reglas de aprobación](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). Necesario cuando la variable [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) está activada en la configuración del sistema de administración. |  |  |  |
| `sales.rule.update.coupon.usage` | + | + | + |
| Evita que [problema](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) donde los cupones de un solo uso se pueden usar varias veces. |  |  |  |
| `sharedCatalogUpdateCategoryPermissions` |  | + |  |
| Actualiza las categorías asignadas a una categoría de catálogo compartido. Necesario cuando la variable [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) está activada en la configuración del sistema de administración. |  |  |  |
| `sharedCatalogUpdatePrice` |  | + |  |
| Actualiza el precio de cada producto en un catálogo compartido. Necesario cuando la variable [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) está activada en la configuración del sistema de administración. |  |  |  |
| `quoteItemCleaner` | + | + |  |
| Elimina las comillas de precio no válidas o inactivas cuando un producto se elimina del catálogo o del carro de compras. Necesario cuando la variable [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) está activada en la configuración del sistema de administración. |  |  |  |

{style=&quot;table-layout:auto&quot;}
