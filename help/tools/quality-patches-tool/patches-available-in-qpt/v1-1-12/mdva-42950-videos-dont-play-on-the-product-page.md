---
title: 'MDVA-42950: Los vídeos no se reproducen en la página de producto'
description: El parche MDVA-42950 soluciona el problema de que los vídeos no se reproducen en la página del producto. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-42950. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Products
role: Admin
exl-id: 61c36dc5-0015-431d-84c1-0726bb310cd6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-42950: Los vídeos no se reproducen en la página de producto

El parche MDVA-42950 soluciona el problema de que los vídeos no se reproducen en la página del producto. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-42950. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los vídeos no se reproducen en la página de producto.

<u>Pasos a seguir</u>:

1. Para configurar la clave de API de YouTube, vaya a **Tiendas** > **Configuración** > **Catálogo** > **Vídeo del producto**.
1. Añada un vídeo de YouTube a cualquier producto simple que tenga configuración principal.
1. Agregar HEADER HTML en Contenido > **Diseño** > **Configuración** > **HTML Head** > **Scripts y hojas de estilo**:

   ```HTML
   <script async="" src="https://www.youtube.com/iframe_api"></script>`
   ```

1. Vaya a la PDP y seleccione la configuración del producto para ver el vídeo en la lista de fotos y vídeos.
1. Intente reproducir el vídeo.

<u>Resultados esperados</u>:

Se está reproduciendo el vídeo.

<u>Resultados reales</u>:

El vídeo no se reproduce.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
