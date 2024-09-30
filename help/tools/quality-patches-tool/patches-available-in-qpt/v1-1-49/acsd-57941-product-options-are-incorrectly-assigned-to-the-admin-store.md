---
title: "ACSD-57941: las opciones de producto se asignan incorrectamente al almacén de administración"
description: Aplique el parche ACSD-57941 para corregir el problema de Adobe Commerce donde las opciones de producto se asignan incorrectamente al almacén de administración en lugar de a sus respectivas tiendas.
feature: Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 0%

---

# ACSD-57941: las opciones de producto se asignan incorrectamente al almacén de administración

El parche ACSD-57941 corrige el problema de que las opciones de producto se asignan incorrectamente al almacén de administración en lugar de a sus respectivas tiendas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49. El ID del parche es ACSD-57941. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las opciones de producto se asignan incorrectamente al almacén de administración en lugar de a sus respectivas tiendas.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Importe el mismo producto con algunas opciones personalizadas.
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y abra el producto creado. Haga clic en **[!UICONTROL Customizable options]** y asegúrese de que las opciones importadas estén visibles.
1. Importe el mismo archivo unas cuantas veces más.

<u>Resultados esperados</u>:

Se han actualizado las opciones personalizadas.

<u>Resultados reales</u>:

Las opciones personalizadas de producto están duplicadas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
