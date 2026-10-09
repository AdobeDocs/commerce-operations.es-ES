---
title: 'MDVA-40134: GraphQL no devuelve productos relacionados cuando el catálogo compartido está habilitado'
description: El parche de MDVA-40134 corrige el problema en el que GraphQL no devuelve productos relacionados cuando el catálogo compartido está habilitado. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. El ID del parche es MDVA-40134. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
exl-id: 5d31e042-4396-40ce-8bf1-63ad9a55214d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%
---
# MDVA-40134: GraphQL no devuelve productos relacionados cuando el catálogo compartido está habilitado

El parche de MDVA-40134 corrige el problema en el que GraphQL no devuelve productos relacionados cuando el catálogo compartido está habilitado. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-40134. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

GraphQL no devuelve productos relacionados cuando el catálogo compartido está habilitado.

<u>Requisitos previos</u>:

Deben instalarse los módulos B2B.
La instancia debe estar limpia con solo los datos de ejemplo.

<u>Pasos a seguir</u>:

1. Vaya a **Tiendas** > **Configuración** > **General** > **Características B2B** y habilite **Compañía y catálogo compartido**.
1. Vaya a **Catálogo** > **Catálogo compartido** y agregue todos los productos al **Catálogo general**.
1. Utilice los datos de ejemplo y modifique la bolsa de lona Joust (SKU 24-MB01).
1. En **Productos relacionados**, agregue las dos bolsas Duffle (ID 7 y 13).
1. Enviar una solicitud **Post**:

<pre>&lbrace;
  products(filter: {sku: {eq: "24-MB01"}&#x200B;}, sort: {name: ASC}) &lbrace;
    elementos &lbrace;
      related_products &lbrace;
        uid
        name
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;</pre>

<u>Resultados esperados</u>:

Los productos relacionados se muestran en la respuesta de GraphQL.

<u>Resultados reales</u>:

Los usuarios reciben el siguiente error:

<pre>El valor devuelto de Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() debe ser del tipo int, null devuelto &lbrace;"exception":"[object] (GraphQL\\Error\\Error(code: 0): El valor devuelto de Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() debe ser del tipo int, null devuelto </pre>

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
