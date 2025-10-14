---
title: 'ACSD-47988: la exportación de productos recorta las etiquetas de HTML de la descripción del producto del generador de páginas'
description: Aplique el parche ACSD-47988 para solucionar el problema de Adobe Commerce donde la exportación del producto recorta las etiquetas de HTML de la descripción del producto de Page Builder.
feature: Admin Workspace, Data Import/Export, Page Builder, Products
role: Admin
exl-id: 2cb3b4ac-38df-4832-b894-b34bb3d7bbc6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-47988: la exportación de productos recorta las etiquetas de HTML de la descripción del producto del generador de páginas

El parche de ACSD-47988 corrige el problema en el que la exportación del producto recorta las etiquetas de HTML de la descripción del producto del generador de páginas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26. El ID del parche es ACSD-47988. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La exportación de productos recorta las etiquetas de HTML de la descripción del producto de Page Builder.

<u>Pasos a seguir</u>:

1. Cree productos con HTML en la descripción. Utilice el elemento HTML de Page Builder para insertar etiquetas de HTML.
1. Exporte los productos mediante la funcionalidad de importación y exportación de Adobe Commerce.
1. Importe el CSV exportado.
1. Abra el producto y compruebe los elementos de HTML en la descripción.

<u>Resultados esperados</u>:

Las etiquetas de HTML permanecen en la descripción del producto después de importar el mismo contenido.

<u>Resultados reales</u>:

Las etiquetas de HTML se eliminan después de la importación.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
