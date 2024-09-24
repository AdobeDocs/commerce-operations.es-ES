---
title: "MDVA-44505: La consulta de GraphQL para el carro de compras que aplica puntos de recompensa no actualiza el total general"
description: El parche MDVA-44505 resuelve el problema en el que la consulta de GraphQL para un carro de compras que aplica puntos de recompensa no considera los puntos de recompensa y devuelve un total general incorrecto. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14. El ID del parche es MDVA-44505. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-44505: La consulta de GraphQL para el carro de compras que aplica puntos de recompensa no actualiza el total general

El parche MDVA-44505 resuelve el problema en el que la consulta de GraphQL para un carro de compras que aplica puntos de recompensa no considera los puntos de recompensa y devuelve un total general incorrecto. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14. El ID del parche es MDVA-44505. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La consulta de GraphQL para un carro de compras que aplica puntos de recompensa no tiene en cuenta los puntos de recompensa y devuelve un total general incorrecto.

<u>Pasos a seguir</u>:

1. Configure los puntos de recompensa.
1. Crear un carro de compras y aplicar algunos puntos de recompensa.
1. Llame a la consulta `GetCart` desde el extremo `GraphQL` y recupere el carro de compras:

   ```GraphQL
   query {
     cart(cart_id: "{CART_ID}") {
       prices {
         discounts {
           amount {
             value
           }
         }
         grand_total {
           value
         }
       }
     }
   }
   ```

1. Compruebe la entrada del total general.
1. Ahora compruebe el total del carro de compras del cliente usando la API de REST (`/rest/V1/carts/mine/totals`).

<u>Resultados esperados</u>:

La consulta de GraphQL para el carro de compras devuelve el total general correcto que tiene en cuenta los puntos de recompensa.

<u>Resultados reales</u>:

La consulta de GraphQL no tiene en cuenta los puntos de recompensa y devuelve un total general incorrecto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
