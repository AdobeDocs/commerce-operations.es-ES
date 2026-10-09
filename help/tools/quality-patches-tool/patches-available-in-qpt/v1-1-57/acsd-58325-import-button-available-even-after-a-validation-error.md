---
title: 'ACSD-58325: botón [!UICONTROL Import] disponible incluso después de un error de validación'
description: Aplique el parche ACSD-58325 para corregir el problema de Adobe Commerce donde el botón [!UICONTROL Import] está disponible incluso después de un error de validación.
feature: Data Import/Export
role: Admin, Developer
exl-id: 551a9ac7-9b7f-49b5-9255-2014c330fb07
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
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
source-wordcount: '306'
ht-degree: 0%
---
# ACSD-58325: botón [!UICONTROL Import] disponible incluso después de un error de validación

La revisión ACSD-58325 corrige el problema en el que el botón **[!UICONTROL Import]** está disponible incluso después de un error de validación. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. El ID del parche es ACSD-58325. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El botón [!UICONTROL Import] está disponible incluso después de un error de validación.

<u>Pasos a seguir</u>:

1. Cree el archivo CSV para la importación de productos con un nombre de imagen incorrecto en el archivo.
1. Cree una importación de producto programada con el archivo CSV creado.
1. Espere hasta que se realice la importación programada.
1. Comprobar [!UICONTROL Last outcome] en la cuadrícula **[!UICONTROL Scheduled Imports/Exports]**.

<u>Resultados esperados</u>:

[!UICONTROL Last outcome] debe ser [!UICONTROL Failed].

<u>Resultados reales</u>:

[!UICONTROL Last outcome] es [!UICONTROL Successful].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
