---
title: 'ACSD-50234: nombre de cliente incorrecto en el correo electrónico de confirmación para pedidos realizados con  [!DNL PayPal]'
description: Aplique el parche ACSD-50234 para corregir el problema de Adobe Commerce en el que el nombre del cliente se muestra incorrectamente en el correo electrónico de confirmación para los pedidos realizados con  [!DNL PayPal].
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 9a8a7cef-0166-4b4b-96a0-87fd4f1a0ef3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-50234: nombre de cliente incorrecto en el correo electrónico de confirmación para pedidos realizados con [!DNL PayPal]

El parche ACSD-50234 corrige el problema en el que el nombre del cliente se muestra incorrectamente en el correo electrónico de confirmación para los pedidos realizados con [!DNL PayPal]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-50234. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El correo electrónico de confirmación de los pedidos realizados con [!DNL PayPal] muestra un nombre de cliente incorrecto.

<u>Pasos a seguir</u>

1. Habilitar **[!UICONTROL PayPal Express Checkout]**.
1. Vaya al front-end como invitado.
1. Añadir productos al carro de compras.
1. Cierre de compra utilizando **[!UICONTROL PayPal Express Checkout]** como método de pago.
1. Compruebe el correo electrónico de confirmación del pedido.

<u>Resultados esperados</u>

El correo electrónico de confirmación del pedido, el correo electrónico de la factura y todos los correos electrónicos relacionados con el envío se dirigen al nombre del cliente.

<u>Resultados reales</u>

El correo electrónico de confirmación de pedido, el correo electrónico de factura y todos los correos electrónicos relacionados con el envío se envían a *Invitado*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
