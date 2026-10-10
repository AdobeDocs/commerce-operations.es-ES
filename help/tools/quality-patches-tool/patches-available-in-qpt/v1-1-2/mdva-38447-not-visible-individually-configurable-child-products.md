---
title: 'MDVA-38447: Los productos secundarios configurables "no visibles individualmente" se devuelven en la respuesta de GraphQL y en la consulta MySQL lenta'
description: El parche de MDVA-38447 Adobe Commerce corrige el problema en el que los productos secundarios configurables "No visibles individualmente" se devuelven en la respuesta de GraphQL y ralentizan la consulta MySQL para productos de GraphQL con el filtro de categoría. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. El ID del parche es MDVA-38447. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
exl-id: d97297c5-e8e8-407b-b43b-033937426fe2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 1%
---
# MDVA-38447: Los productos secundarios configurables &quot;no visibles individualmente&quot; se devuelven en la respuesta de GraphQL y en la consulta MySQL lenta

El parche de MDVA-38447 Adobe Commerce corrige el problema en el que los productos secundarios configurables &quot;No visibles individualmente&quot; se devuelven en la respuesta de GraphQL y ralentizan la consulta MySQL para productos de GraphQL con el filtro de categoría. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-38447. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos secundarios configurables &quot;No visibles individualmente&quot; se devuelven en la respuesta de GraphQL y en la consulta lenta de MySQL para la consulta de productos de GraphQL con el filtro de categoría.

<u>Requisitos previos</u>:

Deben instalarse los módulos B2B.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con productos simples configurados en **No visible individualmente**.
1. Ejecute **reindexación completa**.
1. Ejecutar una **consulta GraphQL** como:

<pre>query getFilteredProducts()
  $filter: ProductAttributeFilterInput.
  $sort: ProductAttributeSortInput.
  $search: String
  $pageSize: Int!
  $currentPage: Int!
) &lbrace;
  products()
    filter: $filter
    sort: $sort
    buscar: $search
    pageSize: $pageSize
    currentPage: $currentPage
  ) &lbrace;
    total_count
    page_info &lbrace;
      total_pages
      current_page
      page_size
    &rbrace;
    elementos &lbrace;
      name
      sku
    &rbrace;
  &rbrace;
&rbrace;</pre>

Variables:

<pre>{"filter":{"user_group":{"eq":""}&#x200B;},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>Resultados esperados</u>:

Los productos con visibilidad definida como &quot;No visible individualmente&quot; no se devolverán como respuesta.

<u>Resultados reales</u>:

Los productos con la visibilidad configurada como &quot;No visible individualmente&quot; se devuelven como respuesta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del tipo de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre parches de calidad para Adobe Commerce, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es).
