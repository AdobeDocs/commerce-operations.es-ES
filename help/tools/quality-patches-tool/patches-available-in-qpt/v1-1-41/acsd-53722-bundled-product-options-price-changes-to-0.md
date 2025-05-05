---
title: 'ACSD-53722: el precio de las opciones de productos agrupadas cambia a 0 $'
description: Aplique el parche ACSD-53722 para corregir el problema de Adobe Commerce en el que el precio de las opciones del producto agrupadas cambia a 0 $ cuando se activan actualizaciones programadas para diferentes ámbitos.
feature: Products
role: Admin, Developer
exl-id: 2e974a6a-0c79-442f-9b45-b4edf831a052
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-53722: el precio de las opciones de productos agrupadas cambia a 0 $

El parche ACSD-53722 corrige el problema en el que el precio de las opciones del producto empaquetado cambia a 0 $ cuando se activan actualizaciones programadas para diferentes ámbitos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.41. El ID del parche es ACSD-53722. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El precio de las opciones de productos agrupados cambia a 0 $ cuando se activan las actualizaciones programadas para diferentes ámbitos.

<u>Pasos a seguir</u>:

1. Cree dos sitios web, A y B.
1. Establecer configuración en **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]**.
1. Cree un producto agrupado con un precio fijo en los sitios web A y B:

   * Precio del producto agrupado = fijo = *0*

1. Añada un producto simple como opción desplegable para el paquete. Fije los siguientes precios:

   * Precio de todas las vistas de la tienda del producto simple dentro de la opción agrupada = *120*
   * Sitio web del producto simple Precio dentro de la opción agrupada = *130*
   * Precio del sitio web B del producto simple dentro de la opción agrupada = *140*

1. Programe una actualización para deshabilitar el producto agrupado en el sitio web A.

<u>Resultados esperados</u>:

La actualización programada para el sitio A no afecta al precio del sitio B.

<u>Resultados reales</u>:

Después de la actualización programada, el precio de la opción de producto empaquetado en el sitio web B se cambió a **$0**.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
