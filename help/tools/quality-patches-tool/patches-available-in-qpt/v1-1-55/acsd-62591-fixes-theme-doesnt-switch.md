---
title: 'ACSD-62591: el tema no cambia cuando se configura **[!UICONTROL User Agent Rules]**'
description: Aplique el parche ACSD-62591 para corregir el problema de Adobe Commerce en el que el tema no cambia correctamente cuando se configuran los **[!UICONTROL User Agent Rules]**.
feature: Themes
role: Admin, Developer
source-git-commit: 319ac7ea1fb8f33f4ed7bfa440477cf6d6657cb5
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# ACSD-62591: el tema no cambia correctamente cuando se configura [!UICONTROL User Agent Rules]

La revisión ACSD-62591 corrige el problema en el que el tema no cambia correctamente cuando se configuran los **[!UICONTROL User Agent Rules]**. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. El ID del parche es ACSD-62591. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El tema no cambia correctamente cuando se configuran los **[!UICONTROL User Agent Rules]**.

<u>Pasos a seguir</u>:

1. Abra Commerce **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]**.
1. Editar una temática de la vista de tienda.
1. Establezca `/iPhone|iPod|BlackBerry|Palm|Googlebot-Mobile|Mobile|mobile|mobi|Windows Mobile|Safari Mobile|Android|Opera Mini/i` en **[!UICONTROL User Agent Rules]** y elija un tema diferente.
1. Guarde los cambios y borre las cachés.
1. Abra una página de una tienda en un dispositivo móvil.
1. Abra la misma página desde un explorador de escritorio.

<u>Resultados esperados</u>:

El navegador de escritorio y el dispositivo móvil muestran las páginas con sus respectivos temas.

<u>Resultados reales</u>:

El explorador de escritorio muestra la página en caché con la temática móvil.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
