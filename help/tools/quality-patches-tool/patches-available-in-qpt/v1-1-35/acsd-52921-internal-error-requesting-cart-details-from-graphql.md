---
title: 'ACSD-52921: Error al solicitar los detalles del carro de compras de GraphQL para un producto configurable sin existencias'
description: Aplique el parche ACSD-52921 para corregir el problema de Adobe Commerce en el que se produce un error interno al solicitar detalles del carro de compras de GraphQL para un producto configurable sin existencias.
feature: GraphQL, Configuration, Products, Shopping Cart
role: Admin
exl-id: 7790718a-6b86-497e-b1a1-88ba22c3e8ff
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-52921: Error al solicitar los detalles del carro de compras de GraphQL para un producto configurable sin existencias

El parche ACSD-52921 corrige el problema en el que se produce un error interno al solicitar detalles del carro de compras de GraphQL para un producto configurable sin existencias. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.35. El ID del parche es ACSD-52921. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error interno al solicitar los detalles del carro de compras de GraphQL para un producto configurable sin existencias.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con algunas opciones.
1. Agregue una opción para el producto configurable anterior al carro de compras desde el front-end (cierre de compra de invitado).
1. Obtenga `[ masked_id ]` de la tabla de `[ quote_id_mask ]` db para el presupuesto creado anteriormente.
1. Ejecute la siguiente consulta de GraphQL para obtener los detalles anteriores del carro de compras de invitados.

   Agregue el(la) `[ masked_id ]` recibido(a) desde el paso 3 en la consulta.

   ```GraphQL
   {
       cart(cart_id: "masked_id") {
           items {
               product {
                   name
                   sku
               }
               ... on ConfigurableCartItem {
                   configurable_options {
                       configurable_product_option_uid
                       option_label
                       configurable_product_option_value_uid
                       value_label
                   }
               }
               quantity
               errors {
                   code
                   message
               }
           }
       }
   }   
   ```

1. Esto devolverá los detalles del presupuesto sin ningún problema.
1. Vaya al servidor y actualice *[!UICONTROL Stock Status]* al *[!UICONTROL Out of Stock]* del producto configurable.
1. Ejecute la misma consulta de GraphQL, como se hace en el paso 4.

<u>Resultados esperados</u>:

El mensaje de error se envía o se trata correctamente en la respuesta.

<u>Resultados reales</u>:

Se produjo el error *500 Internal Server* como respuesta a la consulta de GraphQL.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool]
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
