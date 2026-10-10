---
title: 'MDVA-37234: al agregar un elemento al carro de compras varias veces, se crea un elemento de línea duplicado'
description: El parche de MDVA-37234 soluciona el problema de que, al añadir un artículo al carro de compras varias veces (solicitud paralela) para la misma SKU, se crea un elemento de línea duplicado para la misma ID de carro de compras. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3. El ID del parche es MDVA-37234. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: Orders, Shopping Cart
role: Admin
exl-id: d4e9fca1-7fba-4a33-9c5e-c9695cbfc61c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%
---
# MDVA-37234: al agregar un elemento al carro de compras varias veces, se crea un elemento de línea duplicado

El parche de MDVA-37234 soluciona el problema de que, al añadir un artículo al carro de compras varias veces (solicitud paralela) para la misma SKU, se crea un elemento de línea duplicado para la misma ID de carro de compras. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.3. El ID del parche es MDVA-37234. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.6, 2.4.1 y 2.4.2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.5 - 2.3.7-p1 y 2.4.1 - 2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Si agrega un artículo al carro de compras varias veces (solicitud paralela) para el mismo SKU, se crea un artículo de línea duplicado para el mismo ID de carro de compras.

<u>Pasos a seguir</u>:

1. Cree un producto simple con SKU = simple1.
1. Crear un cliente.
1. Genere un token de cliente para realizar una solicitud de GraphQL.

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
        generateCustomerToken(
            email: "customer email"
            password: "customer password"
        )
        &lbrace;
            token
        &rbrace;
    &rbrace;
    </code>
    </pre>

1. Utilice el token mencionado en el paso 3 para crear un carro de compras vacío para el cliente.

   <pre>
    <code class="language-graphql">
    mutation&lbrace;
     createEmptyCart
    &rbrace;
    </code>
    </pre>

1. Cree un script para hacer dos `addSimpleProductsToCart` solicitudes ejecutándose en paralelo. Por ejemplo:

   <pre>
    <YOUR_ACCESS_TOKEN><YOUR_CART_ID><YOUR_ACCESS_TOKEN><YOUR_CART_ID>
    </pre>

1. Ejecute el script.

<u>Resultados esperados</u>:

En el carro de compras solo se crea una línea de productos con una cantidad total (tres en este caso).

<u>Resultados reales</u>:

En el carro de compras se crean dos líneas independientes para el mismo producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del tipo de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre parches de calidad para Adobe Commerce, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es).
