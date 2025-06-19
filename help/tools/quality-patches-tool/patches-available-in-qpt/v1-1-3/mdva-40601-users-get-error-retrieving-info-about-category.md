---
title: 'MDVA-40601: no se pueden recuperar datos sobre la categoría modificada por la actualización programada a través de GraphQL'
description: El parche de calidad MDVA-40601 Adobe Commerce corrige el problema en el que los usuarios reciben un error al obtener información sobre la categoría modificada por la actualización programada a través de GraphQL. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3. El ID del parche es MDVA-40601. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: Categories, GraphQL
role: Admin
exl-id: c50e9f77-66eb-4c4c-b0b5-b77db84a4a0b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-40601: no se pueden recuperar datos sobre la categoría modificada por la actualización programada a través de GraphQL

El parche de calidad MDVA-40601 Adobe Commerce corrige el problema en el que los usuarios reciben un error al obtener información sobre la categoría modificada por la actualización programada a través de GraphQL. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3. El ID del parche es MDVA-40601. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.3 y 2.4.2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.1 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios reciben un error al intentar recuperar información sobre la categoría modificada por la actualización programada mediante GraphQL.

<u>Pasos a seguir</u>:

1. Configure una estructura de categorías con una subcategoría como se indica a continuación:

   <pre>
   <code class="language-graphql">
   - Root
    - Some category
         - Some child category
   </code>
   </pre>

1. Ejecute la consulta de GraphQL con el ID 49 &quot;Alguna categoría&quot;.

   <pre>
    <code class="language-graphql">
    query {
     category(id: 49) {
      name
      children {
        name
       }
     }
   }
   </code>
   </pre>

   Resultado:

   <pre>
    <code class="language-graphql">
    {
      "data": {
        "category": {
          "name": "Some category",
          "children": [
            {
              "name": "Some child category"
            }
          ]
        }
      }
    }
    </code>
    </pre>

1. Cree una actualización de programación para &quot;Alguna categoría&quot; con un nombre de categoría diferente.
1. Espere a que se active la actualización de la programación.
1. Ejecute la misma consulta que se indicó anteriormente.

<u>Resultados esperados</u>:

Recibirá el mismo resultado pero con el nombre de categoría actualizado.

<u>Resultados reales</u>:

Se obtiene el siguiente error:

<pre>
<code class="language-graphql">
{
  "errors": [
    {
      "debugMessage": "uasort() expects parameter 1 to be array, string given",
      "message": "Internal server error",
      "extensions": {
        "category": "internal"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "category"
      ]
    }
  ],
  "data": {
    "category": null
  }
}
</code>
</pre>

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del tipo de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre parches de calidad para Adobe Commerce, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
