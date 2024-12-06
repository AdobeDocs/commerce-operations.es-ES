---
title: 'ACSD-58685: los correos electrónicos de ventas desactivados se envían al volver a habilitar'
description: Aplique el parche ACSD-58685 para solucionar el problema de Adobe Commerce donde los correos electrónicos de ventas iniciados mientras la comunicación por correo electrónico está desactivada se envían una vez que se vuelve a habilitar la comunicación por correo electrónico.
feature: Configuration
role: Admin, Developer
source-git-commit: db495f2dbf307f9da42b6dc4fc7bed1e6af1d307
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-58685: los correos electrónicos de ventas desactivados se envían al volver a habilitar

El parche ACSD-58685 corrige el problema en el que los correos electrónicos de ventas iniciados mientras la comunicación por correo electrónico está desactivada se envían una vez que se vuelve a habilitar la comunicación por correo electrónico. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. El ID del parche es ACSD-58685. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los correos electrónicos de ventas iniciados mientras la comunicación por correo electrónico está desactivada se envían una vez que se vuelve a habilitar la comunicación por correo electrónico.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Mail Sending Settings]** y establezca **[!UICONTROL Disable Email Communications]** en *[!UICONTROL No]*.
1. Vaya a **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales Emails]** > **[!UICONTROL General Settings]** y establezca **[!UICONTROL Asynchronous Sending]** en *[!UICONTROL Yes]*.
1. Borre la caché de configuración.
1. Haga un pedido.
1. Habilitar comunicación por correo electrónico.
1. Realice otro pedido.
1. Corre el cron.

<u>Resultados esperados</u>:

Solo se envía el correo electrónico del segundo pedido.

<u>Resultados reales</u>:

Se envían correos electrónicos para el primer y el segundo pedido.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

[[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
