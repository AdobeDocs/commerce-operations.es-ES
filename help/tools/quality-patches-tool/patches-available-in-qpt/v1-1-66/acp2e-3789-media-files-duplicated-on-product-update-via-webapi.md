---
title: 'ACP2E-3789: Archivos de medios duplicados en la actualización del producto mediante WebAPI'
description: Aplique el parche ACP2E-3789 para solucionar el problema de Adobe Commerce en el que las actualizaciones de productos se realizan mediante archivos de medios duplicados de WebAPI cuando se proporciona un ID de medios.
feature: Catalog Management, Media, REST, Products, Cache
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8c1924a47248b22327dfc9a15ae426b2802e126b
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# ACP2E-3789: Archivos de medios duplicados en la actualización del producto mediante WebAPI

El parche ACP2E-3789 corrige el problema en el que las actualizaciones de productos a través de archivos de medios duplicados de WebAPI cuando se proporciona un ID de medios. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. El ID del parche es ACP2E-3789. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al actualizar un producto a través de WebAPI con un ID de medios, el sistema duplica los archivos de medios en lugar de reemplazarlos, lo que crea nuevos archivos con cada llamada de API y da como resultado una compilación de imágenes que sobrecarga el directorio `/pub/media/catalog/products/cache/`.

<u>Pasos a seguir</u>:

1. Cree un producto y añada una imagen.
1. Obtenga detalles del producto usando la API de REST en `base_url/rest/V1/products/<sku>`.
1. Realice una petición PUT para actualizar el producto, manteniendo `media_gallery_entrie` sin cambios (mismo nombre de imagen y archivo).
1. Compruebe el directorio `pub/media/catalog/product/xx/yy` antes y después de la actualización.

<u>Resultados esperados</u>:

El archivo de imagen se reemplaza cuando se incluye el ID de medios en la solicitud.

<u>Resultados reales</u>:

La imagen se duplica con un nuevo nombre (por ejemplo, wb04-blue-1.jpg), lo que provoca una acumulación de archivos innecesaria.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
