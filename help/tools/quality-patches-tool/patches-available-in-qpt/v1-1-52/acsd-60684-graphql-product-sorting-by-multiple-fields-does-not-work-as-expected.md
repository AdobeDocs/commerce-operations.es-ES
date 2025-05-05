---
title: 'ACSD-60684: [!DNL GraphQL] la ordenación de productos por varios campos no funciona según lo esperado'
description: Aplique el parche ACSD-60684 para solucionar el problema de Adobe Commerce donde la ordenación de  [!DNL GraphQL] productos por varios campos no funciona cuando se pasa la ordenación en variables.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 1c29299b-c85f-4166-886b-357a1486e67e
source-git-commit: a5dda25e502889ee0a23e99b412aeeb863de452c
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# ACSD-60684: la ordenación de productos [!DNL GraphQL] por varios campos no funciona según lo esperado

La revisión ACSD-60684 corrige el problema en el cual la ordenación de productos [!DNL GraphQL] por varios campos no funciona cuando la ordenación se pasa en variables. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52. El ID del parche es ACSD-60684. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!DNL GraphQL] la ordenación de productos por varios campos no funciona como se esperaba.

<u>Pasos a seguir</u>:

1. Cree tres productos con los nombres A, B y C.
1. Recupere los productos utilizando los siguientes [!DNL GraphQL]:

   ```
   query FindProducts($search: String, $filter:ProductAttributeFilterInput!, $pageSize: Int!, $currentPage: Int!, $sort: ProductAttributeSortInput!){
       products(search: $search, filter: $filter, pageSize: $pageSize, currentPage: $currentPage, sort: $sort){
           total_count
           page_info{total_pages}
           items{
               __typename
               url_key
               sku
               name
               stock_status
               price_range{
                   minimum_price{
                       final_price{
                           value
                           currency
                       }
                   }
               }
           }
       }
   } 
   ```

   Variables:

   ```
   {
       "search": null,
       "filter": {
   
       },
       "pageSize": 24,
       "currentPage": 1,
       "sort": {
           "name": "ASC"
       }
   }  
   ```

1. Repita la consulta con `sort` : `DESC`

<u>Resultados esperados</u>:

Los resultados se ordenan correctamente.

<u>Resultados reales</u>:

No se ha aplicado el orden seleccionado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
