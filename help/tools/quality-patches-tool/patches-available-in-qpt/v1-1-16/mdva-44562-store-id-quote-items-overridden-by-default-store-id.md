---
title: 'MDVA-44562: el ID de tienda de los artículos de presupuesto se sobrescribe por el ID de tienda predeterminado'
description: El parche MDVA-44562 corrige el problema en el que el ID de tienda predeterminado anula el ID de tienda de los elementos de presupuesto de las solicitudes de GraphQL. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16. El ID del parche es MDVA-44562. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
feature: Quotes
role: Admin
exl-id: 007a82f7-4bc9-4a51-8b18-05f6c0867ea7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44562: el ID de tienda de los artículos de presupuesto se sobrescribe por el ID de tienda predeterminado

El parche MDVA-44562 corrige el problema en el que el ID de tienda predeterminado anula el ID de tienda de los elementos de presupuesto de las solicitudes de GraphQL. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16. El ID del parche es MDVA-44562. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El ID de tienda de los artículos de presupuesto se anula con el ID de tienda predeterminado para las solicitudes de GraphQL.

<u>Pasos a seguir</u>:

1. Crear una nueva vista de tienda.
1. Cree un nuevo producto simple con diferentes nombres por vista de tienda.
1. Crear un cliente nuevo.
1. Obtenga el token de autorización de cliente.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Cree una nueva cotización para el cliente utilizando el token de autorización.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. Añadir un producto al carro de compras.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. Obtener el contenido del carro de compras para la vista de tienda predeterminada.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Obtener el contenido del carro de compras para la nueva vista de la tienda.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>Resultados esperados</u>:

La respuesta de la vista de la nueva tienda muestra el nombre del producto desde la vista de la nueva tienda.

<u>Resultados reales</u>:

La respuesta de la nueva vista de tienda muestra la configuración del nombre del producto en la vista de tienda predeterminada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
