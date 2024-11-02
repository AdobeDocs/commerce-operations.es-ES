---
title: 'MDVA-41631: Error al recuperar la información del pedido sin el valor "phone" opcional'
description: El parche MDVA-41631 corrige el problema en el que los usuarios obtienen un error al recuperar la información del pedido sin el valor "phone" opcional a través de GraphQL. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: Orders
role: Admin
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# MDVA-41631: Error al recuperar la información del pedido sin el valor &quot;phone&quot; opcional

El parche MDVA-41631 corrige el problema en el que los usuarios obtienen un error al recuperar la información del pedido sin el valor &quot;phone&quot; opcional a través de GraphQL. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios obtienen un error al recuperar la información del pedido sin el valor &quot;phone&quot; opcional a través de GraphQL.

<u>Pasos a seguir</u>:

1. Vaya a **Tienda** > **Configuración** > **Clientes** > **Configuración del cliente** > **Opciones de nombre y dirección** > **Mostrar teléfono** y establezca el número de teléfono como opcional.
1. Realice un pedido utilizando la API de GraphQL como cliente registrado.
   * No configure el número de teléfono al configurar las direcciones de facturación y envío. Siga las instrucciones que se dan en [Tutorial de cierre de compra de GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/checkout-customer.html) en nuestra documentación para desarrolladores.
1. Recupere el pedido mediante la consulta de GraphQL [customerOrders](https://developer.adobe.com/commerce/webapi/graphql/queries/customer-orders.html).

<pre>
<code class="language-graphql">
{
  customer {
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}}){
        items{
          billing_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
shipping_address {
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
}
        }
    }
  }
}
</code>
</pre>

<u>Resultados esperados</u>:

Los usuarios obtienen información del pedido.

<u>Resultados reales</u>:

Los usuarios reciben el siguiente error: *&quot;message&quot;: &quot;Error interno del servidor&quot;,*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
