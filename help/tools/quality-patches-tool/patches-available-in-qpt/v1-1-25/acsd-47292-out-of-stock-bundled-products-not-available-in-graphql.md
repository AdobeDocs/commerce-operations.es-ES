---
title: 'ACSD-47292: los productos agrupados agotados no están disponibles en la respuesta de GraphQL'
description: Aplique el parche ACSD-47292 para solucionar el problema de Adobe Commerce en el que los productos agrupados sin existencias no están disponibles en la respuesta de GraphQL aunque "mostrar productos sin existencias" esté establecido en Sí.
feature: Admin Workspace, Categories, GraphQL, Orders, Products
role: Admin
exl-id: 3b8114a3-cc45-4d65-af74-cb3e905d7f75
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# ACSD-47292: los productos agrupados agotados no están disponibles en la respuesta de GraphQL

El parche ACSD-47292 corrige el problema en el que los productos empaquetados sin existencias no están disponibles en la respuesta de GraphQL aunque [!UICONTROL Display Out-of-Stock Products] esté establecido en *[!UICONTROL Yes]*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25. El ID del parche es ACSD-47292. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos agrupados de los que no quedan existencias no están disponibles en la respuesta de GraphQL aunque [!UICONTROL Display Out-of-Stock Products] esté establecido en *[!UICONTROL Yes]*.

<u>Pasos a seguir</u>:

1. Vaya a Adobe Commerce Admin > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** y establezca [!UICONTROL Display Out-of-Stock Products] en *[!UICONTROL Yes]*.
1. Cree dos productos simples, s1 y s2.
1. Haga que s1 esté agotado y no sea visible individualmente y que s2 esté disponible y no sea visible individualmente y asígnelos a una categoría.
1. Cree un producto agrupado con al menos una opción de producto y asigne s1 y s2 a esta opción (tipo de entrada &quot;RadioButton&quot;).
1. Guarde el producto agrupado y asígnelo a una categoría.
1. Vaya a la tienda y abra este producto agrupado. Verá que la opción s1, que no tiene existencias, está atenuada pero visible.
1. Enviar una solicitud GraphQL:

```GraphQL
{
  categoryList(filters: { ids: { in: ["3"] } }) {
    id
    name
    products(pageSize: 8, sort: { position: ASC }) {
      total_count
      items {
        id
        sku
        name
        ... on BundleProduct {
          url_key
          items {
            title
            sku
            options {
              quantity
              position
              is_default
              product {
                id
                name
                sku
              }
            }
          }
        }
      }
    }
  }
}
```

<u>Resultados esperados</u>:

La opción de paquete s1 aparece en la respuesta de GraphQL porque [!UICONTROL Display Out-of-Stock Products] está establecido en *[!UICONTROL Yes]* y está visible en la tienda.

<u>Resultados reales</u>:

La opción de paquete s1 no aparece en la respuesta de GraphQL.

```GraphQL
"items": [
                                {
                                    "title": "oo1",
                                    "sku": "bundle2",
                                    "options": [
                                        {
                                            "quantity": 1,
                                            "position": 2,
                                            "is_default": false,
                                            "product": {
                                                "id": 2,
                                                "name": "s2",
                                                "sku": "s2"
                                            }
                                        }
                                    ]
                                }
                            ]
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
