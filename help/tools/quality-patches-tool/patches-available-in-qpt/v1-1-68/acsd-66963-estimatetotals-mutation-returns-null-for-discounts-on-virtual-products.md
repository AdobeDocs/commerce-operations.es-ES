---
title: 'ACSD-66963: la mutación "estimateTotals" devuelve un valor nulo para los descuentos en productos virtuales'
description: Aplique el parche ACSD-66963 para solucionar el problema de Adobe Commerce donde "estimateTotals" devuelve "null*" para obtener descuentos cuando se aplica un código de descuento a un carro de compras que solo contiene productos virtuales.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: b62e48f5-a9d6-456a-97e7-96f740d8e927
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
source-wordcount: '329'
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

   ```graphql
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

```json
    {
      "data": {
        "estimateTotals": {
          "cart": {
            "prices": {
              "discounts": [
                {
                  "amount": {
                    "value": 100.5,
                    "currency": "USD"
                  },
                  "label": "A second discount code for testing",
                  "coupon": {
                    "code": "z3r0c00l"
                  },
                  "applied_to": "ITEM",
                  "type": null
                }
              ]
            }
          }
        }
      },
      "extensions": {}
    }
```

<u>Resultados reales</u>:

La información de descuento se devuelve como *null* para carros de compras con solo productos virtuales.

```json
    {
      "data": {
        "estimateTotals": {
          "cart": {
            "prices": {
              "discounts": null
            }
          }
        }
      },
      "extensions": {}
    }
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
