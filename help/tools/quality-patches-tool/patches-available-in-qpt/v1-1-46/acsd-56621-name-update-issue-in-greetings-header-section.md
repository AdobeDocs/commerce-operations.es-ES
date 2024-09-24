---
title: "ACSD-56621: Los nombres actualizados no se muestran en el encabezado de saludos para el usuario administrador de la empresa"
description: Aplique el parche ACSD-56621 para solucionar el problema de Adobe Commerce donde el nombre y los apellidos actualizados del usuario administrador de la empresa no se reflejan en la sección del encabezado de saludos.
feature: Companies, B2B, User Account
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-56621: los nombres actualizados no se muestran en el encabezado de saludos para el usuario administrador de la empresa

El parche ACSD-56621 corrige el problema en el que el nombre y los apellidos actualizados del usuario administrador de la empresa no se reflejan en la sección del encabezado de saludos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.46. El ID del parche es ACSD-56621. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los nombres actualizados no se muestran en el encabezado de saludos para los usuarios administradores de la empresa.

<u>Pasos a seguir</u>:

1. Vaya al panel **[!UICONTROL Admin]**.
1. Vaya a **[!UICONTROL Stores]** y seleccione **[!UICONTROL Configuration]**.
1. En la sección **[!UICONTROL General]**, seleccione **[!UICONTROL B2B]** para habilitar la funcionalidad de la empresa B2B.
1. Vaya a **[!UICONTROL Storefront]** y registre una nueva compañía.
1. Inicie sesión como usuario administrador de la empresa.
1. Vaya a **[!UICONTROL My Account]** > **[!UICONTROL Company Users]** y modifique los campos de nombre y apellido según sea necesario.

<u>Resultados esperados</u>:

El nombre y los apellidos del usuario en la sección del encabezado de los saludos se cambian inmediatamente.

<u>Resultados reales</u>:

El nombre y los apellidos del usuario solo se cambian cuando este cierra la sesión y vuelve a iniciarla.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
