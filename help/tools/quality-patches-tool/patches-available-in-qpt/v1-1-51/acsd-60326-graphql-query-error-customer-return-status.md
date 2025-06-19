---
title: 'ACSD-60326: la consulta de GraphQL sobre el estado del cliente [!UICONTROL Returns] genera un error'
description: Aplique el parche ACSD-60326 para corregir el problema de Adobe Commerce en el que se produce un error en la consulta de GraphQL para el estado del cliente [!UICONTROL Returns].
feature: GraphQL, Returns, Customers
role: Admin, Developer
exl-id: 5cfd7e0d-8703-43a0-86d3-e69612347534
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# ACSD-60326: la consulta de GraphQL sobre el estado del cliente [!UICONTROL Returns] genera un error

El parche ACSD-60326 corrige el problema en el que se produce un error en la consulta de GraphQL para el estado del cliente [!UICONTROL Returns]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51. El ID del parche es ACSD-60326. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La consulta de GraphQL sobre el estado del cliente [!UICONTROL Returns] genera un error.

<u>Pasos a seguir</u>:

1. Inicialice una instancia nueva con datos de ejemplo.
1. En la barra lateral *[!UICONTROL Admin]*, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]** y establezca **[!UICONTROL Enable RMA on Storefront]** en *Sí*.
1. Vaya a **[!UICONTROL Sales]** > **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** y rellene la dirección.
1. Cambie la contraseña del cliente `roni_cost@example.com`.
1. Inicie sesión en el panel de administración y realice un pedido para el cliente `roni_cost@example.com` con los siguientes productos:
   * *WSH12-32-Red*
   * *WSH12-32-Púrpura*
   * *WSH12-32-Green*
1. Crear un *[!UICONTROL Invoice]* y *[!UICONTROL Shipment]* para este pedido.
1. Seleccione **[!UICONTROL Create Returns]**.
1. Vaya a **[!UICONTROL Return Items]** > **[!UICONTROL Add Items]** y:
   * Seleccione *WSH12-32-Red* y *WSH12-32-Purple*
   * Haga clic **[!UICONTROL Add Selected Products to returns]**:
      * Conjunto **[!UICONTROL Requested]** = *1*
      * Establecer **[!UICONTROL Return Reason]** en *Fuera de servicio*
      * Definir **[!UICONTROL Item Condition]** en *Abierto*
      * Definir **[!UICONTROL Resolution]** en *Reembolso*
   * Haga clic en **[!UICONTROL Submit Returns]**.
1. Abra **[!UICONTROL Returns]** y seleccione **[!UICONTROL Return Items]** a la izquierda.
   * Set **[!UICONTROL Authorized]** = *1* para ambos productos
   * Establecer **[!UICONTROL Status]** como *Autorizado* para *WSH12-32-Purple*
   * Establecer **[!UICONTROL Status]** como *Denegado* para *WSH12-32-Red*
   * Haga clic **[!UICONTROL Save]**
1. Cree un nuevo pedido con los mismos productos.
1. Crear un(a) *[!UICONTROL Invoice]*, *[!UICONTROL Shipment]* y *[!UICONTROL Returns]* para los mismos productos. Autorice ambos y continúe hasta el final del proceso [!UICONTROL Returns].
1. Genere un token de cliente con la siguiente consulta de GraphQL:

   ```GraphQL
    mutation {
     generateCustomerToken(email: "roni_cost@example.com", password: "password") {
       token
      }
   }
   ```

1. Autorice con el token recibido y realice la siguiente consulta:

   ```
   {
   customer {
       returns(pageSize: 20, currentPage: 1) {
        total_count
           items {
               uid
               number
               status
               created_at
           }
       }
   }
   }
   ```

<u>Resultados esperados</u>:

La consulta no muestra ningún error. El estado de la segunda devolución no es *null*.

<u>Resultados reales</u>:

La consulta devuelve un error interno del servidor:

```
    {
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 8,
                    "column": 5
                }
            ],
            "path": [
                "customer",
                "returns",
                "items",
                1,
                "status"
            ]
        }
    ],
    "data": {
        "customer": {
            "returns": {
                "total_count": 2,
                "items": [
                    {
                        "uid": "MQ==",
                        "number": "000000001",
                        "status": "PARTIALLY_AUTHORIZED",
                        "created_at": "2024-07-09 10:35:55"
                    },
                    {
                        "uid": "Mg==",
                        "number": "000000002",
                        "status": null,
                        "created_at": "2024-07-09 10:50:02"
                    }
                ]
            }
        }
    }
    } 
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
