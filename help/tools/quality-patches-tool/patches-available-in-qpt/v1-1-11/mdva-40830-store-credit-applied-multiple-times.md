---
title: 'MDVA-40830: crédito de tienda aplicado varias veces durante el pedido'
description: El parche MDVA-40830 soluciona el problema de que el crédito de la tienda se aplica varias veces durante la realización del pedido. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11. El ID del parche es MDVA-40830. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Orders, Returns
role: Admin
exl-id: 4ee952c8-2736-47b2-84f6-a7a0556608dd
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# MDVA-40830: crédito de tienda aplicado varias veces durante el pedido

El parche MDVA-40830 soluciona el problema de que el crédito de la tienda se aplica varias veces durante la realización del pedido. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11. El ID del parche es MDVA-40830. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.3.7-p2, 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El crédito de la tienda se aplica varias veces durante la realización del pedido.

<u>Pasos a seguir</u>:

1. Cree un cliente y añada crédito de tienda a la cuenta del cliente.
1. Añadir un producto simple al carro de compras.
1. Establecer la dirección de envío y la dirección de facturación del carro de compras.
1. Compruebe el grand_total del carro de compras.
1. Aplique crédito de tienda al carro de compras mediante la siguiente solicitud de GraphQL:

<pre>
<code class="language-graphql">
mutation &lbrace;
  applyStoreCreditToCart(
    input: { cart_id: "%cartId%" }
  ) &lbrace;
    cart &lbrace;
      prices &lbrace;
        grand_total &lbrace;
          currency
          value
        &rbrace;
      &rbrace;
      applied_store_credit &lbrace;
        applied_balance &lbrace;
          currency
          value
        &rbrace;
        current_balance &lbrace;
          currency
          value
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>Resultados esperados</u>:

El valor de applied_store_credit se aplica con precisión y los totales del carro de compras se reflejan correctamente en la respuesta de la API.

<u>Resultados reales</u>:

El valor de applied_store_credit se aplica dos veces, afectando tanto al carrito como a grand_total.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
