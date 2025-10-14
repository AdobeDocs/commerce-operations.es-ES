---
title: 'ACSD-47937: las notificaciones de caída de precios no se envían debido al almacenamiento en caché de nivel de aplicación'
description: Aplique el parche ACSD-47937 para solucionar el problema de Adobe Commerce, donde las notificaciones de caída de precios no siempre se envían debido al almacenamiento en caché de nivel de aplicación.
feature: Admin Workspace, Cache, Orders
role: Admin
exl-id: 91d8e677-c2bb-4230-bbe3-a2c5f9b82e16
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47937: las notificaciones de caída de precios no se envían debido al almacenamiento en caché de nivel de aplicación

El parche ACSD-47937 corrige el problema de que las notificaciones de caída de precios no siempre se envían debido al almacenamiento en caché de nivel de aplicación. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26. El ID del parche es ACSD-47937. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 y 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4, 2.4.5 y 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los clientes no reciben un correo electrónico de bajada de precios de productos para los cambios posteriores en los precios de los productos.

<u>Pasos a seguir</u>:

1. Habilite **[!UICONTROL Product Alert]** tanto para *[!UICONTROL Price Changes]* como para *[!UICONTROL Back in Stock]* en **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. Habilitar **[!UICONTROL Display Out of Stock Products]**.
1. Cree un producto simple (ABC) con la cantidad = 0.
1. Cree un cliente desde la tienda y suscríbase al producto anterior para recibir alertas de productos por caídas de precios.
1. Inicie la alerta del producto para los clientes de.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. Baja el precio del producto ABC.
1. Déclencheur la alerta de producto cron.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Vuelva a bajar el precio del producto ABC.
1. Déclencheur la alerta de producto cron.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>Si no está familiarizado con la herramienta [!DNL n98], puede ejecutar `bin/magento cron:run command` como de costumbre y supervisar la tabla `cron_schedule` para asegurarse de que el trabajo `catalog_product_alert` obtenga el estado de éxito.

<u>Resultados esperados</u>:

Se envía el segundo correo electrónico de caída de precios.

<u>Resultados reales</u>:

No se envía el segundo correo electrónico de caída de precios.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool]
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/es/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
