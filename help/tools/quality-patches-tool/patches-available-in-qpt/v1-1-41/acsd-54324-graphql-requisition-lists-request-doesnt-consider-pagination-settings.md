---
title: 'ACSD-54324: La solicitud de GraphQL request_lists no tiene en cuenta la configuración de paginación'
description: Aplique el parche ACSD-54324 para solucionar el problema de Adobe Commerce en el que la solicitud de GraphQL "request_lists" no tiene en cuenta la configuración de paginación y devuelve todos los resultados.
feature: B2B, Customers, GraphQL
role: Admin, Developer
exl-id: 60f82602-1cfc-4523-a50d-46af5d5f10d9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '431'
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
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La solicitud de GraphQL `requisition_lists` no tiene en cuenta la configuración de paginación y devuelve todos los resultados.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador y vaya a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

   * Establezca *[!UICONTROL Enable Requisition List]* en *Sí*.

1. Inicie sesión en el front-end y vaya a **[!UICONTROL My Requisition Lists]** desde el menú superior o desde **[!UICONTROL My Account]** y cree varias solicitudes (por ejemplo: 7).
1. Después de generar un token de cliente, ejecute la siguiente consulta de GraphQL `requisition_lists` para el cliente.

   * Asegúrese de que el tamaño de página es inferior al número total de listas de solicitudes creadas (por ejemplo: 4)

   ```
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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
