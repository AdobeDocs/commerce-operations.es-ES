---
title: 'ACSD-57477: el procesamiento de reglas de ventas ralentiza el rendimiento en solicitudes relacionadas con el carro de compras'
description: Aplique el parche ACSD-57477 para solucionar el problema de Adobe Commerce en el que, en un proyecto con muchos atributos de producto disponibles (por ejemplo, atributos 1000), cuando se ejecuta la operación de GraphQL AddProductsToCart con variables, Commerce intenta cargar todos estos atributos de producto y provoca problemas de rendimiento lento desde la operación de GraphQL AddProductsToCart.
feature: GraphQL, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 00fce49fbe5432a16324937e0430a08ec7c41188
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACSD-57477: el procesamiento de reglas de ventas ralentiza el rendimiento en solicitudes relacionadas con el carro de compras

El parche ACSD-57477 corrige el problema en el que el procesamiento de reglas de ventas provoca un rendimiento lento en las solicitudes relacionadas con el carro de compras. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACSD-57477. Este problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El procesamiento de reglas de ventas provoca un rendimiento lento en las solicitudes relacionadas con el carro de compras si se envían los parámetros como variables de GraphQL.

<u>Pasos a seguir</u>:

1. Añadir 1000 atributos de producto.
1. Cree un carro de compras utilizando la siguiente consulta de GraphQL.

   ```
   mutation {createEmptyCart}{noformat}
   ```

1. Añada un producto al carro de compras mediante la siguiente consulta de GraphQL.

   ```
   mutation AddProductsToCart($cartId: String!, $products: [CartItemInput!]!) {
       addProductsToCart(cartId: $cartId, cartItems: $products) {
         cart {
           id
           __typename
         }
         __typename
       }
     }
   ```

1. Configure estas variables.

   ```
   {
     "cartId": "id_here",
     "products": [
       {
         "sku": "product_dynamic_1",
         "parent_sku": "product_dynamic_1",
         "quantity": 1
       }
     ]
   }
   ```

1. Este problema solo se produce cuando se envían los parámetros como variables de GraphQL. Si incluye los parámetros en la propia consulta de GraphQL, este problema no se produce.
1. Envíe la misma solicitud **Agregar al carro** después de agregar parámetros a la propia consulta de GraphQL.

   ```
   mutation {
    addProductsToCart(
      cartId: "id_here"
      cartItems:  [
       {
         sku: "product_dynamic_1",
         parent_sku: "product_dynamic_1",
         quantity: 1
       }
     ]
    ) {
      cart {
           id
           __typename
         }
         __typename
    }
   }
   ```

<u>Resultados esperados</u>:

El rendimiento de la operación GraphQL `AddProductsToCart` no debería verse afectado.

<u>Resultados reales</u>:

El rendimiento de la operación de GraphQL `AddProductsToCart` se degrada, ya que carga todos los atributos del producto cuando los parámetros se envían como variables.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas
