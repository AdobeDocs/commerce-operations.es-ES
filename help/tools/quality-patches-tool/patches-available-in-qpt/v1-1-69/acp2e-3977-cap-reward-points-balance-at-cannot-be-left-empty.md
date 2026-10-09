---
title: 'ACP2E-3977: El campo [!UICONTROL Cap Reward Points Balance At] no puede dejarse vacío'
description: Aplique el parche ACP2E-3977 para corregir el problema de Adobe Commerce en el que el campo **[!UICONTROL Cap Reward Points Balance At]** no se podía dejar vacío cuando se establecía el campo **[!UICONTROL Rewards Points Balance Redemption Threshold]**, lo que provocaba un error de validación.
feature: Configuration, Rewards
role: Admin, Developer
type: Troubleshooting
exl-id: 5275911f-4f8c-4b37-af11-24ceb69406c9
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4069cee6-4dc8-5a83-81de-232af6a7c9e9
    internal-label: Rewards
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
source-wordcount: '323'
ht-degree: 0%
---
# ACP2E-3977: El campo **[!UICONTROL Cap Reward Points Balance At]** no puede dejarse vacío

El parche ACP2E-3977 corrige el problema en el que el campo **[!UICONTROL Cap Reward Points Balance At]** no se puede dejar vacío, aunque se deba permitir. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACP2E-3977. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p10

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Dejar **[!UICONTROL Cap Reward Points Balance At]** déclencheur vacíos es un error de validación, aunque debería deshabilitar el límite si se deja en blanco.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward points]**.
1. Conjunto **[!UICONTROL Rewards Points Balance Redemption Threshold]** = *30*.
1. Dejar **[!UICONTROL Cap Reward Points Balance At]** vacío.
1. Guardar.

<u>Resultados esperados</u>:

Se permite un valor vacío para **[!UICONTROL Cap Reward Points Balance At]** y se deshabilita la limitación.

<u>Resultados reales</u>:

*El saldo de puntos de recompensa de límite no es válido. El saldo debe ser un número positivo o dejarse vacío. Verificar y volver a intentarlo.* se muestra el error.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
