---
title: 'ACSD-52801: la consulta del filtro de producto de GraphQL no muestra resultados de coincidencia parciales'
description: Aplique el parche ACSD-52801 para corregir el problema de Adobe Commerce en el que la consulta del filtro de producto de GraphQL no muestra resultados de coincidencia parciales.
feature: Products
role: Admin, Developer
exl-id: 946a7189-60b2-4812-92ca-ed7ba35b2488
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-52801: la consulta del filtro de producto de GraphQL no muestra resultados de coincidencia parciales

>[!NOTE]
>
>Se ha lanzado un parche actualizado ([ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md)) para resolver el mismo problema en las versiones 2.4.6 - 2.4.6-p8. Sustituye al parche ACSD-52801 en las versiones 2.4.6 y posteriores. Para obtener más información, consulte [ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md).

El parche ACSD-52801 corrige el problema en el que la consulta del filtro de producto de GraphQL no muestra resultados de coincidencia parciales. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40. El ID del parche es ACSD-52801. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2, 2.4.5-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La consulta del filtro de producto de GraphQL no muestra resultados de coincidencia parciales.

<u>Pasos a seguir</u>:

1. Instale una instancia limpia con datos de ejemplo.
1. Ejecute la siguiente consulta de GraphQL.

```GraphQL
{
  products(
    filter: { name: { match: "Life" } }
    sort: { position: ASC }
    pageSize: 100
    currentPage: 1
  ) {
    total_count
    items {
      url_key
      sku
      name
      meta_title
    }
  }
}
```

<u>Resultados esperados</u>:

Permite resultados de coincidencia similares a los de la búsqueda avanzada de tienda al agregar el atributo `match_type` ([!UICONTROL PARTIAL], [!UICONTROL FULL]) para controlar los resultados requeridos. [!UICONTROL FULL] coincide con palabras completas y [!UICONTROL PARTIAL] coincide con palabras parciales como vida contenida en palabras de por vida.

<u>Resultados reales</u>:

La consulta del filtro de producto no devuelve los resultados de coincidencias parciales para las palabras clave de búsqueda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
