---
title: 'ACSD-61667: mejora el rendimiento del inventario para crear envíos'
description: Aplique el parche ACSD-60584 para mejorar el rendimiento del inventario a fin de crear envíos en caso de que existan muchos orígenes con recogida en tienda.
feature: Customers, Shipping/Delivery
role: Admin, Developer
exl-id: 47682daf-9117-45f1-ab09-a66c13132ff3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-61667: mejora el rendimiento del inventario para crear envíos

La revisión ACSD-61667 corrige el problema en el que el comerciante no puede enviar el pedido cuando la tienda de recogida [[!DNL Inventory Management for Commerce]](https://experienceleague.adobe.com/es/docs/commerce-admin/inventory/introduction) (anteriormente MSI) está habilitada con varias fuentes. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53. El ID del parche es ACSD-61667. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No puede enviar el pedido cuando la tienda de recogida MSI está habilitada, con varias fuentes. Este parche mejora el rendimiento del inventario para crear envíos en caso de que haya muchos orígenes con recogida en tienda.

<u>Requisitos previos:</u>:

Los módulos de inventario de Adobe Commerce están instalados y habilitados.

<u>Pasos a seguir</u>:

1. Cree más de *10* orígenes y habilite sus ubicaciones de recogida.
1. La tienda de recogida está habilitada en **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Crear un gran volumen de pedidos de recogida.
1. Vaya a **[!UICONTROL Admin login]** y seleccione **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL View]**.
1. Filtre y compruebe si hay pedidos pendientes.
1. Haga clic en **[!UICONTROL Ship]**.

<u>Resultados esperados</u>:

La página de envío se carga según lo esperado.

<u>Resultados reales</u>:

Recibe un error de *503 tiempo máximo de ejecución agotado*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
