---
title: "ACSD-50849: Añadir un nuevo producto después de borrar la caché da como resultado una discrepancia"
description: Aplique el parche ACSD-50849 para solucionar el problema de Adobe Commerce donde, al añadir un nuevo producto a la categoría después de borrar la caché, no coinciden las posiciones y selecciones de los productos existentes.
feature: Cache, Categories, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-50849: Añadir un nuevo producto después de borrar la caché provoca discrepancias

El parche ACSD-50849 corrige el problema que se producía al añadir un nuevo producto a la categoría después de borrar la caché, lo que da como resultado una discrepancia en las posiciones y selecciones de los productos existentes. Esta revisión está disponible cuando está instalado el QPT 1.1.32 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). El ID del parche es ACSD-50849. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Si se añade un nuevo producto a la categoría después de borrar la caché, las posiciones y selecciones de los productos existentes no coinciden.

<u>Pasos a seguir</u>:

1. Cree dos productos.
1. Asignar un producto a una categoría.
1. Abra la categoría desde el administrador.
1. Limpiar la caché `bin/magento cache:flush`.
1. Añada el segundo producto a la categoría.

<u>Resultados esperados</u>:

Los productos existentes asignados en la categoría no se eliminan automáticamente.

<u>Resultados reales</u>:

El primer producto (existente) se elimina automáticamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
