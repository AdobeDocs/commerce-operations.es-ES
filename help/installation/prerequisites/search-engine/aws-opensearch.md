---
title: AWS OpenSearch
description: Siga estos pasos para configurar el servicio web AWS OpenSearch para instalaciones locales de Adobe Commerce.
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# AWS OpenSearch

Adobe Commerce 2.4.5 es compatible con el uso de clústeres del servicio OpenSearch de Amazon. Este servicio es el sucesor del servicio Elasticsearch de Amazon. En este tema se describe cómo configurar Commerce para que utilice AWS OpenSearch y cómo migrar datos de una instancia local de Elasticsearch u OpenSearch a un clúster de AWS OpenSearch.

## Crear un dominio de servicio OpenSearch de AWS

Primero debe establecer una instancia de OpenSearch en AWS.
Lea [Creación y administración de dominios del servicio OpenSearch de Amazon](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) para obtener instrucciones detalladas.

## Obtener datos en AWS OpenSearch

Una vez que todo esté preparado en AWS, es hora de rellenarlo con datos.

Para instalaciones más pequeñas, recomendamos que cree índices directamente en la instancia de AWS por los siguientes motivos:

* La recreación de los índices es una operación rápida.
* Puede haber incompatibilidades de versión entre la instancia antigua y la instancia de AWS, que se pueden evitar creando directamente en la instancia de AWS.

Es posible que las instalaciones más grandes deseen considerar la migración de sus índices de datos de la instancia existente a AWS. Aunque esto puede reducir el tiempo de inactividad, sigue existiendo un pequeño riesgo de problemas de incompatibilidad debido a las distintas versiones entre el antiguo servidor de Elasticsearch y AWS.

No es necesario migrar índices, ya que se pueden volver a crear fácilmente en la instancia de AWS.
Sin embargo, al migrar índices de datos, asegúrese de que las versiones de Elasticsearch/OpenSearch sean compatibles.

Consulte las instrucciones de Amazon [Migración al servicio OpenSearch de Amazon](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) para obtener más información.

### Configuración de Commerce para OpenSearch

Los pasos para configurar OpenSearch se tratan en el tema [Instalación avanzada](../../advanced.md).

Para probar que la nueva configuración funciona, pruebe directamente el punto de conexión de OpenSearch:

1. Cree un producto en el Administrador (por ejemplo: sku=&quot;testproduct1&quot;).
1. Reindexe mediante el administrador.
1. Consulte el extremo de OpenSearch (que se encuentra en la interfaz de usuario de AWS):

   Para obtener índices, anexe: `/_cat/indices/*?v=true` a la dirección URL:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Para obtener productos del índice, anexe: `/magento2docker_product_1/_search?q=*` a la dirección URL:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Recursos adicionales

Para obtener más información, consulte la [Documentación de OpenSearch para AWS](https://docs.aws.amazon.com/opensearch-service/index.html).
