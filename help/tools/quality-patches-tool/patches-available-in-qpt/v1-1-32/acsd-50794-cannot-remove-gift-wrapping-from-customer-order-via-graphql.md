---
title: 'ACSD-50794: no se puede eliminar el envoltorio para regalos del pedido del cliente mediante GraphQL'
description: Aplique el parche ACSD-50794 para solucionar el problema de Adobe Commerce en el que los usuarios no pueden eliminar el envoltorio para regalos del pedido del cliente a través de GraphQL.
feature: Gift, GraphQL, Orders
role: Admin
exl-id: e088fb18-89d3-47e4-ad02-54068c1ab653
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%
---
# ACSD-50794: no se puede eliminar el envoltorio para regalos del pedido del cliente mediante GraphQL

El parche ACSD-50794 corrige el problema en el que los usuarios no pueden eliminar el envoltorio para regalos del pedido del cliente a través de GraphQL. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32. El ID del parche es ACSD-50794. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios no pueden eliminar el envoltorio para regalos del pedido del cliente a través de GraphQL.

<u>Pasos a seguir</u>:

1. Cree un cliente desde el front-end.
1. Cree un producto sencillo.
1. Habilite *[!UICONTROL Gift Messages]* yendo a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** y establezca *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*.
1. Cree *[!UICONTROL Gift Wrapping]* yendo a **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. Obtener token de cliente.
1. Cree un carro de compras vacío, customerCart.
   * Agregar productos al carro de compras: `addProductsToCart` mutación
   * Establecer dirección de facturación: `setBillingAddressOnCart` mutación
   * Establecer dirección de envío: `setShippingAddressesOnCart` mutación
   * Definir método de envío: mutación `setShippingMethodsOnCart` (tasa plana)
   * Establecer método de pago: `setPaymentMethodOnCart` mutación (checkmo)
1. Ahora revise el envoltorio para regalos *Uid* con esta consulta del carro de compras:

   ```GraphQL
   {
     cart(cart_id: "{{CART_ID}}") {
       available_gift_wrappings{
           uid
       }
   }
   }
   ```

1. Definir envoltorio para regalos con `setGiftOptionsOnCart`.
1. Marque la consulta cart: cart.
1. Anule el ajuste de regalo mediante `setGiftOptionsOnCart` (establezca el valor en null).
1. De nuevo, compruebe la consulta cart: cart.
1. Orden: `placeOrder` mutación.
1. Ejecutar consulta del cliente: cliente.

   ```GraphQL
   query {
     customer {
       firstname
       middlename
       lastname
       suffix
       email
       orders {
           items {
               order_date
               gift_wrapping {
                   design
                   uid
               }
           }
       }
       addresses {
         firstname
         middlename
         lastname
         street
         city
         region {
           region_code
           region
         }
         postcode
         country_code
         telephone
       }
     }
   }
   ```

<u>Resultados esperados</u>:

Una vez que un usuario establece un envoltorio para regalos y lo anula, la consulta del cliente devuelve un valor nulo.

<u>Resultados reales</u>:

La consulta del cliente sigue devolviendo el envoltorio para regalos según se aplica.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
