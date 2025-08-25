---
title: 'ACSD-66963: la mutación "estimateTotals" devuelve un valor nulo para los descuentos en productos virtuales'
description: Aplique el parche ACSD-66963 para solucionar el problema de Adobe Commerce donde "estimateTotals" devuelve "null*" para obtener descuentos cuando se aplica un código de descuento a un carro de compras que solo contiene productos virtuales.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 0eede09026df98426cd3b6b1550be274c26d7e13
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# ACSD-66963: la mutación `estimateTotals` devuelve un valor nulo para los descuentos en productos virtuales

El parche ACSD-66963 corrige el problema en el que `estimateTotals` devuelve *null* para obtener descuentos cuando se aplica un código de descuento a un carro de compras que solo contiene productos virtuales. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. El ID del parche es ACSD-66963. Tenga en cuenta que este problema se solucionó en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La mutación `estimateTotals` devuelve *null* para obtener descuentos cuando se aplica un código de descuento a un carro que solo contiene productos virtuales.

<u>Pasos a seguir</u>:

1. Cree un carro de compras que contenga únicamente productos virtuales.
1. Aplicar un código de descuento:

   ```
   mutation {
     estimateTotals(
       input: {
         cart_id: "cart_id",
         address: {
           country_code: US,
           postcode: "78732",
           region: {
             region_code: "TX"
           }
         },
         shipping_method: {
           carrier_code: "{$shipping}",
           method_code: "{$shipping}"
         }
       }
     ) {
       cart {
         prices {
           discounts {
             amount {
               value
               currency
             }
             label
             coupon {
               code
             }
             applied_to
             type
           }
         }
       }
     }
   }
   ```

<u>Resultados esperados</u>:

La información de descuento se incluye para carros que solo contienen productos virtuales.

    &quot;
    &lbrace;
    &quot;datos&quot;: &lbrace;
    &quot;estimateTotals&quot;: &lbrace;
    &quot;cart&quot;: &lbrace;
    &quot;precios&quot;: &lbrace;
    &quot;descuentos&quot;: &lbrack;
    &lbrace;
    &quot;amount&quot;: &lbrace;
    &quot;value&quot;: 100.5,
    &quot;currency&quot;: &quot;USD&quot;
    &rbrace;,
    &quot;label&quot;: &quot;Un segundo código de descuento para pruebas&quot;,
    &quot;coupon&quot;: &lbrace;
    &quot;code&quot;: &quot;z3r0c00l&quot;
    &rbrace;,
    &quot;applied_to&quot;: &quot;ITEM&quot;,
    &quot;type&quot;: null
    &rbrace;
    &rbrack;
    &rbrace;
    &rbrace;
    &rbrace;
    &rbrace;,
    &quot;extensions&quot;: {}
    &rbrace;
    &quot;

<u>Resultados reales</u>:

La información de descuento se devuelve como *null* para carros de compras con solo productos virtuales.

    &quot;
    &lbrace;
    &quot;datos&quot;: &lbrace;
    &quot;estimateTotals&quot;: &lbrace;
    &quot;cart&quot;: &lbrace;
    &quot;precios&quot;: &lbrace;
    &quot;descuentos&quot;: null
    &rbrace;
    
    &rbrace;
    &rbrace;,
    &quot;extensiones&quot;: {}
    &rbrace;
    &quot;

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
