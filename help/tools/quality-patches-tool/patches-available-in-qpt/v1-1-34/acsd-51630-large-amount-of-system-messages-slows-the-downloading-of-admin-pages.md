---
title: 'ACSD-51630: Numerosos mensajes del sistema ralentizan la descarga de las páginas de administración'
description: Aplique el parche ACSD-51630 para solucionar el problema de rendimiento de Adobe Commerce, donde una gran cantidad de mensajes del sistema ralentiza la descarga de las páginas de administración.
feature: Admin Workspace, System
role: Admin
exl-id: 8f39afea-551a-4306-994a-cb8ce5bd5b4a
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-51630: Numerosos mensajes del sistema ralentizan la descarga de las páginas de administración

El parche ACSD-51630 corrige el problema de rendimiento en el que una gran cantidad de mensajes del sistema ralentiza la descarga de las páginas de administración. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.34. El ID del parche es ACSD-51630. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 &lt; 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Numerosos mensajes del sistema ralentizan la descarga de las páginas de administración

<u>Pasos a seguir</u>:

1. Realice una gran cantidad de solicitudes (~50.000) al DELETE `/rest/async/v1/products/ {sku}`.
1. Acceda a cualquier **página de administración**.

<u>Resultados esperados</u>:

La página se carga en un momento adecuado. Solo se deben cargar los mensajes que se muestran.

<u>Resultados reales</u>:

La página tarda demasiado en cargarse. Todos los mensajes existentes se cargan desde la base de datos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
