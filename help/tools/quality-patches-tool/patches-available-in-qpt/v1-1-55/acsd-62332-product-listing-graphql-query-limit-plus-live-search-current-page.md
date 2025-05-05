---
title: 'ACSD-62332: la consulta de GraphQL de la lista de productos está limitada a 10 000 productos y  [!DNL Live Search] establece la página actual en 1'
description: Aplique el parche ACSD-62332 para corregir los problemas de Adobe Commerce en los que la consulta de GraphQL de lista de productos está limitada a un total de 10 000 productos y en los que  [!DNL Live Search] establece la página actual en *1* en lugar de en la página *2* en los criterios de búsqueda cuando se consulta mediante GraphQL.
feature: GraphQL, Products, Search
role: Admin, Developer
source-git-commit: 276fe6ca8d1166a8f4254aca5d49cbb4b1aa607b
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-62332: la consulta GraphQL de la lista de productos está limitada a 10 000 productos y [!DNL Live Search] establece la página actual en 1

>[!NOTE]
>
>Este parche es una versión actualizada de [ACSD-55100](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-55100-graphql-does-not-return-products-beyond-10k-in-the-search-results.md) y reemplaza a [ACSD-52801](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-40/acsd-52801-graphql-product-filter-query-not-showing-partial-match-results.md) en las versiones 2.4.6 - 2.4.6-p8. Consulte los artículos correspondientes para obtener más información.

La revisión ACSD-62332 corrige los problemas en los que la consulta de GraphQL de lista de productos está limitada a `total_count` de 10 000 productos y en los que [!DNL Live Search] establece la página actual en *1* en lugar de en la página *2* en los criterios de búsqueda cuando se consulta a través de GraphQL. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. El ID del parche es ACSD-62332. Tenga en cuenta que los problemas se solucionaron en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La consulta de GraphQL de la lista de productos está limitada a un total de 10 000 productos y donde [!DNL Live Search] establece la página actual en *1* en lugar de en la página *2* en los criterios de búsqueda cuando se consulta a través de GraphQL.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
