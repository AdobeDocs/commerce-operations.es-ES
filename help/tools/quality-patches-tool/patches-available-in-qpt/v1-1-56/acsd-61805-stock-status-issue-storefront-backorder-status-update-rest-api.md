---
title: 'ACSD-61805: corrige un problema de stock en la tienda después de actualizar el estado del pedido pendiente mediante la API de REST'
description: Aplique el parche ACSD-61805 para corregir el problema de Adobe Commerce en el que los productos permanecen sin existencias en la tienda después de actualizar el estado del pedido pendiente mediante la API de REST
feature: REST, Catalog Management, Inventory
role: Admin, Developer
exl-id: ff85e747-6394-43db-a02a-87b1e5e59f00
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '400'
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
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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

   ```shell
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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
