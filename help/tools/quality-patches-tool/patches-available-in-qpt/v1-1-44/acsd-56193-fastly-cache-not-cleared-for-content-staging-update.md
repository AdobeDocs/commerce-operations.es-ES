---
title: 'ACSD-56193: no se ha borrado la caché de [!DNL Fastly] para la actualización del ensayo de contenido'
description: Aplique el parche ACSD-56193 para corregir el problema de Adobe Commerce en el que la caché [!DNL Fastly] no se borra para la actualización del ensayo de contenido.
feature: Cache, GraphQL, Staging
role: Admin, Developer
exl-id: a702ce22-cc85-4f58-8766-637a1b93d405
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 0054e3a7-7067-583b-bfd2-ab39dada9ab5
    internal-label: Staging
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '404'
ht-degree: 0%
---
# ACSD-56193: no se ha borrado la caché de [!DNL Fastly] para la actualización del ensayo de contenido

La revisión ACSD-56193 corrige el problema en el cual la caché [!DNL Fastly] no se borra para la actualización del ensayo de contenido. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.44. El ID del parche es ACSD-56193. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
