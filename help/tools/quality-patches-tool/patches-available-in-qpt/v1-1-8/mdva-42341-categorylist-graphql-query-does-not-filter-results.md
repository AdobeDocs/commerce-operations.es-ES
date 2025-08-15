---
title: 'MDVA-42341: "categoryList" La consulta GraphQL no filtra los resultados'
description: El parche MDVA-42341 resuelve el problema de que la consulta GraphQL categoryList no filtra los resultados si una solicitud tiene el encabezado Store. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8. El ID del parche es MDVA-42341. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: GraphQL, Categories
role: Admin
exl-id: 56b81385-6db0-4e62-8e2b-bccfc9e0a581
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-42341: &quot;categoryList&quot; La consulta GraphQL no filtra los resultados

El parche MDVA-42341 resuelve el problema de que la consulta GraphQL categoryList no filtra los resultados si una solicitud tiene el encabezado Store. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8. El ID del parche es MDVA-42341. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La consulta GraphQL categoryList no filtra los resultados si una solicitud tiene el encabezado Store.

<u>Pasos a seguir</u>:

1. Cree una nueva categoría raíz y asígnele el nombre **root2**.
1. Cree un segundo sitio web, tienda o tienda y asigne **root2** al nuevo almacén.
1. Cree una nueva categoría en Categoría raíz predeterminada = category1.
1. Con una solicitud de GraphQL, obtenga una lista de categorías para el segundo sitio web (utilice Tienda de encabezado = nuevo).

<pre>
<code class="language-graphql">
&lbrace;
  categoryList(filters: {name: {match: "category1"}}) &lbrace;
    uid
    level
    name
    breadcrumbs &lbrace;
      category_uid
      category_name
      category_level
      category_url_key
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>Resultados esperados</u>:

Las categorías de la categoría raíz predeterminada no se enumeran como respuesta, ya que se utiliza un encabezado de tienda &quot;nuevo&quot;.

<u>Resultados reales</u>:

Las categorías de la categoría raíz predeterminada están disponibles en los resultados.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
