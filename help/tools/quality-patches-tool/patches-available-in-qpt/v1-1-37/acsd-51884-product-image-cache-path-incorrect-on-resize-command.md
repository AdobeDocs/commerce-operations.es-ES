---
title: 'ACSD-51884: ruta incorrecta de la caché de imágenes de producto en el comando resize'
description: Aplique el parche ACSD-51884 para corregir el problema de Adobe Commerce en el que la ruta de acceso de la caché de la imagen del producto se vuelve incorrecta después de ejecutar el comando resize.
feature: Products
role: Admin
exl-id: a3779e4b-2749-460e-a0a8-656b26bb06fa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-51884: ruta incorrecta de la caché de imágenes de producto en el comando resize

El parche ACSD-51884 corrige el problema de un error interno en el que la ruta de la caché de la imagen del producto se vuelve incorrecta después de ejecutar el comando de cambio de tamaño. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.37. El ID del parche es ACSD-51884. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7-2.4.7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La ruta de acceso a la caché de imágenes de producto es incorrecta con el comando resize.

<u>Pasos a seguir</u>:

1. Crear nuevo sitio web, tienda o vista de tienda.
1. Cree un producto, asígnelo a ambos sitios web y cargue la imagen del producto.
1. Crear una temática nueva (consulte el Adobe.zip adjunto).
1. En `app/design/Adobe/theme/etc/view.xml` cambio:

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">1</var>
</vars>
```

hasta

```
<vars module="Magento_Catalog">
           <var name="product_image_white_borders">0</var>
</vars>
```

1. Aplique la temática a la vista de tienda creada anteriormente.
1. Consulte la página del producto en el segundo sitio web. La imagen del producto se muestra correctamente.
1. Usar caché de vaciado:
   `bin/magento cache:flush`
1. Consulte la página del producto en el segundo sitio web.

<u>Resultados esperados</u>:

La imagen del producto se muestra correctamente.

<u>Resultados reales</u>:

La imagen del producto no existe.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
