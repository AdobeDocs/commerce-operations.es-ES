---
title: 'MDVA-39935: GraphQL devuelve productos secundarios configurables deshabilitados en el nivel de sitio web'
description: El parche de MDVA-39935 Adobe Commerce corrige el problema en el que GraphQL devuelve productos secundarios configurables desactivados en el nivel de sitio web. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. El ID del parche es MDVA-39935. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: GraphQL, Configuration, Products
role: Admin
exl-id: b86b1595-ddd5-41ce-b126-287046462561
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
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
source-wordcount: '448'
ht-degree: 0%
---
# MDVA-39935: GraphQL devuelve productos secundarios configurables desactivados en el nivel de sitio web

El parche de MDVA-39935 Adobe Commerce corrige el problema en el que GraphQL devuelve productos secundarios configurables desactivados en el nivel de sitio web. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-39935. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

GraphQL devuelve productos secundarios configurables incluso después de que estén desactivados en el nivel de sitio web.

<u>Pasos a seguir</u>:

1. Habilite la opción para mostrar productos sin existencias en **Tienda** > **Configuración** > **Catálogo** > **Inventario** > **Opciones de existencias** > **Mostrar productos sin existencias** > **Sí**.
1. Seleccione cualquier **producto configurable** que tenga más de dos **productos simples**.
1. Deshabilite **Producto simple** y guarde el **Producto configurable**.
1. Recupere los datos de **producto configurable** mediante GraphQL.

<pre>
  <code class="language-graphql">
&lbrace;
  products(filter: { sku: { eq: "cp1" } }) &lbrace;
    items &lbrace;
      __typename
      name
      sku
      ... on ConfigurableProduct &lbrace;
        variants &lbrace;
          product &lbrace;
            __typename
            name
            sku
            color
            stock_status
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>Resultados esperados</u>:

Los productos desactivados NO se muestran en los resultados de la variante.

<u>Resultados reales</u>:

Los datos de productos desactivados se recuperan en los resultados de la variante.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del tipo de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre parches de calidad para Adobe Commerce, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es).
