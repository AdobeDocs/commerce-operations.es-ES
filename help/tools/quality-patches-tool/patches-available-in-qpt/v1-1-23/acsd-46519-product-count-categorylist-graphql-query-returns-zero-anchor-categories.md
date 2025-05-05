---
title: "ACSD-46519: [!UICONTROL product_count] en [!UICONTROL categoryList] [!DNL GraphQL] la consulta devuelve 0 para las categorías de anclaje"
description: Aplique el parche ACSD-46519 para corregir el problema de Adobe Commerce donde, al utilizar el método [!UICONTROL categoryList] [!DNL GraphQL]  para obtener categorías secundarias, muestra [!UICONTROL product_count] como 0 para las categorías principales.
feature: Categories, GraphQL, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-46519: [!UICONTROL product_count] en [!UICONTROL categoryList] [!DNL GraphQL] consulta devuelve 0 para categorías de anclaje

El parche ACSD-46519 resuelve el problema en el que la consulta [!UICONTROL product_count] de [!UICONTROL categoryList] [!DNL GraphQL] devuelve 0 para las categorías de anclaje. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23. El ID del parche es ACSD-46519. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se usa el método [!UICONTROL categoryList] [!DNL GraphQL] para obtener categorías secundarias, muestra [!UICONTROL product_count] como 0 para las categorías principales.

<u>Pasos a seguir</u>:

1. Utilice la siguiente solicitud [!DNL GraphQL] para obtener la jerarquía de categorías con [!UICONTROL product_count]:

<pre><code>
&lbrace;
  categoryList(filters: { ids: { eq: "2" } }) &lbrace;
    id
    name
    product_count
    level
    children &lbrace;
      name
      product_count
      level
      children &lbrace;
        name
        product_count
        level
        children &lbrace;
          name
          product_count
          level
          children &lbrace;
            name
            product_count
            level
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code></pre>

<u>Resultados esperados</u>:

Si la categoría principal es una categoría anclada, [!UICONTROL product_count] debe mostrar la suma de los recuentos de productos de la categoría secundaria en cada nivel.

<u>Resultados reales</u>:

Si la categoría principal es una categoría anclada, los productos se muestran como 0 para la categoría nivel 2 y hacia abajo.

<pre><code>
&lbrace;
    "data": &lbrace;
        "categoryList": &lbrack;
            &lbrace;
                "id": 2,
                "name": "Default Category",
                "product_count": 186,
                "level": 1,
                "children": &lbrack;
                    &lbrace;
                        "name": "What's New",
                        "product_count": 0,
                        "level": 2,
                        "children": []
                    &rbrace;,
                    &lbrace;
                        "name": "Women",
                        "product_count": 0,
                        "level": 2,
                        "children": &lbrack;
                            &lbrace;
                                "name": "Tops",
                                "product_count": 0,
                                "level": 3,
                                "children": []
                            &rbrace;,
                            &lbrace;
                                "name": "Bottoms",
                                "product_count": 0,
                                "level": 3,
                                "children": []
                            &rbrace;
                        &rbrack;
                    &rbrace;,
                    ...
                &rbrack;
            &rbrace;
        &rbrack;
    &rbrace;
&rbrace;
</code></pre>

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
