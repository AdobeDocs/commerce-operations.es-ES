---
title: "ACSD-51149: Programado [!UICONTROL ImportExport] con [!UICONTROL Catalog Permissions] habilitado invalida los indizadores"
description: Aplique el parche ACSD-51149 para corregir el problema de rendimiento de Adobe Commerce en el que el [!UICONTROL ImportExport] programado con [!UICONTROL Catalog Permissions] habilitado invalida los indizadores.
feature: Cache, Data Import/Export
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-51149: programado [!UICONTROL ImportExport] con [!UICONTROL Catalog Permissions] habilitado invalida los indizadores

El parche ACSD-51149 corrige el problema en el que el [!UICONTROL ImportExport] programado con [!UICONTROL Catalog Permissions] habilitado invalida los indizadores. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.35. El ID del parche es ACSD-51149. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Programado [!UICONTROL ImportExport] con [!UICONTROL Catalog Permissions] habilitado invalida los indizadores.

<u>Pasos a seguir</u>:

1. Habilitar *[!UICONTROL Catalog Permissions]*.
1. Establezca todos los indizadores en *[!UICONTROL Update by Schedule]*.
1. Cree un producto sencillo.
1. Exporte este producto a través de **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]**.
1. Descargue el CSV exportado y colóquelo en `<AC root folder>/var/import`.
1. Cree una importación de producto programada con el CSV descargado.
1. Ejecutar reindexación completa.
1. Compruebe el estado de los indexadores. Todos los indexadores deben estar en estado *[!UICONTROL Ready]*.
1. Ejecute la importación programada creada desde la cuadrícula.
1. Vuelva a comprobar el estado de los indexadores.

<u>Resultados esperados</u>:

Todos los indizadores están en estado *[!UICONTROL Ready]*.

<u>Resultados reales</u>:

Algunos de los indizadores se encuentran en estado *[!UICONTROL Reindex Required]*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
