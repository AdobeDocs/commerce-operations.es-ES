---
title: "Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.35"
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.35.
feature: Tools and External Services
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.35

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.35.

QPT v1.1.35 incluye los siguientes parches:

1. **ACSD-51899**: corrige el problema en el que la dirección de envío predeterminada en el paso de envío de cierre de compra se rellena automáticamente con una dirección de recogida previamente seleccionada en la tienda.
1. **ACSD-52041**: corrige el problema donde el mensaje de error: *[ERROR] [!DNL Page Builder] se representaba durante 5 segundos sin liberar bloqueos*. aparece en el explorador [!DNL Chrome] al guardar el contenido editado con [!DNL Page Builder].
1. **ACSD-52095**: corrige el problema por el que el valor `manage_stock` se estableció incorrectamente en 0 en el archivo CSV después de la exportación del producto.
1. **ACSD-51358**: corrige el problema por el cual al eliminar una actualización programada sin una fecha de finalización se eliminan otras actualizaciones programadas para la misma entidad.
1. **ACSD-48070**: corrige el problema en el cual editar una actualización programada déclencheur una excepción.
1. **ACSD-51890**: corrige el problema por el que se puede hacer clic en el botón [!UICONTROL Submit review] varias veces sin la validación de reCAPTCHA v3 de [!DNL Google].
1. **ACSD-51984**: corrige el problema en el cual los valores desmarcados de *Usar valor predeterminado y los valores de campo de producto no predeterminados* no se guardan para el segundo sitio web, tienda y vista de tienda.
1. **ACSD-52398**: corrige el error *La cantidad solicitada no está disponible* que ocurre al intentar actualizar la cantidad de un producto agrupado en el carro de compras en la tienda.
1. **ACSD-52786**: corrige el problema en el que se aplica un SKU de condición de regla de catálogo a todos los productos que comienzan con el SKU dado.
1. **ACSD-52921**: corrige el problema en el que se produce un error interno al solicitar detalles del carro de compras a GraphQL cuando hay un producto configurable sin existencias en el carro de compras.
1. **ACSD-51683**: corrige el problema por el que una opción personalizable no se puede agregar al carro de compras mediante GraphQL.
1. **ACSD-52133**: corrige el problema por el que una cuenta de cliente no se puede guardar después de una actualización.
1. **ACSD-52202**: corrige el problema en el que la cantidad comercializable de existencias predeterminadas cambia incorrectamente a 0 cuando se cambia una cantidad no predeterminada a 0 en el cumplimiento del pedido.
1. **ACSD-51265**: corrige el problema con el rendimiento de reindexación de `catalog_product_price` cuando hay demasiados productos agrupados en el sistema.
1. **ACSD-52831**: corrige el problema en el cual los clientes no pueden realizar pedidos de presupuesto negociables cuando [!DNL Google reCAPTCHA v3 Invisible] está habilitado.
1. **ACSD-51845**: corrige el problema en el cual los productos subsiguientes con precios de nivel y diferentes conjuntos de atributos no se pueden actualizar a través de la API de REST masiva asincrónica.
1. **ACSD-52815**: corrige el problema en el que la entrada del campo de cantidad de un origen no predeterminado admite solo hasta 6 dígitos, a diferencia de 8 para un stock predeterminado.
1. **ACSD-51149**: corrige el problema en el cual [!UICONTROL Scheduled ImportExport] con [!UICONTROL Catalog Permissions] habilitado invalida los indexadores y luego los vaciados de caché por parte de cron.
1. **ACSD-50815**: corrige el problema por el cual la cantidad decimal de un producto simple no se puede usar para una nueva opción de producto agrupado.
1. **ACSD-52399**: corrige el problema donde la opción de producto configurable con una cantidad comercializable de 0 muestra *En stock* en la página de productos.

Utilice el menú de la izquierda para navegar a una página específica del parche.
