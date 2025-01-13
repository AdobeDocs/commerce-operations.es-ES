---
title: 'ACSD-62689: no se pueden agregar categorías en [!UICONTROL Related Product Rules] y widgets después de la profundidad 4'
description: Aplique el parche ACSD-62689 para corregir el problema de Adobe Commerce en el que un cliente no puede agregar categorías en [!UICONTROL Related Product Rules] y widgets después del anidamiento de profundidad cuatro.
feature: Categories
role: Admin, Developer
source-git-commit: 154a017fbc6e069e8e59651db46955922c004955
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# ACSD-62689: no se pueden agregar categorías en *[!UICONTROL Related Product Rules]* y widgets después de la profundidad 4

La revisión ACSD-62689 corrige el problema en el cual un cliente no puede agregar categorías en *[!UICONTROL Related Product Rules]* y widgets después del anidamiento de profundidad cuatro. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/patches/release-notes.html) 1.1.57. El ID del parche es ACSD-62689. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un cliente no puede agregar categorías en *[!UICONTROL Related Product Rules]* y widgets después de anidar en profundidad cuatro.

<u>Pasos a seguir</u>:

1. Cree dos categorías con los nombres *[!UICONTROL Anchor]* y *[!UICONTROL Non-Anchor]* en la categoría raíz predeterminada.
   * Asegúrese de que el indicador *[!UICONTROL Is Anchor]* esté deshabilitado para la categoría *[!UICONTROL Non-Anchor]*.
1. Vaya a **[!UICONTROL Content]** > **[!UICONTROL Widgets]** y cree un widget.
1. En *[!UICONTROL Layout Updates]*, seleccione **[!UICONTROL Non-Anchor Categories]** en el campo *[!UICONTROL Display on]*.
1. Haga clic en **[!UICONTROL Specific Categories]**.
1. Haga clic en el icono de selección de categoría.
1. Expanda la categoría raíz.
1. Compruebe las categorías. Ambos deben deshabilitarse y no seleccionarse.
1. En *[!UICONTROL Layout Updates]*, seleccione **[!UICONTROL Anchor Categories]** en el campo *[!UICONTROL Display on]*. A continuación, siga los pasos 5 y 6.
1. Compruebe las categorías. Ambos deben estar activados y seleccionables.

<u>Resultados esperados</u>:

En el paso 7, solo se debe poder seleccionar la categoría *[!UICONTROL Non-Anchor]*. En el paso 9, la categoría *[!UICONTROL Anchor]* debe ser seleccionable.

<u>Resultados reales</u>:

En el paso 7, ambas categorías no se pueden seleccionar. En el paso 9, ambas categorías son seleccionables.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
