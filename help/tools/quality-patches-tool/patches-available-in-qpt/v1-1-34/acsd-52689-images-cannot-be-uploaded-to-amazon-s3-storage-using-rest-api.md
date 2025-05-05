---
title: 'ACSD-52689: Las imágenes no se pueden cargar en el almacenamiento de Amazon S3 mediante la API de REST'
description: Aplique el parche ACSD-52689 para corregir el problema de Adobe Commerce en el que las imágenes no se pueden cargar en el almacenamiento de Amazon S3 a través de la API de REST.
feature: REST, Storage, Iaas
role: Admin
exl-id: 4d7a8ea7-2856-4b40-a922-fdd356dcaea4
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-52689: Las imágenes no se pueden cargar en el almacenamiento de Amazon S3 mediante la API de REST

El parche ACSD-52689 soluciona el problema que impedía cargar las imágenes en el almacenamiento de Amazon S3 mediante la API de REST. Este parche está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.34. El ID del parche es ACSD-52689. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las imágenes no se pueden cargar en el almacenamiento de Amazon S3 mediante la API de REST

<u>Pasos a seguir</u>:

1. Configure REMOTE_STORAGE para el bloque de Amazon S3.
1. Añada una imagen al producto mediante la API por lotes.

   ```POST .../rest/all/async/bulk/V1/products/bySku/media```

   ```
   [
       {
           "sku": "p1",
           "entry": {
               "media_type": "image",
               "position": 0,
               "disabled": false,
               "types": [
                   "image",
                   "thumbnail",
                   "small_image",
                   "swatch_image"
               ],
               "content": {
                "type": "image\/jpeg",
                   "name": "adobe_commerce_test_3",
                   "base64_encoded_data": "/9j/4AAQSkZJRgABAQAAAQABA..."
               }
           }
       }
   ]
   ```

1. Espere a que se procese la operación masiva.

<u>Resultados esperados</u>

La imagen debe cargarse en el compartimento de Amazon S3.

<u>Resultados reales</u>

La imagen no se carga automáticamente en el contenedor de Amazon S3.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
