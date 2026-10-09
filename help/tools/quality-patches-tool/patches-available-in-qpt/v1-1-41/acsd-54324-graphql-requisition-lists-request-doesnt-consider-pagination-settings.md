---
title: 'ACSD-54324: La solicitud de GraphQL request_lists no tiene en cuenta la configuración de paginación'
description: Aplique el parche ACSD-54324 para solucionar el problema de Adobe Commerce en el que la solicitud de GraphQL "request_lists" no tiene en cuenta la configuración de paginación y devuelve todos los resultados.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 60f82602-1cfc-4523-a50d-46af5d5f10d9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '453'
ht-degree: 0%
---
# ACSD-54324: la solicitud de GraphQL `requisition_lists` no tiene en cuenta la configuración de paginación

El parche ACSD-54324 corrige el problema en el que la solicitud de GraphQL `requisition_lists` no tiene en cuenta la configuración de paginación y devuelve todos los resultados. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.41. El ID del parche es ACSD-54324. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La solicitud de GraphQL `requisition_lists` no tiene en cuenta la configuración de paginación y devuelve todos los resultados.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador y vaya a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Establezca *[!UICONTROL Enable Requisition List]* en *Sí*.

1. Inicie sesión en el front-end y vaya a **[!UICONTROL My Requisition Lists]** desde el menú superior o desde **[!UICONTROL My Account]** y cree varias solicitudes (por ejemplo: 7).
1. Después de generar un token de cliente, ejecute la siguiente consulta de GraphQL `requisition_lists` para el cliente.

   * Asegúrese de que el tamaño de página es inferior al número total de listas de solicitudes creadas (por ejemplo: 4)

   ```graphql
   {
   customer {
   requisition_lists(pageSize: 4, currentPage: 1) {
   items
   
   { uid name description updated_at items_count }
   total_count
   }
   }
   }
   ```

1. Observe que el valor del campo `total_count` muestra 7, cuando debería mostrar 4.

   El número de elementos también muestra 7 cuando debería ser igual que *tamaño de página*.

<u>Resultados esperados</u>:

* El número que aparece como *tamaño de página* se devuelve en `total_count` y no el número total de registros.
* El número de elementos es el mismo que el *tamaño de página*.

<u>Resultados reales</u>:

El número total de registros se devuelve en `total_count`, incluso si se menciona *tamaño de página*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
