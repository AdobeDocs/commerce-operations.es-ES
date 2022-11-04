---
title: AWS OpenSearch
description: Siga estos pasos para configurar el servicio web de AWS OpenSearch para instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: 3692dcfd5b50c2f036b005d40a22db061b9ea5fd
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# AWS OpenSearch

Adobe Commerce y Magento Open Source 2.4.5 admiten el uso de clústeres del servicio OpenSearch de Amazon. Este servicio es el sucesor del servicio Elasticsearch de Amazon. En este tema se describe cómo configurar Commerce para utilizar AWS OpenSearch y cómo migrar datos de un Elasticsearch local o de una instancia OpenSearch a un clúster OpenSearch de AWS.

## Creación de un dominio de servicio de AWS OpenSearch

Primero debe establecer una instancia de OpenSearch en AWS.
Lectura [Creación y administración de dominios del servicio OpenSearch de Amazon](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) para obtener instrucciones detalladas.

## Obtener datos en AWS OpenSearch

Una vez que todo está preparado en AWS, es hora de rellenarlo con datos.

Para instalaciones más pequeñas, se recomienda crear índices directamente en la instancia de AWS por los siguientes motivos:

* Recrear los índices es una operación rápida.
* Puede haber incompatibilidades de versión entre la instancia antigua y la instancia de AWS, que se pueden evitar creando directamente en la instancia de AWS.

Es posible que las instalaciones más grandes deseen considerar la migración de sus índices de datos de la instancia existente a AWS. Aunque esto puede reducir el tiempo de inactividad, sigue habiendo un pequeño riesgo de problemas de incompatibilidad debido a las diferentes versiones entre el antiguo servidor Elasticsearch y AWS.

No es necesario migrar índices, ya que estos se pueden volver a crear fácilmente en la instancia de AWS.
Sin embargo, al migrar índices de datos, asegúrese de que las versiones de Elasticsearch/OpenSearch sean compatibles.

Consulte Amazon [Migración al servicio OpenSearch de Amazon](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) instrucciones para obtener más información.

### Configuración de Commerce para OpenSearch

Los pasos para configurar OpenSearch se tratan en la [Instalación avanzada](../../advanced.md) tema.

Para comprobar que la nueva configuración funciona, pruebe el extremo OpenSearch directamente:

1. Cree un producto en el administrador (por ejemplo: sku=&quot;testproduct1&quot;).
1. Reindexe a través del Administrador.
1. Consulte el extremo OpenSearch (que se encuentra en la interfaz de usuario de AWS):

   Para obtener índices, añada: `/_cat/indices/*?v=true` a la URL:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Para obtener productos del índice, añada: `/magento2docker_product_1/_search?q=*` a la URL:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Recursos adicionales

Para obtener más información, consulte la [Documentación de OpenSearch AWS](https://docs.aws.amazon.com/opensearch-service/index.html).
