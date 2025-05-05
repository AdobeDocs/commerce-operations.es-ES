---
title: 'MDVA-39031: Añadir productos sin asignar al carro de compras es posible mediante GraphQL'
description: El parche MDVA-39031 soluciona el problema de que es posible añadir un producto al carro de compras mediante GraphQL aunque no esté asignado al sitio web de destino. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6. El ID del parche es MDVA-39031. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: GraphQL, Orders, Products, Shopping Cart
role: Admin
exl-id: 6250c6f6-b74b-4713-a704-d252270693d4
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-39031: Añadir productos sin asignar al carro de compras es posible mediante GraphQL

El parche MDVA-39031 soluciona el problema de que es posible añadir un producto al carro de compras mediante GraphQL aunque no esté asignado al sitio web de destino. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6. El ID del parche es MDVA-39031. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Es posible añadir un producto al carro de compras mediante GraphQL aunque no esté asignado al sitio web de destino.

<u>Pasos a seguir</u>:

1. Crear un sitio web secundario.
1. Cree un producto y asígnelo al sitio web principal.
1. Cree un carro de compras vacío para el sitio web secundario mediante GraphQL.

   <pre>
    <code class="language-graphql">
    mutation&lbrace;
     createEmptyCart
    &rbrace;
    </code>
    </pre>

   Con encabezados como:

   <pre>
    <code class="language-graphql">
    &lbrace;
      "Store":"en_au"
    &rbrace;
    </code>
    </pre>

1. Añada el producto asignado al sitio web principal al carro de compras en el sitio web secundario.

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      addProductsToCart(
          cartId: "XHrUN2nJ37OqDByhtL0VC8OxYsEZs41c"
          cartItems: &lbrack;
            &lbrace;
              quantity: 1
              sku: "p1"
            &rbrace;
          &rbrack;
        ) &lbrace;
          cart &lbrace;
           items &lbrace;
            product &lbrace;
              name
              sku
            &rbrace;
            quantity
          &rbrace;
        &rbrace;
      &rbrace;
    &rbrace;
    </code>
    </pre>

   Encabezados

   <pre>
    <code class="language-graphql">
    &lbrace;
      "Store":"en_au"
    &rbrace;
    </code>
    </pre>

<u>Resultados esperados</u>:

El producto no se agrega al carro de compras porque no se asignó al almacén definido en el encabezado.

<u>Resultados reales</u>:

El producto se ha agregado correctamente al carro de compras.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
