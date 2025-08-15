---
title: 'ACSD-49706: valor predeterminado guardado para el atributo de muestra visual cuando no se selecciona ningún valor'
description: Aplique el parche ACSD-49706 para corregir el problema de Adobe Commerce en el que se guarda un valor predeterminado para un atributo de muestra visual cuando no se selecciona ningún valor.
feature: Admin Workspace, Attributes
role: Admin
exl-id: fa3cb0a1-f898-4826-aa64-efeba1af58a8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-49706: valor predeterminado guardado para el atributo de muestra visual cuando no se selecciona ningún valor

El parche ACSD-49706 corrige el problema en el que se guarda un valor predeterminado para un atributo de muestra visual cuando no se selecciona ningún valor. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-49706. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
