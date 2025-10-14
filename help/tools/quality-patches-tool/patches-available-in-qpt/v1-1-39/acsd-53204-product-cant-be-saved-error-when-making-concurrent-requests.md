---
title: 'ACSD-53204: * El producto no se puede guardar * error en solicitudes simultáneas para añadir imágenes a la galería'
description: Aplique el parche ACSD-53204 para corregir el problema de Adobe Commerce en el que se produce el error *El producto no se puede guardar* al realizar solicitudes simultáneas para agregar imágenes a la galería de productos mediante el punto final rest/V1/products/&lt;sku&gt;/media.
feature: Catalog Management, Media, Products, REST
role: Admin, Developer
exl-id: 7fdf41e5-46ef-4505-b8ce-c330bd899fa1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# ACSD-53204: Error &quot;*El producto no se puede guardar*&quot; en solicitudes simultáneas para agregar imágenes a la galería

La revisión ACSD-53204 corrige el problema en el que se produce el error &quot;*El producto no se puede guardar*&quot; al realizar solicitudes simultáneas para agregar imágenes a la galería de productos mediante el extremo `rest/V1/products/<sku>/media`. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.39. El ID del parche es ACSD-53204. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Error &quot;*El producto no se puede guardar*&quot; al realizar solicitudes simultáneas para agregar imágenes a la galería de productos mediante el extremo `rest/V1/products/<sku>/media`.

<u>Pasos a seguir</u>:

1. Inicie sesión en el panel de administración.
1. Cree un producto con el SKU p1.
1. Realice varias solicitudes simultáneas al extremo `rest/V1/products/<sku>/media` para cargar varias imágenes simultáneamente.

<u>Resultados esperados</u>:

Las imágenes se guardan sin errores.

<u>Resultados reales</u>:

El error &quot;*El producto no se puede guardar*&quot; se devuelve de vez en cuando.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
