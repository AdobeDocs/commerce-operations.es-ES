---
title: 'ACSD-45849: los metadatos de vídeo se pierden tras la actualización del ensayo'
description: El parche ACSD-45849 corrige el problema de pérdida de metadatos de vídeo después de aplicar una actualización de ensayo. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18. El ID del parche es ACSD-45849. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.4.
feature: Staging, Page Content
role: Admin
exl-id: cbab0120-585a-47ef-8ed9-abb2da1ec3d6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-45849: los metadatos de vídeo se pierden tras la actualización del ensayo

El parche ACSD-45849 corrige el problema de pérdida de metadatos de vídeo después de aplicar una actualización de ensayo. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18. El ID del parche es ACSD-45849. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los metadatos de vídeo se pierden después de aplicar una actualización de ensayo.

<u>Pasos a seguir</u>:

1. Configure la clave de API de YouTube en **Administración** > **Tiendas** > **Configuración** > **Catálogo** > **Vídeo del producto**.
1. Cree un producto con un vídeo de YouTube. Tenga en cuenta que se han rellenado la dirección URL, el título y la descripción.
1. Cree una nueva actualización programada para el producto con cualquier parámetro sin cambiar la sección *Imágenes y vídeo*.
1. Haz clic en **Ver/Editar** en Cambios programados.
1. Vaya a **Imágenes y vídeos** y haga clic en el vídeo.

<u>Resultados esperados</u>:

La dirección URL, el título y la descripción contienen los datos adecuados.

<u>Resultados reales</u>:

Los campos URL, title y description están vacíos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
