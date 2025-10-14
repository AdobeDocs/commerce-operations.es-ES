---
title: 'ACSD-56090: la respuesta de GraphQL no es específica del almacén'
description: Aplique el parche ACSD-56090 para solucionar el problema de Adobe Commerce, donde la respuesta de GraphQL contiene todos los almacenes de datos en lugar de los específicos del almacén de datos.
feature: GraphQL
role: Admin, Developer
exl-id: 0909c09c-3260-43d2-8eac-0e5d7639f24b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-56090: la respuesta de GraphQL no es específica del almacén

El parche ACSD-56090 corrige el problema en el que la respuesta de GraphQL contiene todos los datos de los almacenes en lugar de los datos específicos de los almacenes. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43. El ID del parche es ACSD-56090. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La respuesta de GraphQL contiene todos los datos de los almacenes en lugar de los datos específicos del almacén.

<u>Pasos a seguir</u>:

1. Inicie sesión en **[!UICONTROL Admin panel]** > **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** y cree dos categorías raíz.
1. Cada categoría raíz debe tener una subcategoría.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL All stores]** > Hay dos tiendas con diferentes categorías raíz para cada una. (Cada tienda debe tener al menos una vista de tienda)
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > y cree un producto con

* Todas las categorías raíz y subcategorías asignadas
* Todos los sitios web asignados.

1. Ejecute la consulta de GraphqQL (añadir encabezado — store = &#39;storename ):

```
   query {
     products(filter: { url_key: { eq: "abc" } }) {
       items {
         categories {
           name
           id
           url_path
           breadcrumbs {
             category_id
             category_name
             category_level
           }
         }
       }
     }
   }
```

1. Compruebe la respuesta después de ejecutar la consulta de GraphqQL.

<u>Resultados esperados</u>:

Se devuelven los datos específicos del almacén

<u>Resultados reales</u>:

Los datos devueltos no son específicos del almacén.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
