---
title: 'ACSD-56090: la respuesta de GraphQL no es específica del almacén'
description: Aplique el parche ACSD-56090 para solucionar el problema de Adobe Commerce, donde la respuesta de GraphQL contiene todos los almacenes de datos en lugar de los específicos del almacén de datos.
feature: GraphQL
role: Admin, Developer
exl-id: 0909c09c-3260-43d2-8eac-0e5d7639f24b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%
---
# ACSD-56090: la respuesta de GraphQL no es específica del almacén

El parche ACSD-56090 corrige el problema en el que la respuesta de GraphQL contiene todos los datos de los almacenes en lugar de los datos específicos de los almacenes. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.43. El ID del parche es ACSD-56090. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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

```graphql
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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
