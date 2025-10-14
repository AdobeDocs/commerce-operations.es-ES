---
title: 'ACSD-62758: problema de procesamiento de vídeo resuelto en páginas de producto configurables'
description: Aplique el parche ACSD-62758 para corregir el problema de Adobe Commerce en el que los vídeos de producto en páginas de detalles de producto configurables no se representan correctamente cuando las direcciones URL contienen opciones de muestra preseleccionadas.
feature: Catalog Management
role: Admin, Developer
exl-id: 084b497d-4471-4458-bc1d-2a452bfe2662
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-62758: problema de procesamiento de vídeo resuelto en páginas de producto configurables

El parche ACSD-62758 corrige el problema de que los vídeos de productos en páginas de detalles de productos configurables no se representan correctamente cuando las direcciones URL contienen opciones de muestra preseleccionadas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. El ID del parche es ACSD-62758. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los vídeos de producto no se representan correctamente en páginas de detalles de producto configurables cuando la URL incluye opciones de muestra preseleccionadas, lo que provoca la visualización de una imagen estática en lugar del vídeo.

<u>Pasos a seguir</u>:

1. Vaya a [!UICONTROL Stores] > [!UICONTROL Attributes] > [!UICONTROL Product].
1. Seleccione el atributo **[!UICONTROL Color]** y edítelo.
1. Actualice la siguiente configuración:
   1. Establezca [!UICONTROL Catalog Input Type for Store Owner] en [!UICONTROL Visual Swatch].
   1. Establezca **[!UICONTROL Update Product Preview Image]** en **[!UICONTROL Yes]**.
1. Cree algunas opciones para este atributo.
1. Cree una nueva categoría y agréguele un nuevo producto configurable, utilizando el atributo **[!UICONTROL Color]**.
1. Añadir una sola imagen aleatoria al producto principal.
1. Edite los productos secundarios configurables recién creados y añada un vídeo a su galería de medios:
   1. Haga clic en **[!UICONTROL Add Video]** y use la URL del vídeo de prueba: https://vimeo.com/12860646.
1. Guarde el producto, borre la caché y vuelva a indexar el almacén.
1. Abra el producto recién creado en la tienda, seleccione una de las opciones de muestra y confirme que el vídeo se carga correctamente con el botón del reproductor en la pantalla.
1. El vídeo se debe cargar según lo esperado y debe aparecer el botón del reproductor.
1. Ahora, haga clic con el botón derecho en una de las opciones de muestra, seleccione **[!UICONTROL Inspect]** y busque el identificador de atributo y el identificador de opción. Copie la dirección URL del producto y anexe lo siguiente al final: `www.product-url.com/producit-test#attribute_id=option_id`. Esto preseleccionará la opción de muestra. Abra la URL actualizada en una nueva ventana.

<u>Resultados esperados</u>:

El vídeo debe cargarse correctamente, de forma similar a cuando se selecciona manualmente una opción de muestra.

<u>Resultados reales</u>:

Se muestra una imagen estática en lugar del vídeo. Se registran errores de consola, lo que indica un error en la inicialización de vídeo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.

