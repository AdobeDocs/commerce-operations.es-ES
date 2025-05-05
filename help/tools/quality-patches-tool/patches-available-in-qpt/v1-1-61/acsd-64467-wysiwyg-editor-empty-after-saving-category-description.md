---
title: 'ACSD-64467: WYSIWYG editor vacía después de guardar categoría descripción en tienda nivel vista'
description: Aplicar el ACSD-64467 parche para solucionar el problema de Adobe Systems Commerce donde el editor WYSIWYG aparece vacío después de guardar una descripción categoría en el nivel tienda vista.
feature: Page Content
role: Admin, Developer
exl-id: 8bc1794f-ace1-4719-9fff-194dbd701ab6
source-git-commit: b71447d5dac3208e537b29204dc8d47e8838f584
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-64467: WYSIWYG editor vacía después de guardar categoría descripción en tienda nivel vista

El parche ACSD-64467 corrige el problema por el cual el editor WYSIWYG aparece vacío después de guardar una descripción categoría en el nivel de vista tienda. Este parche está disponible cuando está instalado 1.1.61 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) . El ID de parche es ACSD-64467. Tenga en cuenta que el problema está programado para solucionarse en Adobe Systems Commerce 2.4.8.

## Productos y versiones afectados

**El parche se crea para Adobe Systems versión de Commerce:**

* Adobe Systems Commerce (todos los métodos implementación) 2.4.7-p3

**Compatible con las versiones de Adobe Systems Commerce:**

* Adobe Systems Commerce (todos los métodos implementación) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con nuevas [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Systems Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]Search para parches Página](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Emitir

El editor WYSIWYG aparece vacío después de guardar una descripción categoría en el nivel tienda vista.

<u>Procedimiento</u>:

1. Editar un categoría en la Administración de comercio a nivel tienda vista.
1. Anule la selección de la *[!UICONTROL Use default value]* casilla de verificación situada junto a la descripción del categoría.
1. Introduzca una descripción en la editor WYSIWYG.
1. Haga clic en **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

La descripción se guarda y se muestra correctamente.

<u>Resultados reales</u>:

La descripción queda vacía después de que se vuelva a cargar el Página.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función de su método implementación:

* Adobe Systems de comercio o Magento Open Source local: [[!DNL Quality Patches Tool] uso >](/help/tools/quality-patches-tool/usage.md) en el [!DNL Quality Patches Tool] guía.
* Adobe Systems Commerce on infraestructura en la nube: [Upgrades and Patches > Aplicar Patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) in the Commerce on Cloud Infrastructure guía.

## Lecturas relacionadas

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: Un herramienta de autoservicio para parches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) de calidad en el Herramientas guía.
