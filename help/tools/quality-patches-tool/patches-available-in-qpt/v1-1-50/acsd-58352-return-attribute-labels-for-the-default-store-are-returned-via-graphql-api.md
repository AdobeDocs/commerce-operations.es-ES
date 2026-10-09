---
title: 'ACSD-58352: las etiquetas de atributo devueltas para el almacén predeterminado se devuelven mediante la API [!DNL GraphQL]'
description: Aplique el parche ACSD-58352 para corregir el problema de Adobe Commerce donde las etiquetas de atributos de retorno para el almacén predeterminado se devuelven mediante la API [!DNL GraphQL] cuando se especifica una vista de almacén no predeterminada en el encabezado de la solicitud.
feature: GraphQL, Returns
role: Admin, Developer
exl-id: e513039e-42cd-4dac-963b-3068ba8bf7ee
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
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
source-wordcount: '417'
ht-degree: 0%
---
# ACSD-58352: las etiquetas de atributo devueltas para el almacén predeterminado se devuelven mediante la API [!DNL GraphQL]

La revisión ACSD-58352 corrige el problema en el que las etiquetas de atributos de retorno para el almacén predeterminado se devuelven mediante la API [!DNL GraphQL] cuando se especifica una vista de almacén no predeterminada en el encabezado de la solicitud. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50. El ID del parche es ACSD-58352. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las etiquetas de atributo devueltas para la tienda predeterminada se devuelven mediante la API [!DNL GraphQL].

<u>Pasos a seguir</u>:

1. Habilite **[!UICONTROL Return Merchandising Authorization]**.
1. Crear un *[!UICONTROL Additional Store]* y un *[!UICONTROL Store View]* en el sitio web predeterminado.
1. Edite el atributo de retorno **[!UICONTROL Reason for Return]** y agregue etiquetas para todas las vistas de tiendas.
1. Crear un *[!UICONTROL Order]*.
1. Cree un(a) *[!UICONTROL Return]* para ese pedido. Asegúrese de que *[!UICONTROL Return]* se encuentre en el estado *[!UICONTROL Pending]*.
1. Enviar una consulta de cliente [!DNL GraphQL] con el valor especificado no predeterminado [!UICONTROL Store View] en el encabezado:

   ```graphql
   query {
       customer {
           returns {
               items {
                   items {
                       custom_attributes {
                           label
                           value
                       }
                   }
               }
           }
       }
   }
   ```

1. Observe la respuesta.

<u>Resultados esperados</u>

Las etiquetas de devolución de la respuesta [!DNL GraphQL] son para [!UICONTROL Store View] establecido en el encabezado de la solicitud.

<u>Resultados reales</u>:

Las etiquetas devueltas en la respuesta [!DNL GraphQL] son para el valor predeterminado [!UICONTROL Store View].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
