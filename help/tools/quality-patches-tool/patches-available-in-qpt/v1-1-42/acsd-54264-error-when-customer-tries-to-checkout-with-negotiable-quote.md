---
title: 'ACSD-54264: Error cuando el cliente intenta pagar con un presupuesto negociable'
description: 'Aplique el parche ACSD-54264 para corregir el problema de Adobe Commerce donde aparece un mensaje de error "No puede actualizar el atributo solicitado. ID de fila: "store_id" aparece cuando un cliente intenta realizar una compra con una oferta negociable de otra vista de tienda.'
feature: B2B, Checkout
role: Admin, Developer
exl-id: b1696228-b2ed-44eb-9e75-bf25ccf2f1cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-54264: Aparece un error cuando el cliente intenta pagar con un presupuesto negociable

El parche ACSD-54264 corrige el problema donde un mensaje de error *No se puede actualizar el atributo solicitado. Id. de fila: store_id* aparece cuando un cliente intenta realizar la retirada con una oferta negociable de otra vista de tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42. El ID del parche es ACSD-54264. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Mensaje de error *No se puede actualizar el atributo solicitado. Id. de fila: store_id* aparece cuando un cliente intenta realizar la retirada con una oferta negociable de otra vista de tienda.

<u>Requisitos previos</u>:

Los módulos B2B de Adobe Commerce están instalados y habilitados.

<u>Pasos a seguir</u>:

1. Cree una vista de tienda adicional para el sitio web predeterminado.
1. Habilite *[!UICONTROL B2B Quote]* en la configuración.
1. Inicie sesión como cliente de la empresa en una de las vistas de la tienda.
1. Agregar un producto a *[!UICONTROL Shopping Cart]*.
1. Envíe el presupuesto para su revisión.
1. Como usuario administrador, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** y envíe el presupuesto aprobado.
1. Como cliente de la compañía, cambie la vista de la tienda a otra vista de la tienda.
1. Trate de verificar.

<u>Resultados esperados</u>:

El cliente realiza un pedido con esta oferta.

<u>Resultados reales</u>:

* El error se produce al guardar la información de envío:

  `You cannot update the request attribute. Row ID: store_id =#`

* Se registra el siguiente error:

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
