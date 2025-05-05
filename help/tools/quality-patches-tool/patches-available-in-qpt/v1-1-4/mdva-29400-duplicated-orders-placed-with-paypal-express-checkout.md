---
title: "MDVA-29400: Pedidos duplicados realizados con el pago y envío de PayPal Express"
description: El parche de MDVA-29400 soluciona el problema en el que se crean pedidos duplicados cuando los clientes realizan pedidos con el Pago y envío de PayPal Express. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4. El ID del parche es MDVA-29400. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.1.
feature: Checkout, Orders, Payments
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# MDVA-29400: pedidos duplicados realizados con el pago y envío de PayPal Express

El parche de MDVA-29400 soluciona el problema en el que se crean pedidos duplicados cuando los clientes realizan pedidos con el Pago y envío de PayPal Express. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4. El ID del parche es MDVA-29400. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.1.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los pedidos duplicados se crean cuando los usuarios realizan pedidos con Pago y envío de PayPal Express.

<u>Requisitos previos</u>:

Pago y envío por PayPal Express activado y configurado.

<u>Pasos a seguir</u>:

1. Añadir un producto al carro de compras.
1. Ve a la página de pago y utiliza PayPal Express como forma de pago.
1. Se redirigirá a paypal/express/review/ page.
1. Realice el pedido. Se le redirigirá a la página de éxito.
1. Vuelve a PayPal/express/review/Page.
1. Haz clic en el botón **Realizar pedido**.

<u>Resultados esperados</u>:

Solo se crea un pedido.

<u>Resultados reales</u>:

Recibe el siguiente error: *El token de pago y envío de PayPal Express no existe*, pero el segundo pedido se realizó correctamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
