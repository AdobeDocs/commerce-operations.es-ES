---
title: 'ACSD-64467: el editor de WYSIWYG está vacío después de guardar la descripción de la categoría en el nivel de vista de tienda'
description: Aplique el parche ACSD-64467 para corregir el problema de Adobe Commerce en el que el editor de WYSIWYG aparece vacío después de guardar una descripción de categoría en el nivel de vista de tienda.
feature: Page Content
role: Admin, Developer
exl-id: 8bc1794f-ace1-4719-9fff-194dbd701ab6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-64467: el editor de WYSIWYG está vacío después de guardar la descripción de la categoría en el nivel de vista de tienda

El parche ACSD-64467 corrige el problema en el que el editor de WYSIWYG aparece vacío después de guardar una descripción de categoría en el nivel de vista de tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. El ID del parche es ACSD-64467. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El editor de WYSIWYG aparece vacío después de guardar una descripción de categoría en el nivel de vista de tienda.

<u>Pasos a seguir</u>:

1. Edite una categoría en el Administrador de Commerce en el nivel de vista de tienda.
1. Anule la selección de la casilla de verificación *[!UICONTROL Use default value]* junto a la descripción de la categoría.
1. Introduzca una descripción en el editor de WYSIWYG.
1. Haga clic en **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

La descripción se guarda y se muestra correctamente.

<u>Resultados reales</u>:

La descripción está vacía después de que la página se vuelva a cargar.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
