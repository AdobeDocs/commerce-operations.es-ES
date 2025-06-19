---
title: 'ACSD-52606: mensaje de error que se muestra cuando el usuario hace clic en "Notificar pedido está listo para su recogida"'
description: Aplique el parche ACSD-52606 para solucionar el problema de Adobe Commerce donde se muestra un mensaje de error cuando el usuario hace clic en **[!UICONTROL Notify Order is Ready for Pickup]**.
feature: Orders, User Account
role: Admin, Developer
exl-id: d0b5a7a6-0d32-4019-8f28-60722fce1a99
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-52606: mensaje de error que se muestra cuando el usuario hace clic en &quot;Notificar pedido está listo para su recogida&quot;

La revisión ACSD-52606 corrige el problema en el que se muestra un mensaje de error *Su pedido no está listo para ser recogido* cuando el usuario hace clic en **[!UICONTROL Notify Order is Ready for Pickup]**. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.37. El ID del parche es ACSD-52606. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se muestra un mensaje de error *Su pedido no está listo para su recogida* en la pantalla cuando el usuario hace clic en **[!UICONTROL Notify Order is Ready for Pickup]**.

<u>Requisitos previos</u>:

Los módulos de inventario están instalados.

<u>Pasos a seguir</u>:

1. Instale una instancia nueva.
1. Crear un nuevo origen y stock.
1. Asigne el nuevo origen al sitio web predeterminado.
1. Habilite la ubicación de recogida para el origen recién creado.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** y habilite **[!UICONTROL In-Store Delivery]**.
1. Cree un producto simple de *En existencia* con *CANT=0* para todos los inventarios y *[!UICONTROL Manage Stock = No]* y asígnelo a ambos orígenes.
1. Cree un pedido desde el front-end con el producto creado en el paso anterior, eligiendo *[!UICONTROL In-Store Pickup]* como método de entrega.
1. En Administración, vaya a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**.
1. Haga clic en **[!UICONTROL Notify order is ready for pickup]**.

<u>Resultados esperados</u>:

Se le notificará sin errores.

<u>Resultados reales</u>:

Recibe el siguiente mensaje de error: *Su pedido no está listo para su recogida*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
