---
title: 'ACSD-57643: productos con opciones personalizadas añadidas incorrectamente al carro de compras mediante GraphQL'
description: Aplique el parche ACSD-57643 para corregir el problema de Adobe Commerce en el que los productos con opciones personalizadas se agregan incorrectamente al carro de compras mediante GraphQL.
feature: Shopping Cart, GraphQL, Products
role: Admin, Developer
exl-id: 568f820b-ecab-4839-b32e-b0b42c1d2342
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-57643: productos con opciones personalizadas añadidas incorrectamente al carro de compras mediante GraphQL

El parche ACSD-57643 soluciona el problema de los productos con opciones personalizadas que se añaden incorrectamente al carro de compras mediante GraphQL. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49. El ID del parche es ACSD-57643. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce y Magento Open Source:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos con opciones personalizadas se añaden incorrectamente al carro de compras mediante GraphQL.

<u>Pasos a seguir</u>:

1. Cree un campo de tipo de opción personalizada para el producto.
1. Genere un token de cliente con GraphQL.
1. Crear un carro vacío.
1. Añada el producto al carro de compras mediante la siguiente carga útil:

   ```graphql
   mutation {
     addProductsToCart(
       cartId: "wNVOTaE6sDCJoObZCCqikHQI3GyFaVif"
       cartItems: [
         {
           quantity: 1
           sku: "24-MB01"
           entered_options: [{
             uid:"Y3VzdG9tLW9wdGlvbi8x",
             value:"product1 option1 "
           }]
         },
         {
           quantity: 1
           sku: "24-MB01"
           entered_options: [{
             uid:"Y3VzdG9tLW9wdGlvbi8x",
             value:"product2 option1"
           }]
         }
         {
           quantity: 3
           sku: "24-MB01",
           entered_options: [{
             uid:"Y3VzdG9tLW9wdGlvbi8x"
             value:"product3 option1"
           }]        
         }
       ]
     ) {
       cart {
         items {
           product {
             name
             sku
           }
           ... on SimpleCartItem {
             customizable_options {
               customizable_option_uid
               label
               values {
                 customizable_option_value_uid
                 value
               }
             }
           }
           quantity
         }
       }
       user_errors {
         code
         message
       }
     }
   }
   ```

1. Verá que el producto se agrega solo una vez:

   ```json
   {
     "data": {
       "addProductsToCart": {
         "cart": {
           "items": [
             {
               "product": {
                 "name": "Joust Duffle Bag",
                 "sku": "24-MB01"
               },
               "customizable_options": [
                 {
                   "customizable_option_uid": "Y3VzdG9tLW9wdGlvbi8x",
                   "label": "Option1",
                   "values": [
                     {
                       "customizable_option_value_uid": "Y3VzdG9tLW9wdGlvbi8x",
                       "value": "product1 option1"
                     }
                   ]
                 }
               ],
               "quantity": 5
             }
           ]
         },
         "user_errors": []
       }
     }
   }
   ```

<u>Resultados esperados</u>:

Se puede añadir un producto al carro de compras utilizando simultáneamente diferentes opciones personalizadas para el mismo SKU.

<u>Resultados reales</u>:

No se puede añadir un producto al carro de compras utilizando diferentes opciones personalizadas para el mismo SKU simultáneamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
