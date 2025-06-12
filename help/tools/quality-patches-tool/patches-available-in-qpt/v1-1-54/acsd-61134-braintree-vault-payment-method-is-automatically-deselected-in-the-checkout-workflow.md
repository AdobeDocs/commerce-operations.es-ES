---
title: 'ACSD-61134: [!UICONTROL Braintree Vault] método de pago deseleccionado automáticamente en el flujo de trabajo de cierre de compra'
description: Aplique el parche ACSD-61134 para resolver el problema de Adobe Commerce en el que el método de pago *[!UICONTROL Braintree Vault]* se anula automáticamente en el flujo de trabajo de cierre de compra cuando un comprador actualiza su dirección de facturación anulando la selección de la casilla de verificación *[!UICONTROL My billing and shipping address are the same]*.
feature: Checkout
role: Admin, Developer
exl-id: 8aad34e2-89ef-460c-8921-91098bd1645b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-61134: *[!UICONTROL Braintree Vault]* método de pago deseleccionado automáticamente en el flujo de trabajo de cierre de compra

El parche ACSD-61134 corrige el problema en el que el método de pago *[!UICONTROL Braintree Vault]* se anula automáticamente de la selección en el flujo de trabajo de cierre de compra cuando un comprador actualiza su dirección de facturación anulando la selección de la casilla de verificación *[!UICONTROL My billing and shipping address are the same]*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.54. El ID del parche es ACSD-61134. Tenga en cuenta que este problema está programado para solucionarse en Adobe Commerce 2.4.7-beta1.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6-p7

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El método de pago *[!UICONTROL Braintree Vault]* se deselecciona automáticamente en el flujo de trabajo de cierre de compra.

<u>Pasos a seguir</u>:

1. Configure el método de pago *[!DNL Braintree]* con *[!UICONTROL Vault]* habilitado.
1. Cierre la compra y guarde una tarjeta en *[!UICONTROL Vault]*.
1. Cierre otro producto.
1. En la página *[!UICONTROL Shipping]*, agregue una nueva dirección de envío para que tenga dos direcciones que seleccionar.
1. En la página *[!UICONTROL Payment]*, seleccione la forma de pago y haga clic en **[!UICONTROL My billing and shipping addresses are the same]**.

<u>Resultados esperados</u>:

El método de pago seleccionado permanece seleccionado.

<u>Resultados reales</u>:

El método de pago seleccionado está desmarcado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
