---
title: 'ACSD-58375: La clave de API de YouTube configurada incorrectamente provoca un error al añadir vídeo en el nivel de vista de tienda'
description: Aplique el parche ACSD-58375 para solucionar el problema de Adobe Commerce donde una configuración incorrecta de la clave de API de YouTube provoca un error al añadir un vídeo de YouTube en el nivel de vista de tienda.
feature: Catalog Management, Configuration
role: Admin, Developer
exl-id: 24187308-d9dc-4ce2-9cfa-70ccb7726a5b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%
---
# ACSD-58735: La clave de API de YouTube configurada incorrectamente provoca un error al añadir vídeo en el nivel de vista de tienda

El parche ACSD-58735 corrige el problema en el que una configuración incorrecta de la clave de API de YouTube provoca un error al añadir un vídeo de YouTube en el nivel de vista de tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.49. El ID del parche es ACSD-58735. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Una configuración incorrecta de la clave de API de YouTube provoca un error al añadir un vídeo de YouTube en el nivel de vista de tienda.

<u>Pasos a seguir</u>:

1. Vaya a Administración > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Video]**.
1. Cambiar el *ámbito* al nivel *[!UICONTROL Main Website]*.
1. Añada la clave de API de YouTube.
1. Ir a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Seleccione cualquier producto y desplácese hasta *[!UICONTROL Images and Video]*. Haga clic en **[!UICONTROL Add Video]**.
1. Copie un vínculo de vídeo de YouTube y péguelo en el campo Video Link. Salga del campo.

<u>Resultados esperados</u>:

La clave de la API de YouTube tiene un ámbito global y está oculta en el nivel de sitio web.

<u>Resultados reales</u>:

Se genera el siguiente error: *No se muestra el vídeo debido al siguiente motivo: La clave de API no es válida. Pase una clave de API válida*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
