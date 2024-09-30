---
title: "ACSD-49898: La cuadrícula de productos genera una excepción"
description: Aplique el parche ACSD-49898 para corregir el problema de Adobe Commerce en el que la cuadrícula de productos presenta una excepción cuando un producto agrupado tiene un precio especial que supera los 1000.
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-49898: La cuadrícula de productos genera una excepción

El parche ACSD-49898 soluciona el problema en el que la cuadrícula de productos genera una excepción cuando un producto agrupado tiene un precio especial que supera los 1000. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-49898. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cuadrícula de productos genera una excepción cuando un producto agrupado tiene un precio especial que supera los 1000. El problema está relacionado con el uso de comas en lugar de puntos para números decimales en ciertas configuraciones regionales.

<u>Pasos a seguir</u>:

1. Cree un producto agrupado.
1. Establezca el precio especial en 9999; guarde y cierre.
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**

>[!NOTE]
>
>Busque el SKU del producto agrupado si no está visible.

<u>Resultados esperados</u>:

* El usuario puede filtrar/ver el producto agrupado con el precio especial.
* El precio especial se muestra como porcentaje para productos agrupados y como precio para otros tipos de productos.

<u>Resultados reales</u>:

Se produjo el siguiente error: *Se encontró un valor no numérico*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
