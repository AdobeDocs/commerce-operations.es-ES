---
title: 'ACSD-61805: corrige un problema de stock en la tienda después de actualizar el estado del pedido pendiente mediante la API de REST'
description: Aplique el parche ACSD-61805 para corregir el problema de Adobe Commerce en el que los productos permanecen sin existencias en la tienda después de actualizar el estado del pedido pendiente mediante la API de REST
feature: REST, Catalog Management, Inventory
role: Admin, Developer
source-git-commit: abad1a2f2a1bdc2c1a4b6f821e6b02190a5ebe83
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# ACSD-61805: corrige un problema de stock en la tienda después de actualizar el estado del pedido pendiente mediante la API de REST

El parche ACSD-61805 corrige el problema en el que los productos permanecen sin existencias en la tienda después de actualizar el estado del pedido pendiente a través de la API de REST. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. El ID del parche es ACSD-61805. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos permanecen agotados en la tienda después de actualizar el estado del pedido pendiente a través de la API de REST.

<u>Pasos a seguir</u>:

1. Instale una instancia limpia con datos de ejemplo.
1. Crear un nuevo origen de inventario.
1. Cree un nuevo inventario de stock y asígnele el nuevo origen.
1. Asigne la nueva fuente al producto 24-MB01.
1. Establezca **[!UICONTROL Source Item Status]** en `In Stock` para ambos orígenes de productos.
1. Establezca la cantidad (**[!UICONTROL QTY]**) en *0* para ambas cantidades de productos.
1. Guarde el producto.
1. Recupere el token de administrador de esta dirección URL de extremo: `/rest/default/V1/integration/admin/token`

   ```json
   {
     "username":"admin", 
     "password":"password" 
   }
   ```

1. Actualizar el producto mediante el extremo: `/rest/default/V1/products`

   ```json
   {
     "product":{
       "sku": "24-MB01",
       "extension_attributes": {
           "stock_item": {
               "stock_id": "1",
               "is_in_stock": "0",
               "use_config_backorders": "false",
               "backorders": "0"
           }
       }
     }
   }
   ```

1. Ejecute los trabajos cron dos veces (una vez para crear programaciones y otra para ejecutarlas):

   ```bash
   bin/magento cron:run
   ```

1. Vaya al front-end y compruebe el producto.

<u>Resultados esperados</u>:

El producto debe estar *En stock*.

<u>Resultados reales</u>:

El producto está *agotado*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
