---
title: 'ACSD-62670: la exportación de [!UICONTROL Ordered Products Report] a CSV y XML devuelve el error 404'
description: Aplique el parche ACSD-62670 para solucionar el problema de Adobe Commerce en el que la exportación de [!UICONTROL Ordered Products Report] a CSV y XML genera un error.
feature: Reporting, Admin Workspace, Data Import/Export
role: Admin, Developer
exl-id: 99d77ddd-4fb3-4eda-8771-62c0e25f49d1
type: Troubleshooting
source-git-commit: 3469da56c15499de4ceb5313c3cc2dfde0f0771c
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# ACSD-62670: error al exportar *[!UICONTROL Ordered Products Report]* a CSV y XML

La revisión ACSD-62670 corrige el problema en el cual la exportación de *[!UICONTROL Ordered Products Report]* a CSV y XML genera un error. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) 1.1.56. El ID del parche es ACSD-62670. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La exportación de *[!UICONTROL Ordered Products Report]* a CSV y XML genera un error.

<u>Pasos a seguir</u>:

1. Vaya al panel *Admin* y vaya a **[!UICONTROL Reports]** > **[!UICONTROL Products]** > **[!UICONTROL Ordered]**.
1. Intente exportar archivos CSV o de Excel.

<u>Resultados esperados</u>:

Los informes se exportan sin errores.

<u>Resultados reales</u>:

La exportación de *[!UICONTROL Ordered Products Report]* genera el error 404.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
