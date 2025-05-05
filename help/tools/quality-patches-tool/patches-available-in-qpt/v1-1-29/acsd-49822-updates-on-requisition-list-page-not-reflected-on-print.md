---
title: 'ACSD-49822: las actualizaciones en la página de lista de solicitudes no se reflejan en la lista de solicitudes de impresión'
description: Aplique el parche ACSD-49822 para solucionar el problema de Adobe Commerce en el que las actualizaciones de la página de lista de solicitudes no se reflejan en la lista de solicitudes de impresión.
feature: Admin Workspace, B2B
role: Admin
exl-id: 053b8900-0900-4b7e-ba1b-ad4b88ca3f35
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-49822: las actualizaciones en la lista de solicitudes no se reflejan en la lista de solicitudes de impresión

El parche ACSD-49822 soluciona el problema en el que las actualizaciones en la página de lista de solicitudes no se reflejan en la lista de solicitudes de impresión. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-49822. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las actualizaciones en la página de lista de solicitudes no se reflejan en la lista de solicitudes de impresión.

<u>Pasos a seguir</u>:

1. Para habilitar la lista de solicitudes, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[Características B2B]**.
1. Cree un producto.
1. Conéctese como cliente y añada dos productos a la lista de solicitudes.
1. Ir a **[!UICONTROL My Account]** > **[!UICONTROL My Requisition Lists]**.
1. Consultar una lista de solicitudes.
1. Haga clic en **[!UICONTROL Print]** en la esquina superior derecha.
1. Cierre la ventana de impresión e imprima la página de lista de solicitudes.
1. Elimine un elemento de la lista o actualice una cantidad de un elemento e intente imprimirlo de nuevo.
1. Observará que los elementos no se actualizan en la ventana de impresión.
1. Cierre la ventana de impresión.
1. Observe que los artículos no se actualizan en la página de impresión de la lista de solicitudes.

<u>Resultados esperados</u>:

La lista que se va a imprimir se actualiza después de aplicar cualquier cambio.

<u>Resultados reales</u>:

Las actualizaciones no se reflejan en la página de impresión de la lista de solicitudes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
