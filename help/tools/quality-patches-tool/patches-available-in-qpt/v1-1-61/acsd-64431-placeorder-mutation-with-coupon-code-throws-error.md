---
title: 'ACSD-64431: La mutación "placeOrder" con código de cupón en la solicitud genera un error interno del servidor'
description: Aplique el parche ACSD-64431 para solucionar el problema de Adobe Commerce donde la mutación "placeOrder" que contiene la información del código de cupón en la solicitud genera un error interno del servidor en lugar de realizar el pedido correctamente.
feature: GraphQL, Orders, Promotions/Events
role: Admin, Developer
source-git-commit: 883b9db12308c8832afbf709bc188edab746618f
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# ACSD-64431: La mutación &quot;placeOrder&quot; con código de cupón en la solicitud genera un error interno

El parche ACSD-64431 corrige el problema en el que la mutación `placeOrder` que contiene la información del código de cupón en la solicitud genera un error interno del servidor en lugar de realizar el pedido correctamente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. El ID del parche es ACSD-64431. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La mutación `placeOrder` que contiene la información del código de cupón en la solicitud genera un error interno, en lugar de realizar el pedido correctamente.

<u>Pasos a seguir</u>:

1. Cree un producto simple con _SKU 2836611_.
1. Cree un(a) **[!UICONTROL Cart Price Rule]**, establezca **[!UICONTROL Coupon]** en `Specific Coupon` e indique _TEST1234_ como código de cupón.
1. Crear un cliente:

   ```
   mutation {
   createCustomer(
       input: {
       firstname: "John"
       lastname: "Doe"
       email: "john.doe@example.com"
       password: "b1b2b3l@w+"
       is_subscribed: true
       }
   ) {
       customer {
       firstname
       lastname
       email
       is_subscribed
       }
   }
   }
   ```

1. Genere un token de cliente. Puede utilizar este token para solicitudes posteriores.

   ```
   mutation {
   generateCustomerToken(email: "john.doe@example.com", password: "b1b2b3l@w+") {
       token
   }
   }
   ```

1. Crear un carro vacío. Guarde el ID de carro de compras y utilícelo para las solicitudes posteriores.

   ```
   mutation {
       createEmptyCart
   } 
   ```

1. Añadir el producto al carro de compras:

   ```
   mutation {
       addProductsToCart(
           cartId: "xxxx"
           cartItems: [{ quantity: 1, sku: "2836611" }]
       ) {
           cart {
               itemsV2 {
                   items {
                       product {
                           name
                           sku
                       }
                       ... on ConfigurableCartItem {
                           configurable_options {
                               configurable_product_option_uid
                               value_label
                           }
                       }
                       quantity
                   }
                   total_count
                   page_info {
                       page_size
                       current_page
                       total_pages
                   }
               }
           }
           user_errors {
               code
               message
           }
       }
   }
   ```

1. Aplique el cupón:

   ```
   mutation {
       applyCouponToCart(input: { cart_id: "xxxx", coupon_code: "TEST1234" }) {
           cart {
               itemsV2 {
                   items {
                       product {
                           name
                       }
                       quantity
                   }
                   total_count
                   page_info {
                       page_size
                       current_page
                       total_pages
                   }
               }
               applied_coupons {
                   code
               }
               prices {
                   grand_total {
                       value
                       currency
                   }
               }
           }
       }
   }
   ```

1. Establecer una dirección de envío:

   ```
   mutation {
       setShippingAddressesOnCart(
           input: {
               cart_id: "xxxxx"
               shipping_addresses: [
                   {
                       address: {
                           firstname: "John"
                           lastname: "Doe"
                           company: "Company Name"
                           street: ["3320 N Crescent Dr", "Beverly Hills"]
                           city: "Los Angeles"
                           region: "CA"
                           region_id: 12
                           postcode: "90210"
                           country_code: "US"
                           telephone: "123-456-0000"
                           save_in_address_book: false
                       }
                   }
               ]
           }
       ) {
           cart {
               shipping_addresses {
                   firstname
                   lastname
                   company
                   street
                   city
                   region {
                       code
                       label
                   }
                   postcode
                   telephone
                   country {
                       code
                       label
                   }
                   available_shipping_methods {
                       carrier_code
                       carrier_title
                       method_code
                       method_title
                   }
               }
           }
       }
   }
   ```

1. Establecer un método de envío:

   ```
   mutation {
       setShippingMethodsOnCart(
           input: {
               cart_id: "xxxx"
               shipping_methods: [{ carrier_code: "flatrate", method_code: "flatrate" }]
           }
       ) {
           cart {
               shipping_addresses {
                   selected_shipping_method {
                       carrier_code
                       carrier_title
                       method_code
                       method_title
                       amount {
                           value
                           currency
                       }
                   }
               }
           }
       }
   }
   ```

1. Establecer una dirección de facturación:

   ```
   mutation {
       setBillingAddressOnCart(
           input: {
               cart_id: "xxxx"
               billing_address: {
                   address: {
                       firstname: "John"
                       lastname: "Doe"
                       company: "Company Name"
                       street: ["64 Strawberry Dr", "Beverly Hills"]
                       city: "Los Angeles"
                       region: "CA"
                       region_id: 12
                       postcode: "90210"
                       country_code: "US"
                       telephone: "123-456-0000"
                       save_in_address_book: true
                   }
               }
           }
       ) {
           cart {
               billing_address {
                   firstname
                   lastname
                   company
                   street
                   city
                   region {
                       code
                       label
                   }
                   postcode
                   telephone
                   country {
                       code
                       label
                   }
               }
           }
       }
   }
   ```

1. Defina una forma de pago:

   ```
   mutation {
       setPaymentMethodOnCart(
           input: { cart_id: "xxxx", payment_method: { code: "checkmo" } }
       ) {
           cart {
               selected_payment_method {
                   code
               }
           }
       }
   }
   ```

1. Realice el pedido:

   ```
   mutation {
   placeOrder(
       input: {
       cart_id: "{{cart_id}}"
       }
   ) {
       orderV2 {
       number
       token
       }
       errors {
       message
       code
       }
   }
   }
   ```


<u>Resultados esperados</u>:

Se debe realizar el pedido.

<u>Resultados reales</u>:

Aparece el siguiente mensaje de error:
`"message": "Internal server error"`

`exception.log` contiene el siguiente error:

```
    report.ERROR: "discount_model" value should be specifiedGraphQL (1:135)
    1: mutation { placeOrder(input: {cart_id: "xxxx"}) { orderV2 { total { discounts { amount { currency value } coupon { code } } } } errors { message code } } }
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Pasos adicionales necesarios tras la instalación del parche

(Esta sección es opcional; es posible que se requieran algunos pasos después de aplicar el parche para solucionar el problema). 

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
