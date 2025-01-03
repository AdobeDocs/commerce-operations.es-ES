---
title: 'ACSD-62965: corrige el mensaje LocalizedException que falta en la respuesta de colocación de pedidos de GraphQL'
description: Aplique el parche ACSD-62965 para solucionar los problemas de Adobe Commerce en los que el mensaje LocalizedException no se incluía en la respuesta de GraphQL durante la realización del pedido.
feature: Orders, GraphQL
role: Admin, Developer
source-git-commit: 8191bf8feda8f8e041ecf83d9ddf5c5119930531
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-62965: corrige el mensaje `LocalizedException` que falta en la respuesta de colocación de pedidos de GraphQL

El parche ACSD-62965 corrige el problema en el que el mensaje `LocalizedException` no se incluía en la respuesta de GraphQL durante la realización del pedido. Este parche está disponible con [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. El ID del parche es ACSD-62965. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La respuesta de GraphQL para la colocación de pedidos no incluye un mensaje `LocalizedException`, lo que da como resultado detalles de error insuficientes para la depuración.

<u>Pasos a seguir</u>:

1. Instale una instancia de **[!DNL Adobe Commerce]** limpia.
1. Añada un producto al carro de compras y continúe con el paso de colocación de pedidos.
1. Agregar un `LocalizedException` a `Magento\Framework\Exception\LocalizedException` en `app/code/Magento/QuoteGraphQl/Model/Resolver/PlaceOrder.php`.
1. Inserte la excepción después de la línea siguiente:

   ```
   $cart = $this->getCartForCheckout->execute($maskedCartId, $userId, $storeId);
   ```

   Añada la excepción:

   ```
   throw new LocalizedException(new Phrase("Test LocalizedException"));
   ```

1. Ejecute la solicitud de GraphQL de pedido de lugares:

   ```
   mutation {
   placeOrder(input: {cart_id: "cart_id"}) {
       order {
       order_number
       }
   }
   }
   ```

1. Observe la respuesta:
   1. La respuesta no incluye el mensaje `LocalizedException`.
   1. Ejemplo de respuesta incorrecta:

      ```
      {
      "data": {
          "placeOrder": {
          "order": null
          }
      }
      }
      ```

<u>Resultados esperados</u>:

Si se produce un `LocalizedException`, el mensaje de excepción debe incluirse en la respuesta de GraphQL de colocación de pedidos para mejorar la administración de errores.

<u>Resultados reales</u>:

Si se produce un `LocalizedException`, el mensaje de excepción no se incluye en la respuesta de GraphQL de la ubicación de pedido.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
