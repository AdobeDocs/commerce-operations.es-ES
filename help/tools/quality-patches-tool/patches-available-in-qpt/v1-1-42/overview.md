---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.42'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.42.
feature: Tools and External Services
role: Admin, Developer
exl-id: 40db5196-0ba3-49c4-97b7-32f146c67f95
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.42

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.42.

QPT v1.1.42 incluye los siguientes parches:

1. **ACSD-53658**: corrige el problema en el cual los datos del producto *[!UICONTROL Recently Viewed]* no se actualizan correctamente en la vista de la tienda.
1. **ACSD-54626**: corrige el problema que impide crear una nueva regla de pedido de compra (`createPurchaseOrderApprovalRule`) con el atributo `NUMBER_OF_SKUS` a través de GraphQL.
1. **ACSD-53845**: corrige el problema de tiempo de espera de conexión MySQL cuando `consumer max_messages` = 0.
1. **ACSD-54890**: corrige el problema en el que `aggregate_sales_report_bestsellers_data` causa errores de MySQL debido a que el disco `/tmp` está sin espacio.
1. **ACSD-55112**: corrige el problema por el que se puede hacer clic en el botón *[!UICONTROL Submit review]* varias veces sin validación de [!DNL Google reCAPTCHA v3].
1. **ACSD-54264**: corrige el problema donde el mensaje de error *No se puede actualizar el atributo solicitado. Id. de fila: store_id* aparece cuando un cliente intenta realizar la retirada con una oferta negociable de otra vista de tienda.
1. **ACSD-54418**: corrige el problema en el que se aplica incorrectamente una cantidad fija de descuento a cada producto secundario del paquete con precio dinámico.
1. **ACSD-55238**: corrige el problema al guardar la metadescripción del producto vacía.
1. **ACSD-54966**: corrige el problema en el cual un código de cupón con un uso limitado por cliente no se puede reutilizar si falla el pedido anterior.
1. **ACSD-54060**: corrige el problema en el cual un administrador restringido no puede guardar un producto si es secundario de otro producto asignado a un ámbito diferente.
1. **ACSD-48910**: corrige el problema por el que un producto agrupado asignado a varios orígenes se queda sin existencias después de facturar y enviar un pedido, incluso si tiene una cantidad distinta de cero.
1. **ACSD-55381**: corrige un error interno del servidor al consultar los campos `configurable_product_option_uid` y `configurable_product_option_value_uid` desde un B2B *[!UICONTROL Requisition list]* a través de GraphQL.
1. **ACSD-55628**: corrige la carga de un archivo en el formulario de registro de la compañía y reemplaza un archivo por un atributo de cliente en la tienda.

Utilice el menú de la izquierda para navegar a una página específica del parche.
