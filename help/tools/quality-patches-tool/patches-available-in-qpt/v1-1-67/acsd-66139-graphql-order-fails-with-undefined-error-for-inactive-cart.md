---
title: 'ACSD-66139: el pedido de GraphQL falla con un error INDEFINIDO para el carro de compras inactivo'
description: Aplique el parche ACSD-66139 para solucionar el problema de Adobe Commerce donde, al realizar un pedido de un carro de compras inexistente o inactivo, GraphQL devuelve un código de error UNDEFINED en lugar de uno específico cuando se traducen mensajes de error.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: 5a1a94ca-f274-4098-8b44-d3f1a0ea65a1
source-git-commit: 8681dd706e614f86bbee36c182b47491ec707196
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-66139: el pedido de GraphQL falla con el error &quot;UNDEFINED&quot; para el carro de compras inactivo

El parche ACSD-66139 corrige el problema en el que, al realizar un pedido de un carro de compras inexistente o inactivo, GraphQL devuelve un código de error *UNDEFINED* en lugar de uno específico cuando se traducen mensajes de error. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. El ID del parche es ACSD-66139. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` al ión más reciente y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: Buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

GraphQL devuelve un código de error *UNDEFINED* en lugar de uno específico al realizar un pedido de un carro de compras inexistente o inactivo, si se traduce el mensaje de error.

<u>Pasos a seguir</u>:

1. Agregue `app/i18n/Magento/de_DE/de_DE.csv` e incluya la siguiente traducción de cadena de error:

```
"Could not find a cart with ID ""%masked_cart_id""","Oh noo, we have an UNDEFINED issue, see!",module,Magento_QuoteGraphQl
```

1. En el panel de administración, vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** > **[!UICONTROL Create Store View]** para crear una vista de tienda.
1. Establezca **[!UICONTROL Code]** en *prueba*.
1. Asignar idioma de `german` a la vista de tienda recién creada.
1. Ejecutar `setup:upgrade` y `setup:static-content:deploy -f`.
1. Ejecute la siguiente consulta de GraphQL con el encabezado `Store:test`:

```
mutation {
    placeOrder(input: { cart_id: "test" }) {
        orderV2 {
            id
            number
        }
    }
}
```

<u>Resultados esperados</u>:

Respuesta de error correcta:

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "CART_NOT_FOUND"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

<u>Resultados reales</u>:

El `error_code` devuelto es *UNDEFINED*:

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "UNDEFINED"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
