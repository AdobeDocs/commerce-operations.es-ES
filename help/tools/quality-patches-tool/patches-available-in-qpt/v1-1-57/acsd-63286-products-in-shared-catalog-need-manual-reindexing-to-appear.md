---
title: 'ACSD-63286: los productos asignados al catálogo compartido deben reindexarse manualmente para que aparezcan'
description: Aplique el parche ACSD-63286 para corregir el problema de Adobe Commerce en el que los productos asignados a un catálogo compartido mediante API no aparecen en la tienda hasta que se ejecute un reíndice manual.
feature: Products, REST
role: Admin, Developer
exl-id: 0435c06e-337e-4320-acc6-fa79a3b34008
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
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
source-wordcount: '424'
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
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando los productos se asignan a un catálogo compartido mediante API, no aparecen en el front-end después de que se ejecuten los trabajos de indexador parcial y de consumidor cron. Sin embargo, sí aparecen después de una reindexación manual completa.

<u>Pasos a seguir</u>:

1. Configurar [!DNL RabbitMQ] como servicio de cola.
1. Cree un catálogo compartido y asígnele una empresa.
1. Cree un producto simple y asígnelo a una categoría.
1. Ejecutar reindexación parcial.

   ```shell
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Utilice la siguiente solicitud de API para asignar el producto creado al catálogo compartido `pub/rest/all/V1/sharedCatalog/<id>/assignProducts`:

   ```json
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Ejecute el siguiente cron para borrar las colas y ejecutar el reíndice parcial.

   ```shell
   bin/magento cron:run --group=consumers
   ```

   ```shell
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Inicie sesión en el front-end como usuario de la compañía.
1. Compruebe la página de categoría de front-end. Los productos recién asignados no son visibles.
1. Ejecute una reindexación manual:

   ```shell
   bin/magento index:reindex
   ```

<u>Resultados esperados</u>:

El producto aparece en el front-end sin un reíndice manual.

<u>Resultados reales</u>:

El producto aparece en el front-end solo después de reindexar manualmente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
