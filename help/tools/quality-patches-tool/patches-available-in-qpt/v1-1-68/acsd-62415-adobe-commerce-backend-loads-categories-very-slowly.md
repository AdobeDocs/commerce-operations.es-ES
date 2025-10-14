---
title: 'ACSD-62415: el servidor de Adobe Commerce carga [!UICONTROL Categories] muy lentamente'
description: Aplique el parche ACSD-62415 para corregir el problema de Adobe Commerce en el que el rendimiento de la página [!UICONTROL Categories] en el panel [!UICONTROL Admin] se carga muy lentamente cuando hay un gran número de categorías de anclaje.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8040414630cf3c992e0d68d5693990f8f50fdbcb
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# ACSD-62415: el servidor de Adobe Commerce carga **[!UICONTROL Categories]** muy lentamente cuando hay categorías de anclaje presentes

La revisión ACSD-62415 corrige el problema en el que el rendimiento de la página **[!UICONTROL Categories]** en el panel **[!UICONTROL Admin]** se carga muy lentamente cuando hay un gran número de categorías de anclaje presentes. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. El ID del parche es ACSD-62415. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La página **[!UICONTROL Categories]** del panel **[!UICONTROL Admin]** se carga muy lentamente cuando hay un gran número de categorías de anclaje.

<u>Pasos a seguir</u>:

1. Generar categorías de anclaje 3K.
1. Abra **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** página en el panel **[!UICONTROL Admin]**.

<u>Resultados esperados</u>:

La página **[!UICONTROL Categories]** se carga rápidamente y la consulta no debería repetirse 1.000 veces.

<u>Resultados reales</u>:

La carga tarda de 7 a 20 segundos y la consulta se ejecuta más de 1000 veces.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
