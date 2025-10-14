---
title: 'ACSD-54067: el vídeo del producto no se reproduce en el dispositivo móvil'
description: Aplique el parche ACSD-54067 para corregir el problema de Adobe Commerce en el que un vídeo del producto no se reproduce en un dispositivo móvil.
feature: Media, Products
role: Admin, Developer
exl-id: 023e7cf7-c344-4e86-850d-741b85df87a9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# ACSD-54067: El vídeo del producto no se reproduce en un dispositivo móvil

El parche ACSD-54067 soluciona el problema de que el vídeo de un producto no se reproduce en un dispositivo móvil. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41. El ID del parche es ACSD-54067. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El vídeo de un producto no se reproduce en un dispositivo móvil.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce.
1. Ejecute el comando:
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Vaya a la página **[!UICONTROL Admin product list]** y filtre por *[!UICONTROL SKU product_dynamic_120]*.
1. Abra la página del producto y vaya a **[!UICONTROL Images and Videos]** > y agregue un vídeo > complete la URL: https://vimeo.com/347119375 y guarde los cambios.
1. Vaya a la tienda y abra la página de producto de *[!UICONTROL product_dynamic_120]*.
1. Establezca el explorador en *dispositivo móvil* con una anchura de *320 px* y actualice.
1. En el deslizador de la galería, seleccione el vídeo y haga clic en para reproducirlo.

<u>Resultados esperados</u>:

Se reproduce el vídeo del producto.

<u>Resultados reales</u>:

El vídeo del producto no se reproduce.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
