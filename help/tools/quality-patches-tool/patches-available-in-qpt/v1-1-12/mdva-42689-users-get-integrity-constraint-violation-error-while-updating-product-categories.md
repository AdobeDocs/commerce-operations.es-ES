---
title: 'MDVA-42689: Los usuarios obtienen un error de infracción de la restricción de integridad al actualizar las categorías de productos durante la importación'
description: El parche MDVA-42689 resuelve el problema en el que los usuarios reciben un error de infracción de restricción de integridad al actualizar las categorías de productos durante la importación. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-42689. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: 3f81f195-5a95-45f6-8970-403b8398e759
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-42689: Los usuarios obtienen un error de infracción de la restricción de integridad al actualizar las categorías de productos durante la importación

El parche MDVA-42689 resuelve el problema en el que los usuarios reciben un error de infracción de restricción de integridad al actualizar las categorías de productos durante la importación. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-42689. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Adobe Commerce emite un error de infracción de la restricción de integridad al actualizar las categorías de productos durante la importación.

<u>Pasos a seguir</u>:

1. Configurar dos sitios web.
1. Cree subcategorías bajo la categoría raíz hasta dos niveles en la página de categoría. Por ejemplo, Categoría raíz > **Equipo** > **Relojes**.
1. Cree dos productos sencillos y asigne ambos a la misma categoría **Equipo** > **Relojes**.
1. Asigne un producto simple a ambos sitios web.
1. Guarde el producto.
1. Prepare un archivo CSV para su importación. Debe haber dos registros de producto con vistas de tienda diferentes. Uno de los productos debe pertenecer a ambas vistas de tienda.
1. Ahora importe el archivo CSV navegando a **Sistema** > **Importar** > **Tipo de entidad** (Productos).

<u>Resultados esperados</u>:

El archivo CSV se importa sin errores.

<u>Resultados reales</u>:

Adobe Commerce genera el siguiente error:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1062 Duplicate entry '1302' for key 'PRIMARY', query was: INSERT INTO `catalog_url_rewrite_product_category` (`url_rewrite_id`,`category_id`,`product_id`) VALUES (?, ?, ?), (?, ?, ?), (?, ?, ?)
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
