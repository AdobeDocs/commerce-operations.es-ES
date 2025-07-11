---
title: 'ACSD-64118: Las solicitudes de guardado de productos simultáneas para el mismo producto causan incoherencia de datos y entradas duplicadas'
description: Aplique el parche ACSD-64118 para corregir el problema de Adobe Commerce en el que las solicitudes simultáneas para guardar y actualizar el mismo producto resultan en incoherencia de datos o productos duplicados.
feature: REST
role: Admin, Developer
type: Troubleshooting
source-git-commit: 4235511ccbef028e1564d7626daadaa5beae0fd4
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# ACSD-64118: Las solicitudes de guardado de productos simultáneas para el mismo producto causan incoherencia de datos y entradas duplicadas

El parche ACSD-64118 corrige el problema en el que las solicitudes simultáneas para guardar y actualizar el mismo producto resultan en incoherencia de datos o productos duplicados. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. El ID del parche es ACSD-64118. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p7

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p10

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las solicitudes simultáneas para guardar y actualizar el mismo producto producen incoherencia de datos o productos duplicados.

<u>Pasos a seguir</u>:

1. Configurar procesos múltiples para consumidores en `env.php`:

   ```
   'multiple_processes' =>
       array (
           'async.operations.all' => 4,
       ),
   ```

1. Agregue una tienda adicional y una nueva vista de la tienda al sitio web principal.
1. Envíe una solicitud de API masiva al extremo predeterminado de la vista de tienda `/rest/default/async/bulk/V1/products` con la siguiente carga útil para crear un producto:

   ```
   [
     {
       "product": {
         "sku": "Test_Prod",
         "name": "Test Product",
         "attribute_set_id": 4
       }
     }
   ]
   ```

1. Utilice la misma carga útil para enviar una solicitud de API masiva al nuevo extremo de vista de tienda `/rest/store/async/bulk/V1/products` para actualizar el producto.
1. Vaciar caché.
1. Ejecutar trabajos cron.
1. Consulte la tabla `catalog_product_entity` para ver las entradas del producto de los pasos anteriores.

<u>Resultados esperados</u>:

* Una sola entrada para el SKU del producto debe estar presente en la tabla `catalog_product_entity`.
* La primera solicitud de API de REST debe crear una entrada de base de datos y todas las solicitudes posteriores deben actualizar esa entrada de base de datos.

<u>Resultados reales</u>:

Hay varias entradas para el mismo SKU en la tabla `catalog_product_entity`.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
