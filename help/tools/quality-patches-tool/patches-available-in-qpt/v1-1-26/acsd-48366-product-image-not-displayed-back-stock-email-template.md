---
title: 'ACSD-48366: la imagen del producto no se muestra en la plantilla de correo electrónico [!UICONTROL Back to Stock]'
description: Aplique el parche ACSD-48366 para corregir el problema de Adobe Commerce en el que la imagen en miniatura del producto no se muestra en el correo electrónico de alerta de existencias del producto.
feature: Admin Workspace, Communications, Orders, Products
role: Admin
exl-id: a721f399-f50a-4a13-9f5d-17ae7f3985f6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48366: la imagen del producto no se muestra en la plantilla de correo electrónico [!UICONTROL Back to Stock]

El parche ACSD-48366 corrige el problema en el que la imagen en miniatura del producto no se muestra en el correo electrónico de alerta de existencias del producto. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26. El ID del parche es ACSD-48366. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La imagen del producto no se muestra en la plantilla de correo electrónico [!UICONTROL Back to Stock].

<u>Pasos a seguir</u>:

1. Habilite *[!UICONTROL Product Alert]* para *[!UICONTROL Back in Stock]* yendo a **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]*.
1. Para habilitar *[!UICONTROL Display Out of Stock Products]*, vaya a **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]*.
1. Cree un producto simple con cantidad = 0.
1. Cree un cliente desde la tienda y suscríbase al producto anterior para recibir alertas de productos cuando esté disponible.
1. Haga que el producto esté en stock.
1. Ejecute la alerta de producto cron.

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Inicie la alerta de producto para el cliente.

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. Compruebe el correo electrónico. El correo electrónico de alerta de stock debería estar disponible en el receptor de correo.

<u>Resultados esperados</u>:

La imagen del producto se muestra en el correo electrónico de alerta de stock.

<u>Resultados reales</u>:

La imagen del producto no está disponible en el correo electrónico de alerta de stock.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
