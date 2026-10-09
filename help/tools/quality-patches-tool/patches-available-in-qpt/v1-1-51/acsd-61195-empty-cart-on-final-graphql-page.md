---
title: 'ACSD-61195: la solicitud de GraphQL del carro de compras no devuelve elementos en la página final'
description: Aplique el parche ACSD-61195 para corregir el problema de Adobe Commerce en el que no se devuelven elementos del carro de compras en la última página de la solicitud de GraphQL del carro de compras.
feature: GraphQL
role: Admin, Developer
exl-id: 15f0f29c-8517-4f1e-9370-772572e75c9a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%
---
# ACSD-61195: la solicitud de GraphQL del carro de compras no devuelve elementos en la página final

El parche ACSD-61195 corrige el problema de que no se devuelven elementos del carro de compras en la última página de la solicitud de GraphQL del carro de compras. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.51. El ID del parche es ACSD-61195. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1 - 2.4.7-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La solicitud de GraphQL del carro de compras no devuelve elementos en la página final.

<u>Pasos a seguir</u>:

1. Crear un nuevo carro de compras:

   ```graphql
   mutation createEmptyCart($input: createEmptyCartInput) {
       createEmptyCart(input: $input)
   } 
   ```

1. Añadir más de cinco productos al carro de compras:

   ```text
   addProductsToCart(
       cartId: "{{cartId}}"
       cartItems: [
         {
           quantity: 1
           sku: "test"
         }
       ]
     ) {
       cart {
          itemsV2 {
          items {
           product {
            name
            sku
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

1. Ejecute la siguiente consulta:

   ```text
   cart(cart_id: $cartId) {
   email
   itemsV2(pageSize: 2, currentPage: 3) {
       total_count
       page_info {
          page_size
          current_page
          total_pages
       }
     items {
       id
       product {
         name
         sku
       }
       quantity
       }
   }
   }  
   ```

<u>Resultados esperados</u>:

La consulta devuelve los elementos de la última página.

<u>Resultados reales</u>:

```json
  {
    "data": {
        "cart": {
            "email": "roni_cost@example.com",
            "itemsV2": {
                "total_count": 5,
                "page_info": {
                    "page_size": 2,
                    "current_page": 3,
                    "total_pages": 3
                },
                "items": []
            }
        }
    } 
    }  
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
