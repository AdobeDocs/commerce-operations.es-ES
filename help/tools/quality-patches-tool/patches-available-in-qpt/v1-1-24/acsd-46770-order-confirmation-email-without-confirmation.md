---
title: 'ACSD-46770: el correo electrónico de confirmación de pedido se envía incluso cuando [!UICONTROL Email Order Confirmation] está desmarcado'
description: Aplique el parche ACSD-46770 para corregir el problema de Adobe Commerce donde se envían correos electrónicos de confirmación de pedido incluso cuando [!UICONTROL Email Order Confirmation] no está seleccionado.
feature: Communications, Orders
role: Admin
exl-id: d25ca121-7551-417c-b598-d8ed3a3da969
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%
---
# ACSD-46770: el correo electrónico de confirmación de pedido se envía incluso cuando **[!UICONTROL Email Order Confirmation]** está desmarcado

El parche ACSD-46770 corrige el problema en el cual los pedidos se pueden realizar mediante la API de REST como usuario invitado incluso cuando **[!UICONTROL Email Order Confirmation]** no está seleccionado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24. El ID del parche es ACSD-46770. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se envía un correo electrónico de confirmación de pedido aunque **[!UICONTROL Email Order Confirmation]** no esté seleccionado.

<u>Pasos a seguir</u>:

1. Cree una cuenta de cliente.
1. Vaya a **[!UICONTROL Sales]** > **[!UICONTROL Order]** y haga clic en **[!UICONTROL Create New Order]**.
1. Seleccione el cliente, añada los productos al pedido, rellene la dirección y seleccione los métodos de envío y pago.
1. Antes de enviar el pedido, anule la selección de la casilla **[!UICONTROL Email Order confirmation]**.
1. Haga clic en **[!UICONTROL Submit Order]** para crear el pedido.

<u>Resultados esperados</u>:

No se debe enviar un correo electrónico de confirmación de pedido si se deselecciona **[!UICONTROL Email Order Confirmation]**.

<u>Resultados reales</u>:

Se enviará un correo electrónico de confirmación de pedido independientemente de la casilla de verificación **[!UICONTROL Email Order Confirmation]** sin seleccionar.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
