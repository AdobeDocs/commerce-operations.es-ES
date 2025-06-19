---
title: 'ACSD-60538: los atributos no se muestran correctamente si el producto está deshabilitado en [!UICONTROL All Store Views]'
description: Aplique el parche ACSD-60538 para solucionar el problema de Adobe Commerce donde, si un producto está deshabilitado en *Todas las vistas de tienda* y solo está habilitado en ámbitos específicos de vista de tienda, los atributos del producto no se muestran correctamente en la respuesta de GraphQL, lo que provoca que el producto no se muestre correctamente.
feature: Attributes, GraphQL
role: Admin, Developer
exl-id: 2ea9de11-b750-4ab6-9cc7-e940e1791f22
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-60538: los atributos no se muestran correctamente si el producto está deshabilitado en *[!UICONTROL All Store Views]*

La revisión ACSD-60538 corrige el problema en el cual si un producto está deshabilitado en *[!UICONTROL All Store Views]* y habilitado solo en ámbitos específicos de vista de tienda, los atributos del producto no se muestran correctamente en la respuesta de GraphQL, lo que provoca que el producto no se muestre correctamente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51. El ID del parche es ACSD-60538. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Si un producto está deshabilitado en *[!UICONTROL All Store Views]* y habilitado solamente en ámbitos específicos de vista de tienda, los atributos del producto no se muestran correctamente en la respuesta de GraphQL, lo que provoca que el producto no se muestre correctamente.

<u>Requisitos previos</u>:

Módulo de inventario instalado.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con el atributo *color* y tres productos secundarios (*azul*, *negro* y *marrón*).
1. Deshabilite dos productos secundarios asociados (*azul* y *negro*) en el ámbito *[!UICONTROL All Store Views]*.
1. Ir al ámbito **[!UICONTROL Store View]**.
1. Habilite los productos secundarios (*azul* y *negro*) en el ámbito *[!UICONTROL Store View]*.
1. Ejecute la siguiente solicitud de GraphQL:

   ```GraphQL
   {
     products(filter: { sku: { eq: "SKU" } }) {
       items {
           ... on ConfigurableProduct {
             configurable_options {
               attribute_id,
               attribute_code,
            values {
             value_index
             label
           }
       }
       variants {
         product {
           sku
         }
         attributes {
           label
           code
           value_index
          }
         }
        }
       }
      }
     }  
   ```

<u>Resultados esperados</u>:

La respuesta de GraphQL incluye los valores de atributo del producto secundario asociado que está deshabilitado en *[!UICONTROL All Store Views]* y habilitado en el ámbito *[!UICONTROL Store View]*.

<u>Resultados reales</u>:

La respuesta de GraphQL tiene valores de atributo vacíos para el producto secundario asociado cuando el producto está deshabilitado en *[!UICONTROL All Store Views]* y habilitado en el ámbito *[!UICONTROL Store View]*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
