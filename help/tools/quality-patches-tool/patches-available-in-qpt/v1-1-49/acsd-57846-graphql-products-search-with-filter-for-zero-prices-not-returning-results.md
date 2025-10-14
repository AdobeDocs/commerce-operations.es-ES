---
title: 'ACSD-57846: los productos de GraphQL buscan con el filtro cero precios no devuelven resultados'
description: Aplique el parche ACSD-57846 para corregir el problema de Adobe Commerce en el que el filtrado de productos por precio desde cero genera una solicitud con formato incorrecto a  [!DNL OpenSearch]  y no devuelve ningún resultado.
feature: GraphQL, Products
role: Admin, Developer
exl-id: ec523a54-201b-4a8f-85ce-cbe1d0bf1304
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-57846: los productos de GraphQL buscan con el filtro cero precios no devuelven resultados

El parche ACSD-57846 corrige el problema por el que el filtrado de productos para el precio desde cero conduce a una solicitud mal formada para [!DNL OpenSearch] y no devuelve ningún resultado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49. El ID del parche es ACSD-57846. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El filtrado de productos para el precio desde cero en una búsqueda de productos de GraphQL produce una solicitud mal formada para [!DNL OpenSearch] y no devuelve ningún resultado.

<u>Pasos a seguir</u>:

1. Cree una categoría con dos productos simples:
   * simple1 - precio $0
   * simple2 - precio $10
1. Asegúrese de que ambos productos estén visibles en el front-end.
1. Enviar una solicitud con `price:{from:"1"}`.

   ```graphql
   query {
     products(
       pageSize: 50
       currentPage: 1,
       filter: {price:{from:"1"}}
     ) {
       totalResult: total_count
       productItems: items {
         sku
         urlKey: url_key
         price: price_range {
           fullPrice: minimum_price {
             finalPrice: final_price {
               currency
               value
             }
           }
         }
       }
     }
   }
   ```

1. Devuelve el producto *simple2*.
1. Ahora envíe una solicitud con `price:{from:"0"}`.

   ```graphql
   query {
     products(
       pageSize: 50
       currentPage: 1,
       filter: {price:{from:"0"}}
     ) {
       totalResult: total_count
       productItems: items {
         sku
         urlKey: url_key
         price: price_range {
           fullPrice: minimum_price {
             finalPrice: final_price {
               currency
               value
             }
           }
         }
       }
     }
   }
   ```

<u>Resultados esperados</u>:

Se devuelven tanto los productos *simple1* como *simple2*.

<u>Resultados reales</u>:

No se devuelve ningún producto.

```json
{
    "data": {
        "products": {
            "totalResult": 0,
            "productItems": []
        }
    }
}
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
