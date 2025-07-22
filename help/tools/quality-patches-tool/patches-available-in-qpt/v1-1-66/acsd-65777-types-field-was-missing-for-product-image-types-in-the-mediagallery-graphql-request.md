---
title: 'ACSD-65777: falta el campo "tipos" para los tipos de imagen de producto en la solicitud de GraphQL de MediaGallery'
description: Aplique el parche ACSD-65777 para corregir el problema de Adobe Commerce en el que faltaba el campo "tipos" para los tipos de imagen de producto en la solicitud de GraphQL de MediaGallery.
feature: GraphQL, Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: 4f0ac23d70eed6d2ea0441d4c8aa8cfc3138ff04
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---


# ACSD-65777: falta el campo **[!UICONTROL types]** para los tipos de imagen de producto en la solicitud de GraphQL `MediaGallery`

La revisión ACSD-65777 corrige el problema en el que faltaba el campo **[!UICONTROL types]** para los tipos de imagen de producto en la solicitud de GraphQL `MediaGallery`. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. El ID del parche es ACSD-65777. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Falta el campo **[!UICONTROL types]** para los tipos de imagen de producto al recuperar datos de medios mediante la solicitud de GraphQL `MediaGallery`.

<u>Pasos a seguir</u>:

1. Cree un producto.
1. Cargue una imagen en el producto.
1. Recupere los datos de medios con la siguiente GraphQL.

   ```
   query{
     products(search:"",filter:{sku:{eq:"p1"}})\{
       items{
         media_gallery{
           disabled
           label
           position
           url
         }
         media_gallery_entries\{
           types
         }
       }
     }
   }
   ```

<u>Resultados esperados</u>:

La interfaz de GraphQL `media_gallery` debe incluir el campo **[!UICONTROL types]**.

<u>Resultados reales</u>:

El `media_gallery` no contiene el campo de medios **[!UICONTROL types]**.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
