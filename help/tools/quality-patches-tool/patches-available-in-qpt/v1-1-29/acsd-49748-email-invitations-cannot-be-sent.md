---
title: 'ACSD-49748: no se pueden enviar invitaciones por correo electrónico'
description: Aplique el parche ACSD-49748 para solucionar el problema de Adobe Commerce en el que los usuarios no pueden enviar invitaciones por correo electrónico.
feature: Admin Workspace, Communications, Marketing Tools
role: Admin
exl-id: 03dad66c-4691-421e-8c80-eca12c60175c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---

# ACSD-49748: no se pueden enviar invitaciones por correo electrónico

El parche ACSD-49748 corrige el problema en el que los usuarios no pueden enviar invitaciones por correo electrónico. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-49748. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Aparece el error *Se produjo un error al enviar invitaciones* al enviar invitaciones.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Admin Panel]** > **[!UICONTROL Marketing]** > **[!UICONTROL Private Sales]** > **[!UICONTROL Invitations]**.
1. Cree una invitación y guárdela.
1. Vaya a **[!UICONTROL Invitation Grid]** y seleccione cualquier invitación.
1. Envíe la invitación.

<u>Resultados esperados</u>:

Se envía una invitación al hacer clic en *[!UICONTROL Send Invitation]*.

<u>Resultados reales</u>:

Aparece el error *Se produjo un error al enviar invitaciones* y no se envía la invitación.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].
