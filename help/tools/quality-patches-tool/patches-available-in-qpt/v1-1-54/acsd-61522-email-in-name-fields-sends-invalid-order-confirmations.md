---
title: 'ACSD-61522: Las direcciones de correo electrónico de los campos *Nombre y Apellido* envían confirmaciones de pedido no válidas'
description: Aplique el parche ACSD-61522 para corregir el problema de Adobe Commerce donde es posible introducir direcciones de correo electrónico en los campos *[!UICONTROL First Name]* y *[!UICONTROL Last Name]* de un cliente invitado, lo que provoca que se envíen correos electrónicos de confirmación de pedido no válidos.
feature: Checkout, Customers
role: Admin, Developer
exl-id: e1ed7a57-4054-44db-bc17-9b9056096fce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-61522: las direcciones de correo electrónico de los campos *Nombre y Apellido* envían confirmaciones de pedidos no válidas

El parche ACSD-61522 corrige el problema en el que es posible introducir direcciones de correo electrónico en los campos *[!UICONTROL First Name]* y *[!UICONTROL Last Name]* de un cliente invitado, lo que provoca que se envíen correos electrónicos de confirmación de pedido no válidos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. El ID del parche es ACSD-61522. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p9

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El sistema permite introducir direcciones de correo electrónico en los campos *[!UICONTROL First Name]* y *[!UICONTROL Last Name]* de un cliente invitado, lo que da como resultado el envío de correos electrónicos de confirmación de pedido no válidos.

<u>Pasos a seguir</u>:

1. Agregue cualquier producto al carro de compras como cliente invitado.
1. Ir a **[!UICONTROL Checkout]**.
1. Rellene el campo *[!UICONTROL Email Address]* con *test1@example.com*.
1. Rellene el campo *[!UICONTROL First Name]* con *<test2@example.com>*.
1. Rellene *[!UICONTROL Last Name]* con *<test3@example.com>*.
1. Rellene otros campos obligatorios.
1. Realice el pedido.

<u>Resultados esperados</u>:

No es posible utilizar direcciones de correo electrónico en los campos *[!UICONTROL First Name]* y *[!UICONTROL Last Name]*.

<u>Resultados reales</u>:

1. Se realiza el pedido.
1. Los campos *[!UICONTROL First Name]* y *[!UICONTROL Last Name]* se guardan como se ingresaron.
1. Los correos electrónicos de confirmación de pedido se envían a los tres correos electrónicos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
