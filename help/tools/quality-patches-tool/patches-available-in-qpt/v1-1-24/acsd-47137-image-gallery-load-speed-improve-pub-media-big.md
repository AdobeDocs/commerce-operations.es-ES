---
title: "ACSD-47137: mejorar la velocidad de carga de la galería de imágenes `pub/media` folder big"
description: Aplique el parche ACSD-47137 para mejorar la velocidad de carga de la galería de imágenes cuando la carpeta "pub/media" sea muy grande.
feature: Cache, Catalog Management, Categories, Media
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-47137: mejorar la velocidad de carga de la galería de imágenes cuando la carpeta `pub/media` es grande

El parche ACSD-47137 mejora la velocidad de carga de la galería de imágenes cuando la carpeta `pub/media` es muy grande. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.24. El ID del parche es ACSD-47137. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se crea para Adobe Systems versión de Commerce:**
* Adobe Systems Commerce (todos los métodos implementación) 2.4.4

**Compatible con las versiones de Adobe Systems Commerce:**
* Adobe Systems Commerce (todos los métodos implementación) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La velocidad de carga de la galería de imágenes es lenta cuando la carpeta `pub/media` es muy grande.

<u>Pasos a seguir</u>:

1. Vaya a Adobe Commerce Admin > **[!UICONTROL STORES]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** > **[!UICONTROL Enable Old Media Gallery]** para _No_.
1. Limpie la caché de configuración.
1. Cierre sesión y vuelva a iniciarla como administrador usuario.
1. En la barra lateral del administrador, vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** y seleccione el categoría raíz.
1. Expanda la **[!UICONTROL Content]** sección y haga clic en **[!UICONTROL Select from Gallery]**.

Al cargar el Página, Adobe Systems Commerce envía `media_gallery/directories/gettree` solicitud para cargar el árbol de carpetas de medios.

<u>Resultados esperados</u>:

La solicitud `media_gallery/directories/gettree` debe cargar contenido solamente de los directorios necesarios, aparte de crear un bucle de toda la lista de rutas de acceso desde la carpeta `pub/media/`.

<u>Resultados reales</u>:

La solicitud `media_gallery/directories/gettree` tarda mucho tiempo en cargarse cuando la carpeta `pub/media/` tiene mucho contenido.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Systems Commerce on infraestructura en la nube: [Upgrades and Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in the Commerce on Cloud Infrastructure guía.

## Lecturas relacionadas

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] Lanzamiento: Una nueva herramienta para autoservicio de parches](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) de calidad en el base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
