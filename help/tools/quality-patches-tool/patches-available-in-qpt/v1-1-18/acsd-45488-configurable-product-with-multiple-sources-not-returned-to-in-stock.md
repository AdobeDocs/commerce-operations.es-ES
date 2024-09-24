---
title: "ACSD-45488: Producto configurable con varios orígenes que no se devuelve a en stock automáticamente"
description: El parche ACSD-45488 resuelve el problema en el que un producto configurable con varias fuentes no se devuelve a en stock automáticamente. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18. El ID del parche es ACSD-45488. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
feature: Configuration, Orders, Products, Returns
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-45488: producto configurable con varios orígenes que no se devuelve en stock automáticamente

El parche ACSD-45488 resuelve el problema en el que un producto configurable con varias fuentes no se devuelve a en stock automáticamente. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.18. El ID del parche es ACSD-45488. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un producto configurable con varios orígenes no se devuelve a en stock automáticamente.

<u>Pasos a seguir</u>:

1. Crear un origen de stock secundario.
1. Cree un producto configurable con dos productos virtuales asociados.
1. Asigne los productos asociados al origen de stock predeterminado y establezca la cantidad en uno.
1. Compruebe `stock_status` de `cataloginventory_stock_status`.
1. Establezca ambos productos asociados en *sin existencias*.
1. Compruebe `stock_status` de `cataloginventory_stock_status`.
1. Establezca ambos productos asociados en *en stock*.
1. Compruebe `stock_status` de `cataloginventory_stock_status`.

<u>Resultados esperados</u>:

El estado de existencias del producto configurable se actualiza a *en existencias* cuando los productos asociados están disponibles.

<u>Resultados reales</u>:

El estado de existencias del producto configurable no se actualiza a *en existencias* cuando los productos asociados están disponibles.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
