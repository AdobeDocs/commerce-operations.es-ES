---
title: 'ACSD-63883: corrigiendo &grave;items_count&grave; incorrecto en  [!DNL GraphQL] respuesta para [!UICONTROL Requisition List]'
description: Aplique el parche ACSD-63883 para corregir el problema en el que [!UICONTROL Requisition List] devuelve un valor "items_count" incorrecto en la respuesta  [!DNL GraphQL] s.
feature: B2B, GraphQL
role: Admin, Developer
exl-id: 8946d7fb-558a-4867-a843-a61715416f25
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# ACSD-63883: corrigiendo `items_count` incorrecto en la respuesta [!DNL GraphQL] para [!UICONTROL Requisition List]

El parche ACSD-63883 corrige el problema en el que **[!UICONTROL Requisition List]** devuelve un `items_count` incorrecto en la respuesta [!DNL GraphQL]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. El ID del parche es ACSD-63883. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce B2B 1.5.3.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El **[!UICONTROL Requisition List]** devuelve un `items_count` incorrecto en la respuesta [!DNL GraphQL].


<u>Pasos a seguir</u>:

1. Habilitar la característica **[!UICONTROL Requisition List]** de B2B.
1. Cree algunos productos.
1. Cree una cuenta de cliente.
1. Haga clic en **[!UICONTROL Create new Requisition List]**.
1. Envíe la solicitud de mutación `addProductsToRequisitionList` [!DNL GraphQL] con un producto para agregarlo al [!UICONTROL Requisition List].

   ```
   mutation addProductsToRequisitionList(
   $requisitionListUid: ID!
   $requisitionListItems: [RequisitionListItemsInput!]!
   ) {
   addProductsToRequisitionList(
   requisitionListUid: $requisitionListUid
   requisitionListItems: $requisitionListItems
   ) {
   requisition_list
   { uid name description items_count }
   }
   }
   ```

1. Envíe la solicitud de mutación `addProductsToRequisitionList` [!DNL GraphQL] con otros tres productos para agregarlos a [!UICONTROL Requisition List].
1. Compruebe `items_count` en la respuesta.

**Resultados esperados**:

* `items_count`: se debe devolver 4 en la respuesta.

**Resultados reales**:

* `items_count`: 2 se devolvió en la respuesta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
