---
title: 'MDVA-41631: Error al recuperar la información del pedido sin el valor "phone" opcional'
description: El parche MDVA-41631 corrige el problema en el que los usuarios obtienen un error al recuperar la información del pedido sin el valor "phone" opcional a través de  [!DNL GraphQL]. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: Orders
role: Admin
exl-id: e56cea59-ffc1-4520-85ca-136cda613884
source-git-commit: 3f14d93eca09967e320aae4af5e94c6d0c16cd20
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# MDVA-41631: Error al recuperar la información del pedido sin el valor &quot;phone&quot; opcional

La revisión MDVA-41631 corrige el problema en el cual los usuarios obtienen un error al recuperar la información del pedido sin el valor &quot;phone&quot; opcional a través de [!DNL GraphQL]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.7. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios obtienen un error al recuperar la información del pedido sin el valor &quot;phone&quot; opcional a través de [!DNL GraphQL].

<u>Pasos a seguir</u>:

1. Vaya a **Tienda** > **Configuración** > **Clientes** > **Configuración del cliente** > **Opciones de nombre y dirección** > **Mostrar teléfono** y establezca el número de teléfono como opcional.
1. Realice un pedido con [!DNL GraphQL API] como cliente que inició sesión.
   * No configure el número de teléfono al configurar las direcciones de facturación y envío. Siga las instrucciones que se dan en [[!DNL GraphQL] Tutorial de cierre de compra](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) en nuestra documentación para desarrolladores.
1. Recupere el pedido utilizando la consulta [!DNL GraphQL] [`customerOrders` ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/orders/).

<pre>
<code class="language-graphql">
&lbrace;
  customer &lbrace;
    firstname
    lastname
    suffix
    email

    orders(filter:{number:{eq:"000000001"}})&lbrace;
        items&lbrace;
          billing_address &lbrace;
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
&rbrace;
shipping_address &lbrace;
firstname
lastname
street
city
region
region_id
postcode
telephone
country_code
&rbrace;
        &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>Resultados esperados</u>:

Los usuarios obtienen la información del pedido.

<u>Resultados reales</u>:

Los usuarios reciben el siguiente error: *&quot;message&quot;: &quot;Error interno del servidor&quot;,*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
