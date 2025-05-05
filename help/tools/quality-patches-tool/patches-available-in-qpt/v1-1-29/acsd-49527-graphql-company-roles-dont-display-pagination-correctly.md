---
title: 'ACSD-49527: Los roles de compañía de GraphQL no muestran la paginación correctamente'
description: Aplique el parche ACSD-49527 para corregir el problema de Adobe Commerce en el que los roles de compañía de GraphQL no muestran la paginación correctamente.
feature: B2B, GraphQL, Companies, Roles/Permissions
role: Admin
exl-id: 2fbc80ad-5a15-471b-99f0-213609ab3978
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-49527: Los roles de compañía de GraphQL no muestran la paginación correctamente

El parche ACSD-49527 corrige el problema de que los roles de compañía de GraphQL no muestran la paginación correctamente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-49527. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los roles de compañía de GraphQL no muestran la paginación correctamente.

<u>Pasos a seguir</u>:

1. Habilitar empresa B2B.
1. En la tienda, cree una nueva compañía.
1. Cree al menos dos nuevas funciones para esta compañía, de modo que haya un total de tres funciones, ya que una función es la predeterminada.
1. Envíe una solicitud de GraphQL para obtener los roles que especifican [!UICONTROL pageSize]: 2.

   ```GraphQL
   query {
       company {
           roles(pageSize: 2, currentPage: 1) {
               items {
                   name
               }
               total_count
               page_info {
                   total_pages
                   current_page
               }
           }
       }
   } 
   ```

1. Compruebe la respuesta de GraphQL.

<u>Resultados esperados</u>:

`total_count: 3` y `total_pages: 2` se devuelven en la respuesta de GraphQL.

<u>Resultados reales</u>:

`total_count: 2` y `total_pages: 1` se devuelven en la respuesta de GraphQL.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
