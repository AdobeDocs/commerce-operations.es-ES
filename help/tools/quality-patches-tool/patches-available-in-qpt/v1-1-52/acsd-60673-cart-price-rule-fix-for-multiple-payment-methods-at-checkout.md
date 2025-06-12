---
title: 'ACSD-60673: [!UICONTROL Cart Price Rule] problema corregido para varios métodos de pago al finalizar la compra'
description: Aplique el parche ACSD-60673 para solucionar el problema de Adobe Commerce donde los descuentos de un [!UICONTROL Cart Price Rule] que utilizan una condición de método de pago no siempre aparecen en los totales.
feature: Price Rules
role: Admin, Developer
exl-id: 2fe27959-5e5f-4d25-9f56-b0f8319fd562
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-60673: [!UICONTROL Cart Price Rule] problema corregido para varios métodos de pago al finalizar la compra

El parche ACSD-60673 corrige el problema en el que los descuentos de un(a) [!UICONTROL Cart Price Rule] que utilizan una condición de método de pago no siempre aparecen en los totales. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52. El ID del parche es ACSD-60673. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El [!UICONTROL Cart Price Rule] para múltiples formas de pago al momento del pago no se aplica correctamente al método de pago específico.

<u>Requisitos previos</u>

Asegúrese de que en **[!UICONTROL Multiple Payment Methods]** > **[!UICONTROL Money Order]** y **[!UICONTROL Bank Transfer]** esté habilitado.

<u>Pasos a seguir</u>:

1. Habilitar **[!UICONTROL Multiple Payment Methods]**.
1. Crear un *[!UICONTROL Cart Price Rule]*.
   * Establecer **[!UICONTROL Conditions]** : método de pago a **[!UICONTROL Money Order]** (o transferencia bancaria)
   * Seleccionar **[!UICONTROL Actions]** = *25%* de descuento en todos los productos
1. Cree un producto virtual.
1. Para copiar una cotización nueva y un cliente invitado *[!UICONTROL Status]*, ve a la tienda y borra las cookies.
1. Agregar el producto virtual al carro de compras.
1. Continuar con *cierre de compra*.
1. Haga clic en el método de pago definido en *[!UICONTROL Cart Price Rule]*.
1. Actualice su *[!UICONTROL Billing Address]*.
1. Asegúrese de que el descuento sea visible en el importe total.
1. Pulsa en la casilla de verificación para cambiar la forma de pago.
1. Compruebe que el descuento sea visible.

<u>Resultados esperados</u>:

El descuento se ve en *Totales* después de hacer clic en la casilla de verificación para cambiar a una forma de pago aplicable.

<u>Resultados reales</u>:

El descuento no es visible en *Totales*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
