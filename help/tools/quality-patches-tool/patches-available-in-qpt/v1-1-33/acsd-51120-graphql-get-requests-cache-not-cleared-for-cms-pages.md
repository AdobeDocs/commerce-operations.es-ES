---
title: 'ACSD-51120: la caché de solicitudes de GraphQL GET no se borra para las páginas de CMS que contienen bloques de CMS'
description: Aplique el parche ACSD-51120 para corregir el problema de Adobe Commerce en el que la caché de solicitudes de GraphQL GET no se borra para las páginas de CMS que contienen bloques de CMS.
exl-id: e1b84db0-2441-4729-aeeb-8486a623aebf
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-51120: la caché de solicitudes de GraphQL GET no se borra para las páginas de CMS que contienen bloques de CMS

El parche ACSD-51120 corrige el problema de que la caché de solicitudes de GraphQL GET no se borra para las páginas de CMS que contienen bloques de CMS que se actualizan mediante una actualización de ensayo. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33. El ID del parche es ACSD-51120. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La caché de solicitudes de GraphQL GET no se borra para las páginas de CMS que contienen bloques de CMS que se actualizan mediante una actualización de ensayo.

<u>Pasos a seguir</u>:

1. Cree un bloque de CMS.
1. Incluya el bloque de CMS en una página de CMS mediante [!DNL Page Builder].
1. Recupere la página de CMS utilizando la consulta de GraphQL determinada utilizando una solicitud de GET:

   ```GraphQL
   {
   cmsPage( identifier: "<CMS PAGE IDENTIFIER>") {
       content
       content_heading
       identifier
       meta_description
       meta_keywords
       meta_title
       page_layout
       title
       url_key
   }
   }
   ```

1. Asegúrese de que la respuesta de GraphQL se almacena en caché en [!DNL Varnish].
1. Cree una actualización programada para el bloque.
1. Espere a que se aplique la actualización programada y ejecute el trabajo cron para aplicar la actualización programada.
1. Vuelva a recuperar la página de CMS con la consulta de GraphQL determinada mediante una solicitud de GET.

<u>Resultados esperados</u>:

La respuesta muestra el contenido actualizado.

<u>Resultados reales</u>:

La respuesta sigue mostrando el contenido antiguo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
