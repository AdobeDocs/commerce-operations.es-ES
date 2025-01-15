---
title: 'ACSD-62708: [!DNL TinyMCE] 7 tamaño de fuente del editor en el panel de administración muestra PT'
description: Aplique el parche ACSD-62708 para solucionar el problema de Adobe Commerce donde el tamaño de fuente del editor  [!DNL TinyMCE] 7 en el administrador muestra PT y no PX. Ahora, también puede establecer el tamaño de fuente en PX en lugar de PT.
feature: Admin Workspace
role: Admin, Developer
source-git-commit: ecb04a058e858580dfbc7a1edcd319423be9eeaa
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---


# ACSD-62708: [!DNL TinyMCE] 7 tamaño de fuente del editor en el panel de administración muestra PT

El parche ACSD-62708 resuelve el problema por el que el tamaño de fuente del editor [!DNL TinyMCE] 7 en el panel de administración se muestra en formato PT en lugar de PX. Este parche le permite establecer el tamaño de fuente en PX. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. El ID del parche es ACSD-62708. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El editor [!DNL TinyMCE] 7 del panel de administración muestra el tamaño de fuente en PT en lugar de PX.

<u>Pasos a seguir</u>:

1. Abra la página de edición del producto en el panel de administración.
1. Expanda la sección [!UICONTROL Content].
1. Compruebe los controles de fuente en el editor [!DNL TinyMCE].

<u>Resultados esperados</u>:

El tamaño de fuente debe ser PX.

<u>Resultados reales</u>:

El tamaño de fuente es en formato PT.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
