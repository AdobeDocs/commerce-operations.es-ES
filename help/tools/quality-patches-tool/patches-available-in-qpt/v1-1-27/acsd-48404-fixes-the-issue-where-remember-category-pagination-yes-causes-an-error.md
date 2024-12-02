---
title: 'ACSD-48404: *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* provoca un error al pulsar el botón Atrás del explorador'
description: Aplique el parche ACSD-48404 para solucionar el problema de Adobe Commerce donde *[!UICONTROL Remember Category Pagination] = [!UICONTROL Yes]* provoca un error al pulsar el botón Atrás del explorador.
feature: Categories
role: Admin
exl-id: 8c08f0e2-d4f9-4ac8-b8e8-85b4a7de98fb
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-48404: *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* causa un error al pulsar el botón Atrás del explorador

La revisión ACSD-48404 corrige el problema donde *[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* causa un error al presionar el botón Atrás del explorador. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.27. El ID del parche es ACSD-48404. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

*[!UICONTROL Remember Category Pagination]=[!UICONTROL Yes]* provoca un error al pulsar el botón Atrás del explorador.


<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Storefront]** y establezca *[!UICONTROL Remember Category Pagination]* en *Sí*.
1. Abre una categoría en la tienda.
1. Seleccione un valor que no sea el valor predeterminado en la lista desplegable *[!UICONTROL Show Per Page]*. Después de seleccionar una opción, la página se vuelve a cargar.
1. Una vez que la página se haya recargado, haga clic en cualquier producto de la página del catálogo.
1. En la página de detalles del producto abierta, haga clic en el botón **[!UICONTROL Back]** del explorador.

<u>Resultados esperados</u>:

Se vuelve a abrir la página del catálogo.

<u>Resultados reales</u>:

La página de categoría devuelve un error.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
