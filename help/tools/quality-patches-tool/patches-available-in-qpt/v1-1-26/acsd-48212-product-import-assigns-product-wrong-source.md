---
title: 'ACSD-48212: la importación de producto asigna el producto a un origen incorrecto'
description: Aplique el parche ACSD-48212 para corregir el problema de Adobe Commerce donde la importación del producto asigna el producto al origen incorrecto.
feature: Admin Workspace, Data Import/Export, Products
role: Admin
exl-id: d573d95b-95fc-4f59-b518-18088855a154
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-48212: la importación de producto asigna el producto a un origen incorrecto

El parche ACSD-48212 corrige el problema en el que la importación del producto asigna el producto al origen incorrecto. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.26. El ID del parche es ACSD-48212. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La importación de productos asigna el producto al origen incorrecto.

<u>Pasos a seguir</u>:

1. Crear un origen de inventario secundario.
1. Cree un producto con el origen de inventario predeterminado solamente.
1. Exporte el producto.
1. Ejecutar `bin/magento cron:run`.
1. Abra **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Seleccione el producto en la cuadrícula.
1. Cancele la asignación de existencias mediante el menú *[!UICONTROL mass action]*.
1. Ejecutar `bin/magento cron:run`.
1. Asigne el origen secundario mediante el menú *[!UICONTROL mass action]*.
1. Ejecutar `bin/magento cron:run`.
1. Elimine el producto mediante el menú *[!UICONTROL mass action]*.
1. Ejecutar `bin/magento cron:run`.
1. Importe el producto utilizando el CSV exportado anteriormente.
1. Compruebe la asignación de origen.

<u>Resultados esperados</u>:

El producto solo está asignado al origen predeterminado.

<u>Resultados reales</u>:

El producto se asigna tanto al origen predeterminado como al secundario.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
