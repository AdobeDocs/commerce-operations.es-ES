---
title: 'MDVA-43491: La etiqueta de imagen base no se actualiza cuando se importa mediante CSV'
description: El parche MDVA-43491 soluciona el problema de que la `base_image_label` no se actualiza al importarla mediante un archivo CSV para un sitio web de varias tiendas. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13. El ID del parche es MDVA-43491. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Data Import/Export
role: Admin
exl-id: f6a5f641-aaf0-4b6e-afa9-7f436f8f59e6
source-git-commit: f6abbbb28a3077f7bf26a393388c5059fcd8c599
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-43491: La etiqueta de imagen base no se actualiza cuando se importa mediante CSV

La revisión MDVA-43491 corrige el problema en el cual `base_image_label` no se actualiza cuando se importa a través de un archivo CSV para un sitio web de varias tiendas. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.13. El ID del parche es MDVA-43491. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

`base_image_label` no se actualiza cuando se importa con un archivo CSV para un sitio web de varias tiendas.

<u>Requisitos previos</u>:

Uno o más sitios web, tiendas y vistas de tiendas existentes que no son predeterminados.

<u>Pasos a seguir</u>:

1. Cree un nuevo producto.

   * Cargue una imagen.
   * Asigne el producto a los sitios web recién creados.

1. Exporte el producto como CSV.
1. Actualice `base_image_label` para cada vista de almacén duplicando la fila predeterminada del archivo CSV.
1. Importe el archivo CSV. Actualizará correctamente las etiquetas de cada tienda, lo cual se puede comprobar en la ficha **Imágenes y vídeos** de la página de edición del producto.
1. Vuelva a exportar el archivo CSV y actualice la columna `base_image_label` con valores diferentes.
1. Vuelva a importar el archivo CSV.
1. Abra el producto en Admin y compruebe si la etiqueta se ha actualizado para cada vista de tienda.

<u>Resultados esperados</u>:

El texto alternativo (etiqueta de imagen) se actualiza con el valor específico del almacén según el archivo CSV.

<u>Resultados reales</u>:

El texto alternativo (etiqueta de imagen) no se actualiza con el valor `base_image_label` en el archivo CSV.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
