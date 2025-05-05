---
title: 'ACSD-63286: los productos asignados al catálogo compartido deben reindexarse manualmente para que aparezcan'
description: Aplique el parche ACSD-63286 para corregir el problema de Adobe Commerce en el que los productos asignados a un catálogo compartido mediante API no aparecen en la tienda hasta que se ejecute un reíndice manual.
feature: Products, REST
role: Admin, Developer
exl-id: 0435c06e-337e-4320-acc6-fa79a3b34008
source-git-commit: e18a41c5abb1cc8b407ff6c188acdeed0e8a7659
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-63286: los productos asignados al catálogo compartido deben reindexarse manualmente para que aparezcan

El parche ACSD-63286 soluciona el problema de que los productos asignados a un catálogo compartido mediante API no aparecen en la tienda hasta que se ejecuta un reíndice manual. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. El ID del parche es ACSD-63286. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando los productos se asignan a un catálogo compartido mediante API, no aparecen en el front-end después de que se ejecuten los trabajos de indexador parcial y de consumidor cron. Sin embargo, sí aparecen después de una reindexación manual completa.

<u>Pasos a seguir</u>:

1. Configurar [!DNL RabbitMQ] como servicio de cola.
1. Cree un catálogo compartido y asígnele una empresa.
1. Cree un producto simple y asígnelo a una categoría.
1. Ejecutar reindexación parcial.

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Utilice la siguiente solicitud de API para asignar el producto creado al catálogo compartido `pub/rest/all/V1/sharedCatalog/<id>/assignProducts`:

   ```
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Ejecute el siguiente cron para borrar las colas y ejecutar el reíndice parcial.

   ```
   bin/magento cron:run --group=consumers
   ```

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Inicie sesión en el front-end como usuario de la compañía.
1. Compruebe la página de categoría de front-end. Los productos recién asignados no son visibles.
1. Ejecute una reindexación manual:

   ```
   bin/magento index:reindex
   ```

<u>Resultados esperados</u>:

El producto aparece en el front-end sin un reíndice manual.

<u>Resultados reales</u>:

El producto aparece en el front-end solo después de reindexar manualmente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
