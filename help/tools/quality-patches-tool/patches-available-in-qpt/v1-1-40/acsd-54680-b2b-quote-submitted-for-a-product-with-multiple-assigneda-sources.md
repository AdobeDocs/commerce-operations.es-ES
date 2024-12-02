---
title: 'ACSD-54680: no se puede procesar la cotización B2B de un producto con varias fuentes asignadas'
description: Aplique el parche ACSD-54680 para solucionar el problema de Adobe Commerce en el que no se puede procesar la cotización B2B de un producto con varios orígenes asignados.
feature: B2B
role: Admin, Developer
exl-id: c5307785-a4c6-4d0c-9009-0d0caee97b3d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-54680: la cotización B2B de un producto con varios orígenes asignados no se puede procesar.

El parche ACSD-54680 soluciona el problema que impedía procesar el presupuesto B2B de un producto con varias fuentes asignadas. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.40. El ID del parche es ACSD-54680. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cotización B2B de un producto con varios orígenes asignados no se puede procesar.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Sources]** y cree dos nuevas fuentes: **Source 1** y **Source 2**.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Stocks]** y cree un nuevo inventario de stock: **Stock A**, asígnelo al sitio web principal y asígnele **Source 1** y **Source 2**.
1. Cree un producto simple, asigne **Source 1** y **Source 2**, y establezca una cantidad = *2* para cada origen. (la cantidad vendible del producto debería ser *4* como resultado).
1. Crear una cuenta de compañía.
1. Vaya a **[!UICONTROL Storefront]** e inicie sesión en la cuenta de la empresa.
1. Agregue el producto simple al carro de compras con la cantidad = *4*.
1. Abra *[!UICONTROL Shopping cart]* y haga clic en el botón **[!UICONTROL Request a quote]**.
1. Agregue un comentario y un nombre de comillas y haga clic en el botón **[!UICONTROL Send a Request]**.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Abrir oferta enviada recientemente.

<u>Resultados esperados</u>:

Los artículos citados contienen el producto pedido.

<u>Resultados reales</u>:

La sección de la página de artículos citados está vacía y no es posible procesar el presupuesto.
`var/log/system.log` contiene

```
report.CRITICAL: TypeError: number_format() expects parameter 1 to be float, null given in .../vendor/magento/module-negotiable-quote/Model/QuoteUpdatesInfo.php:232
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
