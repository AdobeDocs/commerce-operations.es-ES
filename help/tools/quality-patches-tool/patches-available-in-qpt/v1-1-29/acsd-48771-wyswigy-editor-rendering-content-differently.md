---
title: "ACSD-48771: el editor de WYSIWYG procesa el contenido de forma diferente"
description: Aplique el parche ACSD-48771 para corregir el problema de Adobe Commerce en el que el editor de WYSIWYG procesa el contenido de forma diferente.
feature: Cache, Page Content
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# ACSD-48771: el editor WYSIWYG procesa el contenido de forma diferente

El parche ACSD-48771 corrige el problema en el que el editor de WYSIWYG procesa el contenido de forma diferente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-48771. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El editor de WYSIWYG procesa el contenido de forma diferente.

<u>Pasos a seguir</u>:

1. Vaya al Administrador de Adobe Commerce, cree una nueva página con una fila de tres columnas y guarde la página.
1. Actualice Adobe Commerce a una de las versiones más recientes.
1. Configure el explorador [!DNL Chrome] para deshabilitar la caché y la velocidad a *Fast 3G*.
1. Vuelva a la página de edición y actualícela hasta que las columnas se conviertan en filas.
1. Guarde la página mientras las columnas están en filas.

<u>Resultados esperados</u>:

El generador de páginas de administración no debe mostrar columnas en filas.

<u>Resultados reales</u>:

Las columnas aparecen en filas diferentes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
