---
title: 'ACSD-55334: las etiquetas no se traducen mediante diccionarios de traducción en la respuesta de GraphQL'
description: Aplique el parche ACSD-55334 para corregir el problema de Adobe Commerce en el que las etiquetas no se traducen mediante diccionarios de traducción en la respuesta de GraphQL.
feature: Categories, GraphQL
role: Admin, Developer
exl-id: c22e5007-c661-49d4-90b7-dcee9b97c823
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# ACSD-55334: las etiquetas no se traducen mediante diccionarios de traducción en la respuesta de GraphQL

El parche ASCD-55334 corrige el problema de que las etiquetas no se traducen mediante diccionarios de traducción en la respuesta de GraphQL. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43. El ID de parche es ASCD-55334. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las etiquetas no se traducen mediante diccionarios de traducción en la respuesta de GraphQL.

<u>Pasos a seguir</u>:

1. Instale un paquete de idioma.
1. Enviar una solicitud GraphQL como:

   ```GrapQL
   query {
       products(filter: {}, pageSize: 25, sort: {}) {
           aggregations {
               label
           }
           total_count
       }
   }
   ```

1. Compruebe la respuesta.

<u>Resultados esperados</u>:

La etiqueta *[!UICONTROL Category]* está traducida.

<u>Resultados reales</u>:

La etiqueta *[!UICONTROL Category]* no está traducida.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
