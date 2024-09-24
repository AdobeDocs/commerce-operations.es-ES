---
title: "ACSD-47336: error [!UICONTROL Something went wrong] al descartar las notificaciones en el administrador de Adobe Commerce"
description: Aplique el parche ACSD-47336 para solucionar el problema de Adobe Commerce en el que el usuario ve el error [!UICONTROL Something went wrong] al descartar las notificaciones en el administrador  [!DNL Commerce] Admin.
feature: Admin Workspace
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-47336: error _[!UICONTROL Something went wrong]_al descartar las notificaciones en el administrador de Adobe Commerce

El parche ACSD-47336 corrige el problema en el que el usuario ve el error _[!UICONTROL Something went wrong]_al descartar las notificaciones en el administrador de [!DNL Commerce]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24. El ID del parche es ACSD-47336. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación): 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario ve un error de _[!UICONTROL Something went wrong]_al descartar las notificaciones en el administrador de [!DNL Commerce].

<u>Pasos a seguir</u>:

1. Realice una operación por lotes (por ejemplo, una actualización por lotes de los atributos de producto de la cuadrícula de productos).
1. Complete la operación (por ejemplo, ejecute `bin/magento queue:consumer:start product_action_attribute.update`).
1. Actualice la página de administración [!DNL Commerce], expanda la sección de notificaciones de administración y haga clic en el vínculo **[!UICONTROL Dismiss All Completed Tasks]**.

<u>Resultados esperados</u>:

El error _[!UICONTROL Something went wrong]_no debería mostrarse al borrar las tareas completadas.

<u>Resultados reales</u>:

Se muestra el error _[!UICONTROL Something went wrong]_.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
