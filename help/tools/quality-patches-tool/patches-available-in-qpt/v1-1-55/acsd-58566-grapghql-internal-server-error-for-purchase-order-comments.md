---
title: 'ACSD-58566: error interno del servidor de GraphQL para comentarios de pedidos de compra'
description: Aplique el parche ACSD-58566 para solucionar el problema de Adobe Commerce donde GraphQL devuelve un error interno del servidor al consultar el campo created_at en la mutación addPurchaseOrderComment.
feature: B2B, Purchase Orders, GraphQL
role: Admin, Developer
source-git-commit: 3b8cc44ea8d71982b8a2eb76d9d7ec2a5c3180b0
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-58566: error interno del servidor de GraphQL para comentarios de pedidos de compra

El parche ACSD-58566 corrige el problema en el que al consultar el campo `created_at` en la mutación `addPurchaseOrderComment` se devuelve un valor nulo en lugar de la fecha y hora esperadas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. El ID del parche es ACSD-58566. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

GraphQL devuelve un error interno del servidor al consultar el campo `created_at` en la mutación `addPurchaseOrderComment`.

<u>Requisitos previos</u>:

Se instalan los módulos B2B y se activan los pedidos de empresa y compra.

<u>Pasos a seguir</u>:

1. Genere un token de cliente para un usuario de la compañía.
1. Realice la siguiente secuencia de solicitudes de GraphQL:
   1. Crear un *carro* con `customerCart`.
   1. Agregar un producto al *carro* mediante `addProductsToCart`.
   1. Realice el pedido con `placePurchaseOrder`.
   1. Agregar un comentario al pedido de compra usando `addPurchaseOrderComment`.

   ```
   mutation {
       addPurchaseOrderComment(
           input: { purchase_order_uid: "MQ==", comment: "Looks good to me" }
   ) {
           comment {
               uid
               created_at
               author {
                   firstname
                   lastname
                   email
               }
               text
           }
       }
   }
   ```

<u>Resultados esperados</u>:

El campo `created_at` devuelve la fecha y hora del comentario del pedido de compra.

<u>Resultados reales</u>:

Muestra null en lugar de la fecha `created_at`.

```
{
  "errors": [
    {
      "message": "Internal server error",
      "locations": [
        {
          "line": 10,
          "column": 1
        }
      ],
      "path": [
        "addPurchaseOrderComment",
        "comment",
        "created_at"
      ]
    }
  ],
  "data": {
    "addPurchaseOrderComment": null
  }
}
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

[[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
