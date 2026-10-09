---
title: 'ACSD-49706: valor predeterminado guardado para el atributo de muestra visual cuando no se selecciona ningún valor'
description: Aplique el parche ACSD-49706 para corregir el problema de Adobe Commerce en el que se guarda un valor predeterminado para un atributo de muestra visual cuando no se selecciona ningún valor.
feature: Admin Workspace, Attributes
role: Admin
exl-id: fa3cb0a1-f898-4826-aa64-efeba1af58a8
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%
---
# ACSD-49706: valor predeterminado guardado para el atributo de muestra visual cuando no se selecciona ningún valor

El parche ACSD-49706 corrige el problema en el que se guarda un valor predeterminado para un atributo de muestra visual cuando no se selecciona ningún valor. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29. El ID del parche es ACSD-49706. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se guarda un valor predeterminado para un atributo de muestra visual cuando no se selecciona ningún valor.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Haga clic en **[!UICONTROL Add New Attribute]**.
1. Rellene los campos.

   * Por ejemplo, elija el tipo de entrada *[!UICONTROL Visual Swatch]* y agregue varias opciones (como *Rojo*, *Verde*). Asegúrese de elegir una de estas opciones como predeterminada.
   * Haga clic en **[!UICONTROL Save Attribute]**.

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Edite el conjunto de atributos *[!UICONTROL Default]*.
1. Mover *[!UICONTROL New Attribute]* de la columna *[!UICONTROL Unassigned Attributes]* a la carpeta *[!UICONTROL Product Details]* en la columna central.

   * Haga clic en **[!UICONTROL Save]**.

1. Cree un nuevo producto con el conjunto de atributos *[!UICONTROL Default]*.

   * Deje *[!UICONTROL New Attribute]* vacío y guárdelo.

1. Una vez guardado, aparecerá un valor en *[!UICONTROL New Attribute]*.

<u>Resultados esperados</u>:

No se ha asignado ningún valor a *[!UICONTROL New Attribute]* de manera predeterminada.

<u>Resultados reales</u>:

Al guardar un producto, se aplica un valor predeterminado al atributo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
