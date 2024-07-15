---
title: La ficha [!UICONTROL Elasticsearch]
description: Obtenga información acerca de la ficha [!UICONTROL Elasticsearch] de  [!DNL Observation for Adobe Commerce].
exl-id: e98d351d-b3b1-47bc-bc0d-f96ba9ec2b80
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# La ficha [!UICONTROL Elasticsearch]

## [!UICONTROL Cluster Status Summary]:

![Resumen del estado del clúster](../../assets/tools/cluster-status-summary.jpg)

Durante el periodo de tiempo seleccionado, el fotograma **[!UICONTROL Cluster Status Summary]** muestra los estados de color por los que ha pasado el clúster [!DNL Elasticsearch]. En este ejemplo, durante el periodo de tiempo seleccionado, el clúster estaba en estado Verde una vez y en estado Amarillo una vez durante el periodo de tiempo seleccionado.

## [!UICONTROL Active Primary Shards]

![Recursos compartidos principales activos](../../assets/tools/active-primary-shards.jpg)

El marco **[!UICONTROL Active Primary Shards]** muestra los diferentes números en función del número de fragmentos principales activos para el servicio [!DNL Elasticsearch] de la cuenta seleccionada.

De [!DNL Elasticsearch]: la guía definitiva [2.x]:

&quot;En [Índices actualizables dinámicamente](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html), explicamos que un uso compartido es un índice Lucene y que un índice [!DNL Elasticsearch] es una colección de elementos compartidos. La aplicación habla con un índice y [!DNL Elasticsearch] enruta las solicitudes a los fragmentos correspondientes. Un fragmento es la unidad de escala. El índice más pequeño que puede tener es uno con un solo uso compartido. Esto puede ser más que suficiente para sus necesidades (un solo fragmento puede contener muchos datos), pero limita su capacidad de escalado&quot;.

Cuando se crea un índice, hay varios fragmentos creados con él. De forma predeterminada, se asignan cinco fragmentos principales a cada nuevo índice, lo que significa que un índice se puede distribuir en cinco nodos (un fragmento por nodo). También hay fragmentos de réplica. Se utilizan principalmente para failover. Los fragmentos de réplicas pueden servir solicitudes de lectura.

## [!UICONTROL Active Shards in Cluster]

![Recursos compartidos activos en el clúster](../../assets/tools/active-shards-in-cluster.jpg)

El fotograma **[!UICONTROL Active Shards in Cluster]** muestra el número total de particiones principales y de réplica en un clúster [!DNL Elasticsearch].

## [!UICONTROL Index health - this will show the index name and color status]

![Estado del índice](../../assets/tools/index-health.jpg)

Este marco muestra el nombre del índice y el recuento del estado del color del índice. Al desplazarse hacia abajo en la tabla, verá el mismo nombre de índice con los estados de color amarillo y rojo. El número que sigue al nombre de índice 27 es el recuento del color del estado. Si es cero, no había instancias del índice en ese estado de color durante los periodos de tiempo seleccionados.

## [!UICONTROL Elasticsearch Status by node information]

![Estado del Elasticsearch](../../assets/tools/elasticsearch-status-by-node.jpg)

El marco **[!UICONTROL Elasticsearch Status by node information]** muestra el estado del clúster [!DNL Elasticsearch] por color y por nodo. Esto ayuda a indicar qué nodo del clúster [!DNL Elasticsearch] devuelve qué estado durante el periodo de tiempo seleccionado.

## [!UICONTROL Elasticsearch index information]

![Información del índice del Elasticsearch](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

La tabla **[!UICONTROL Elasticsearch index information]** muestra el nombre del índice, en qué nodo se encuentra, el número de documentos indexados, el estado del índice y el tamaño del índice en MB en un momento determinado.

## [!UICONTROL Elasticsearch process CPU %]

![CPU de proceso de Elasticsearch](../../assets/tools/elasticsearch-process-cpu.jpg)

El fotograma **[!UICONTROL Elasticsearch process CPU %]** muestra el porcentaje de CPU del proceso por el proceso [!DNL Elasticsearch] durante el periodo de tiempo seleccionado.

## [!UICONTROL Elasticsearch Memory garbage collection]

![Basura de memoria Elasticsearch](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] es un proceso Java. Si se queda sin memoria asignada, iniciará la recolección de elementos no utilizados para liberar memoria. Si la recolección de elementos no utilizados es frecuente, esto indica que puede haber demasiados índices o fragmentos para la memoria asignada. Puede haber una oportunidad de limpiar los índices y fragmentos o [!DNL Elasticsearch] puede necesitar más memoria.

## [!UICONTROL Elasticsearch Index information]

![Información del índice de Elasticsearch](../../assets/tools/elasticsearch-index-information-2.jpg)

A medida que se crean y actualizan los índices, su estado puede cambiar.

## [!UICONTROL Elasticsearch Index Size]

![Tamaño de índice del Elasticsearch](../../assets/tools/elasticsearch-index-size.jpg)

El fotograma **[!UICONTROL Elasticsearch Index Size]** indica el nombre y el tamaño del índice en el periodo de tiempo seleccionado. Puede indicar problemas con la indexación de un sitio.

## [!UICONTROL Elasticsearch Errors]

![Errores Del Elasticsearch](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)

El marco **[!UICONTROL Elasticsearch Errors]** muestra errores con [!DNL Elasticsearch], como la falta de espacio, el cambio del estado Amarillo a Rojo, cuando se produce un error en todos los fragmentos, cuando hay problemas de parámetros con las búsquedas, errores de versión y cuando todos los nodos no están disponibles.

## [!UICONTROL Elasticsearch Unassigned Shards]:

![Recursos compartidos sin asignar de Elasticsearch](../../assets/tools/elasticsearch-unassigned-shards.jpg)

Los fragmentos sin asignar harán que un grupo pase del estado Verde al estado Amarillo.
