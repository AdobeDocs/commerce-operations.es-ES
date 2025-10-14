---
title: 'ACSD-46683: El precio de envío se muestra *Aún no se ha calculado*'
description: Aplique el parche ACSD-46683 para solucionar el problema de Adobe Commerce donde el precio de envío indica *Aún no se ha calculado*.
feature: Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ebd79187-2835-403b-945d-80ac34d6fb9c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# ACSD-46683: el precio de envío muestra *Aún no se ha calculado*

El parche ACSD-46683 corrige el problema donde el precio de envío muestra *Aún no se ha calculado*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30. El ID del parche es ACSD-46683. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El precio de envío muestra *No calculado* todavía.

<u>Requisitos previos</u>:

Los módulos de Adobe Commerce Inventory management (MSI) están instalados.

<u>Pasos a seguir</u>:

1. Cree un producto simple y establezca su precio en *$34*.
1. Configure el método de envío gratuito.
1. Configure al menos un método de envío más.
1. Vaya a **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** y cree una regla nueva:
   * Nombre = *75more*
   * Cupón = Ninguno
   * Prioridad = 1
   * Condiciones: El subtotal es igual o mayor que *$75*
   * Acciones:
      * Aplicar al importe de envío = Sí
      * Descartar reglas subsiguientes = No
      * Envío gratuito = para envíos con artículos coincidentes
1. Crear otra regla de precios de carro de compras:
   * Nombre = *35off*
   * Prioridad = 0
   * Coupon = Specific Coupon
   * Código de cupón = 35off
   * Acciones:
      * Aplicar = Porcentaje de descuento en el precio del producto
      * Importe de descuento = 35
      * Aplicar al importe de envío = No
      * Descartar reglas subsiguientes = Sí
      * Envío gratuito = No
1. Abra la tienda y añada tres productos al carro de compras para que el subtotal supere los 75 $.
1. Continúe con el pago y envío como invitado.
1. En el paso de envío, selecciona **$0 - envío gratuito** y continúa con el paso de pago.
1. Marque [!UICONTROL Order Summary] en el paso de pago. Muestra *[!UICONTROL $0 - Free Shipping - Free]*.
1. Si se aplica el código de cupón *35off*, se actualizará el subtotal y se reducirá a 75 $.
1. Marque [!UICONTROL Order Summary] en el paso de pago.

<u>Resultados esperados</u>:

Se muestra el siguiente mensaje: *El método de envío seleccionado no está disponible. Seleccione otra forma de envío para este pedido.*

<u>Resultados reales</u>:

El precio de envío muestra *Aún no se ha calculado*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
