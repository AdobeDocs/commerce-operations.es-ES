---
title: "ACSD-53098: Los productos del catálogo compartido no se reflejan en el front-end"
description: Aplique el parche ACSD-53098 para corregir el problema de Adobe Commerce en el que los productos asignados a un catálogo compartido no se reflejan en el front-end al ejecutar un índice parcial.
feature: B2B, Catalog Management, Categories, Products
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-53098: los productos del catálogo compartido no se reflejan en el front-end

El parche ACSD-53098 corrige el problema de que los productos asignados a un catálogo compartido no se reflejan en el front-end al ejecutar un índice parcial. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.38. El ID del parche es ACSD-53098. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos asignados a un catálogo compartido mediante API no aparecen en el front-end después de que el indexador parcial ejecute el trabajo cron, seguido del cron del consumidor.

<u>Pasos a seguir</u>:

1. Configurar [!DNL RabbitMQ] como servicio de cola.
1. Cambie los indizadores al modo **[!UICONTROL Update on Schedule]**.
1. Cree un catálogo compartido y asígnelo a una empresa.
1. Cree un producto simple y asígnelo a una categoría. Ejecute el reindexado parcial:

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Utilice la siguiente solicitud de API para asignar el producto creado al catálogo compartido.

   ```
   pub/rest/all/V1/sharedCatalog/<id>/assignProducts
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Ejecute el siguiente cron para borrar las colas y ejecutar el reíndice parcial:

   `bin/magento cron:run --group=consumers`

   `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`

1. Inicie sesión en el front-end como usuario de la compañía.
1. Compruebe la página de categoría de front-end.

<u>Resultados esperados</u>:

Los productos recién asignados aparecerán en el front-end.

<u>Resultados reales</u>:

Los productos recién asignados no aparecen en el front-end.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
