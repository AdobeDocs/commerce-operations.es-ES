---
title: 'ACSD-59786: GraphQL devuelve un error al recuperar un quote_id para una cotización caducada'
description: Aplique el parche ACSD-59786 para solucionar el problema de Adobe Commerce donde una consulta de GraphQL devuelve un error al recuperar un quote_id para un presupuesto caducado.
feature: GraphQL, Quotes, Companies
role: Admin, Developer
exl-id: 3c7aaa99-a2e0-44fe-9426-b24095615915
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-59786: GraphQL devuelve un error al recuperar un `quote_id` para una oferta caducada

El parche ACSD-59786 corrige el problema en el que una consulta de GraphQL devuelve un error al recuperar un `quote_id` para una cotización caducada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51. El ID del parche es ACSD-59786. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Una consulta de GraphQL devuelve un error al recuperar un `quote_id` para una oferta caducada.

<u>Pasos a seguir</u>:

1. Habilitar **[!UICONTROL Companies]** y **[!UICONTROL Purchase Orders]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** y estableció **[!UICONTROL Enable Company]** en *Sí*.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** > **[!UICONTROL Order Approval Configuration]** y se estableció **[!UICONTROL Enable Purchase Orders]** en *Sí*.
1. Cree una nueva compañía y establezca **[!UICONTROL Enable Purchase Orders]** en *Yes* para el mismo.
1. Cree un producto simple y asígnelo a una categoría.
1. Inicie sesión en Storefront con la cuenta de administrador de la compañía y cree un nuevo pedido con **[!UICONTROL Purchase Order]** como método de pago.
1. Cambiar **[!UICONTROL Quote Lifetime (days)]**.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Shopping Cart]** > **[!UICONTROL Quote Lifetime (days)]** = *0*.
1. Ejecute el comando `bin/magento c:f`.
1. Vaya a la base de datos `quote_table` y cambie los valores `created_at` y `updated_at` con un día en el pasado.
1. Ejecute el comando `bin/magento cron:run --group="sales_clean_quotes`.
1. Ejecute la solicitud de GraphQL que se indica a continuación con un token autorizado para el administrador que crea **[!UICONTROL Purchase Order]**:

   ```GraphQL
   {
       customer {
           purchase_order(uid: "MQ==") {
               quote {
                   id
               }
           }
       }
   } 
   ```

<u>Resultados esperados</u>:

La consulta GraphQL devuelve `quote_id`.

<u>Resultados reales</u>:

La consulta de GraphQL devuelve un error interno del servidor.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
