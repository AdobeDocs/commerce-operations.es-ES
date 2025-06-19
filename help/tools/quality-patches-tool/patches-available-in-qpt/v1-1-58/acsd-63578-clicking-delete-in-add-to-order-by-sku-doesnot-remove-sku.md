---
title: 'ACSD-63578: al hacer clic en el icono [!UICONTROL Delete] en [!UICONTROL Add to Order by SKU], no se elimina la SKU'
description: Aplique el parche ACSD-63578 para solucionar el problema de Adobe Commerce en el que al hacer clic en el icono [!UICONTROL Delete] en [!UICONTROL Add to Order by SKU] en el Administrador no se elimina el SKU.
feature: Orders
role: Admin, Developer
exl-id: 12afceb5-db3c-4783-a532-93c4c71f05f4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-63578: al hacer clic en el icono **[!UICONTROL Delete]** en *[!UICONTROL Add to Order by SKU]*, no se elimina la SKU

La revisión ACSD-63578 corrige el problema que causa que al hacer clic en el icono **[!UICONTROL Delete]** en *[!UICONTROL Add to Order by SKU]* en el Administrador no se elimine la SKU. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. El ID del parche es ACSD-63578. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p7

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al hacer clic en el icono **[!UICONTROL Delete]** en *[!UICONTROL Add to Order by SKU]* en el Administrador, no se elimina el SKU del pedido.

<u>Pasos a seguir</u>:

1. Vaya a Administración > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** y haga clic en **[!UICONTROL Create New Order]**.
1. Elija un cliente.
1. Haga clic en **[!UICONTROL Add to Order by SKU]**.
   * Introduzca un SKU.
   * Haga clic en el botón **[!UICONTROL Add another]**.
1. Haga clic en el icono **[!UICONTROL Delete]**.

<u>Resultados esperados</u>:

* Los productos se añaden y eliminan de un pedido en Admin.

<u>Resultados reales</u>:

* El icono **[!UICONTROL Delete]** no funciona.
* Hay un error en la consola:

  `jquery.js:130 Refused to execute inline script because it violates the following Content Security Policy directive`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
