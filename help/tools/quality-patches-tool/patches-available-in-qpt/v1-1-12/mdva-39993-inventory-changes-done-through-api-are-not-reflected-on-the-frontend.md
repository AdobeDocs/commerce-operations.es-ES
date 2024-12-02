---
title: 'MDVA-39993: Los cambios en el inventario realizados a través de la API no se reflejan en la tienda'
description: El parche MDVA-39993 resuelve el problema de que los cambios de inventario realizados a través de la API no se reflejen en la tienda. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-39993. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: REST, Inventory, Orders, Storefront
role: Admin
exl-id: 5fa13635-bd58-470b-a4d5-e50cda8a46e3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# MDVA-39993: Los cambios en el inventario realizados a través de la API no se reflejan en la tienda

El parche MDVA-39993 resuelve el problema de que los cambios de inventario realizados a través de la API no se reflejen en la tienda. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-39993. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5 - 2.3.7-p2 y 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los cambios de inventario realizados mediante API no se reflejan en la página del producto de la tienda.

<u>Requisitos previos</u>:

Módulos de inventario instalados.

<u>Pasos a seguir</u>:

1. Asegúrese de que la cola está configurada para ejecutarse con cron y que cron está instalado y en ejecución.
1. Cree un producto configurable (COC001), con dos colores (Negro y Rojo) y dos tamaños (M y L).
1. Haga una opción sin existencias (COC001-Red-M).
1. Cargue la página de producto configurable en la tienda e intente hacer clic en cada color. Al hacer clic en **Rojo**, el tamaño **M** se debe tachar porque está agotado.
1. Haga que COC001-Red-M esté disponible usando el siguiente punto final de API y la carga útil:

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. Compruebe este sencillo producto desde el backend de y compruebe que se ha actualizado a En stock.
1. Cargue el producto configurable desde el front-end y haga clic en cada color. Observe el tamaño **M** cuando hace clic en **Rojo**.

<u>Resultados esperados</u>:

La opción COC001-Red-M no está tachada porque la hemos actualizado a En stock mediante API.

<u>Resultados reales</u>:

La opción COC001-Red-M sigue tachada, aunque esté en stock.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
