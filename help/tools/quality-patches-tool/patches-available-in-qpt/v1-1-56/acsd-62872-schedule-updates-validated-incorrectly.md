---
title: 'ACSD-62872: programar actualizaciones validadas incorrectamente'
description: Aplique el parche ACSD-62872 para corregir el problema de Adobe Commerce con validación de atributos únicos en el que las actualizaciones programadas se validan incorrectamente.
feature: Catalog Management, Admin Workspace
role: Admin, Developer
source-git-commit: f734dab2316237d60164a430eeabed17782b0ae6
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-62872: programar actualizaciones validadas incorrectamente

El parche ACSD-62872 corrige el problema de validación de atributos únicos en el que las actualizaciones programadas se validan incorrectamente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. El ID del parche es ACSD-62872. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La actualización programada para un atributo personalizado se ha validado incorrectamente.

<u>Pasos a seguir</u>:

1. Cree un atributo personalizado para las categorías.
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Cree una nueva categoría.
1. En la misma categoría, vaya a la sección **[!UICONTROL Scheduled Updates]**.
1. Configure una nueva actualización para esta categoría en cualquier momento futuro.
1. Antes de iniciar la actualización programada, intente editar la actualización de programación creada para la categoría.

<u>Resultados esperados</u>:

Debe poder actualizar la actualización programada.

<u>Resultados reales</u>:

Se genera un error: *El valor del atributo &quot;Atributo personalizado&quot; no es único. Establezca un valor único e inténtelo de nuevo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
