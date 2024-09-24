---
title: "ACSD-53643: El pedido tiene un total incorrecto al realizar un pedido de compra"
description: Aplique el parche ACSD-53643 para solucionar el problema de Adobe Commerce en el que el pedido tiene un total incorrecto al realizar un pedido de compra con productos desactivados o sin existencias.
feature: B2B
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-53643: el pedido tiene un total incorrecto al realizar un pedido de compra

El parche ACSD-53643 corrige el problema en el que el pedido tiene un total incorrecto al realizar un pedido de compra con productos desactivados o sin existencias. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41. El ID del parche es ACSD-53643. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El total del pedido es incorrecto al realizar un pedido de compra con productos desactivados o sin existencias.

<u>Pasos a seguir</u>:

1. Instalar *[!UICONTROL B2B]* y *[!UICONTROL Inventory]*.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** y establezca **[!UICONTROL Company]** = *Sí* y **[!UICONTROL Purchase Order]** = *Sí*.
1. Borre la caché de configuración.
1. Cree una nueva compañía, actívela y habilite *[!UICONTROL Purchase order]* para la compañía.
1. Cree un nuevo usuario para la compañía.
1. Cree una *regla de aprobación* para aprobar todos los pedidos de más de *1 USD* por parte del administrador de la compañía.
1. Cree una fuente adicional.
1. Inicie sesión como el nuevo usuario de la empresa.
1. Añada dos productos al carro de compras y realice un pedido de compra.
1. Deshabilite el segundo producto.
1. Inicie sesión como administrador de la empresa.
1. Abra el pedido de compra y compruebe que el pedido contiene ambos productos y que el total es para ambos.
1. Apruebe el pedido de compra.
1. Realice el pedido.
1. Abra los detalles del pedido.

<u>Resultados esperados</u>:

* No se puede realizar el pedido aunque un producto del pedido esté *deshabilitado* o *agotado*.
* El botón *[!UICONTROL Place Order]* está oculto.

<u>Resultados reales</u>:

El pedido realizado contiene únicamente el primer producto activo, pero el total del pedido se calcula para ambos productos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
