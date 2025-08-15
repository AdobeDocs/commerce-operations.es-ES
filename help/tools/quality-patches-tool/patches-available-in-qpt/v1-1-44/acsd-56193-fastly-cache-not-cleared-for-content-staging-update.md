---
title: 'La caché ACSD-56193: [!DNL Fastly] no se ha borrado para la actualización del ensayo de contenido'
description: Aplique el parche ACSD-56193 para corregir el problema de Adobe Commerce en el que la caché  [!DNL Fastly] no se borra para la actualización del ensayo de contenido.
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: a702ce22-cc85-4f58-8766-637a1b93d405
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-56193: no se ha borrado la caché de [!DNL Fastly] para la actualización del ensayo de contenido

La revisión ACSD-56193 corrige el problema en el cual la caché [!DNL Fastly] no se borra para la actualización del ensayo de contenido. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44. El ID del parche es ACSD-56193. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se ha borrado la caché [!DNL Fastly/Varnish] para la actualización del ensayo de contenido

<u>Pasos a seguir</u>:

1. Instalar y configurar la caché de [!DNL Varnish].
1. Cree un bloque estático con una actualización programada.
1. Cree una categoría que incruste el bloque estático.
1. Recupere el contenido de la categoría utilizando la siguiente consulta de GraphQL:

   ```GraphQL
      query GetCategories($id: String!) {
         categoryList(filters: { category_uid: { eq: $id } }) 
       {
           meta_title
           meta_keywords
           meta_description
           description
           path
           cms_block {
             content
             identifier
             title
             __typename
           }
           __typename
       }
     }
     {"id":"Mwo="}
   ```

1. Ejecute esta consulta varias veces y asegúrese de que la respuesta se almacena en caché en [!DNL Varnish].
1. Ejecute el cron para aplicar el cambio programado.
1. Vuelva a ejecutar la consulta de GraphQL anterior.
1. Cree una nueva programación para el mismo bloque estático.
1. Repita los pasos numerados del 5 al 9.

<u>Resultados esperados</u>:

El contenido actualizado se devuelve después de que se ejecuten las actualizaciones programadas.

<u>Resultados reales</u>:

El contenido obsoleto se devuelve después de que se ejecuten las actualizaciones programadas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
