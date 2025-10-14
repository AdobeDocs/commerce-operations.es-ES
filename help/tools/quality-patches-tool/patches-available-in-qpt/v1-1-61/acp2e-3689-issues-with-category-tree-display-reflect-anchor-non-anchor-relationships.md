---
title: 'ACP2E-3689: Varios problemas con la visualización del árbol de categorías en niveles más profundos y que reflejan relaciones de anclaje/no anclaje'
description: Aplique el parche ACP2E-3689 para corregir el problema de Adobe Commerce con la visualización del árbol de categorías en más de cuatro niveles de anidación y que reflejen las relaciones de anclaje/no anclaje.
feature: Categories, Page Content
role: Admin, Developer
exl-id: 8d3c484f-3f8d-4fc1-8b31-e850cb34341c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACP2E-3689: Varios problemas con la visualización del árbol de categorías en niveles más profundos y que reflejan relaciones de anclaje/no anclaje

>[!NOTE]
>
>Este parche reemplaza el [ACSD-62689](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-62689-customer-add-categories-issue-related-product-rules-and-widgets.md) para las versiones 2.4.7 y posteriores.

El parche ACP2E-3689 corrige varios problemas con la visualización del árbol de categorías en más de la profundidad cuatro al anidar y reflejar las relaciones de anclaje/no anclaje. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. El ID del parche es ACP2E-3689. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El árbol de categorías en los niveles más profundos (4+) no se muestra correctamente y refleja las relaciones de anclaje/no anclaje.

<u>Pasos a seguir</u>:

1. Configure un árbol de categorías con categorías anidadas de más de 4 niveles.
1. Expanda el árbol de categorías en Administración que aparece en diferentes lugares:
   1. Configure un [!UICONTROL Related Products Rule] y una condición basada en categorías.
   1. Cree un widget y en [!UICONTROL Layout Updates] seleccione [!UICONTROL Anchor categories].

<u>Resultados esperados</u>:

Todos los niveles del árbol de categorías se muestran correctamente.

<u>Resultados reales</u>:

Solo están disponibles los primeros niveles (&lt;4) del árbol de categorías.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
