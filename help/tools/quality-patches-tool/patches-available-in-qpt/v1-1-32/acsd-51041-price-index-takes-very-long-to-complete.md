---
title: 'ACSD-51041: El índice de precios tarda mucho en completarse'
description: Aplique el parche ACSD-51041 para solucionar el problema de Adobe Commerce, donde el índice de precios tarda mucho tiempo en completarse con un conjunto de productos muy grande.
feature: Configuration
role: Admin
exl-id: d45d4042-06a1-445d-bed3-803085626dd3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-51041: El índice de precios tarda mucho en completarse

El parche ACSD-51041 soluciona el problema en el que el índice de precios tarda mucho tiempo en completarse con un conjunto de productos muy grande. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32. El ID del parche es ACSD-51041. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.5-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Con un conjunto de productos muy grande, el índice de precios tarda mucho tiempo en completarse.

<u>Pasos a seguir</u>:

1. Habilite el módulo *[!UICONTROL Inventory]*.
1. Tener varias fuentes de stock (con una fuente no predeterminada que proporcione la mayoría de las existencias).
1. Genere ~200k productos.
1. Ejecutar un índice de inventario.

<u>Resultados esperados</u>:

`deleteIndexData` procesa solo los ID únicos para optimizar el rendimiento.

<u>Resultados reales</u>:

`deleteIndexData` procesa todos los ID, lo cual lleva mucho tiempo completar.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
