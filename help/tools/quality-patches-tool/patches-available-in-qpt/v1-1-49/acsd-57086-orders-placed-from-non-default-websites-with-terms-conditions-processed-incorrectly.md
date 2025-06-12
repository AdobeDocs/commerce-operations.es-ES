---
title: 'ACSD-57086: los pedidos de sitios web no predeterminados con los términos y condiciones habilitados se procesan incorrectamente'
description: Aplique el parche ACSD-57086 para corregir el problema de Adobe Commerce en el que los pedidos realizados desde sitios web no predeterminados con los términos y condiciones habilitados no se procesan correctamente.
feature: Orders
role: Admin, Developer
exl-id: d9f2ef50-12c4-4a2d-b140-dfd0e8948fd3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---

# ACSD-57086: los pedidos de sitios web no predeterminados con los términos y condiciones habilitados se procesan incorrectamente

El parche ACSD-57086 corrige el problema en el que los pedidos realizados desde sitios web no predeterminados con los términos y condiciones habilitados no se procesan correctamente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49. El ID del parche es ACSD-57086. Tenga en cuenta que este problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al utilizar una configuración de varias tiendas con procesamiento AsyncOrder, los pedidos realizados en cualquier sitio web o tienda que no sea el sitio web principal se rechazan debido a problemas con la administración del ámbito en el código de consumidor de cola.

<u>Pasos a seguir</u>:

1. Instale [!DNL RabbitMQ] y ejecute `bin/magento setup:upgrade` para crear las colas de [!DNL RabbitMQ].
1. Configurar el procesamiento de AsyncOrder con:

   ```bash
   bin/magento setup:config:set --checkout-async 1
   ```

1. Crear un sitio web secundario, una tienda y una vista de la tienda.
1. Cree un producto que se comparta entre ambos sitios web.
1. Habilitar términos y condiciones:
   1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.
   1. Establezca *[!UICONTROL Enable Terms And Conditions]* en *Sí*.
1. Configure los términos y condiciones de ambos sitios web:
   1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Terms And Conditions]** > **[!UICONTROL Add New Condition]**.
   1. Utilice la siguiente configuración:
      * *[!UICONTROL Condition Name]*: *Cualquier cosa*
      * *[!UICONTROL Status]*: *[!UICONTROL Enabled]*
      * *[!UICONTROL Applied]*: *[!UICONTROL Manually]*
      * *[!UICONTROL Store View]*: *[!UICONTROL Default Store View]*
   1. Cree otra condición para la segunda vista del sitio web o la tienda.
1. Cambie el sitio web predeterminado yendo a **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**. Haga clic en el segundo sitio web, marque *[!UICONTROL Set as Default]* y guarde.
1. Borre la caché con:

   ```bash
   bin/magento cache:clear
   ```

1. Vaya a la Tienda y añada un producto al carro de compras. Continúe con el proceso de pago y realice un pedido (debería ver una casilla de verificación en el paso del método de pago para aceptar los términos y condiciones).
1. Vuelva a Administración después de realizar el pedido y cambie el sitio web predeterminado al sitio web principal original y guarde los cambios.
1. Borre la caché:

   ```bash
   bin/magento cache:clear
   ```

1. Ejecute el siguiente comando para iniciar el consumidor de cola:

   ```bash
   bin/magento queue:cons:start placeOrderProcessor
   ```

<u>Resultados esperados</u>:

El pedido se completa; no se rechaza automáticamente.

<u>Resultados reales</u>:

El estado del pedido es *rechazado* con el siguiente comentario:

*No se realizó el pedido. En primer lugar, acepte los términos y condiciones y, a continuación, intente realizar el pedido de nuevo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
