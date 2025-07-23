---
title: 'La consulta ACSD-65750: [!DNL GraphQL] "route" devuelve productos desordenados en el tipo de contenido  [!DNL Page Builder] Products'
description: Aplique el parche ACSD-65750 para corregir el problema de Adobe Commerce donde la consulta "route" de GraphQL devuelve productos desordenados en el tipo de contenido  [!DNL Page Builder] Products.
feature: GraphQL, Page Builder, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 2555327c02985a51e7f34a36dd256227b12b5924
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-65750: [!DNL GraphQL] la consulta de &quot;ruta&quot; devuelve productos desordenados en [!DNL Page Builder] Tipo de contenido de productos

El parche ACSD-65750 corrige el problema en el que la consulta &quot;route&quot; de [!DNL GraphQL] devuelve productos desordenados en el tipo de contenido de productos [!DNL Page Builder]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. El ID del parche es ACSD-65750. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1 - 2.4.8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La consulta &quot;ruta&quot; [!DNL GraphQL] no devuelve productos en el orden de clasificación correcto al usar el tipo de contenido [!DNL Page Builder] Productos.

<u>Pasos a seguir</u>:

1. Cree una nueva categoría y algunos productos en el catálogo y vincule los productos a esta categoría.
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**, edite la categoría creada y abra la pestaña **[!UICONTROL Products in Category]**.
1. Establecer **[!UICONTROL Position]** personalizado para cada producto de esta categoría.
1. Guarde la categoría y ejecute el reindexado.
1. Vaya a **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]** y haga clic en **[!UICONTROL Add New Page]**.
1. Expanda la ficha **[!UICONTROL Content]** y haga clic en **[!UICONTROL Edit with Page Builder]**.
1. Arrastre un elemento **[!UICONTROL Row]** al área de contenido y, a continuación, arrastre un elemento **[!UICONTROL Products]** dentro de la fila.
1. Configure el elemento Products de la siguiente manera:
   * **[!UICONTROL Select Products By]**: *Categoría*
   * **[!UICONTROL Category]**: *Seleccione la categoría recién creada*
   * **[!UICONTROL Sort By]**: *Posición*
1. Cambie a la ficha **[!UICONTROL Search Engine Optimization]** y establezca **[!UICONTROL URL Key]** en *test-widget*.
1. Guarde la página.
1. Realice la siguiente solicitud de [!DNL GraphQL]:

```
query {
  route(url: "/test-widget") {
    relative_url
    redirect_code
    type
    ... on CmsPage {
      identifier
      content
      __typename
    }
    ... on ProductInterface {
      uid
      __typename
    }
    ... on CategoryInterface {
      uid
      __typename
    }
    __typename
  }
}
```

<u>Resultados esperados</u>:

El sistema devuelve los productos en el orden definido por su posición en la categoría.

<u>Resultados reales</u>:

El sistema devuelve productos en un pedido que no coincide con su posición en la categoría de la respuesta de GraphQL.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
