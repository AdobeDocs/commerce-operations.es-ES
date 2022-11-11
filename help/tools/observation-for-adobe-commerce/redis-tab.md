---
title: "El [!UICONTROL Redis] tab"
description: Obtenga información sobre [!UICONTROL Redis] pestaña [!DNL Observation for Adobe Commerce].
source-git-commit: f4379d0b89a6ea6d2f2a5a02c505581d4d54708f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# La variable [!DNL Redis] ficha

## [!UICONTROL Redis Node summary]

![Resumen del nodo de redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

La variable **[!UICONTROL Redis Node summary]** incluye todos los nodos de un entorno. El ejemplo anterior incluye los nodos para el ensayo compartido. Hay una primaria y dos secundarias en producción y también una primaria y dos secundarias en ensayo.

## [!UICONTROL Redis node detail]

![Detalles del nodo de Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

La variable **[!UICONTROL Redis node detail]** frame indica el entorno, [!DNL Redis] función, versión del software y tamaño del nodo.

## [!UICONTROL Redis node roles timeline]

![Línea de tiempo de las funciones de los nodos de Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

La variable **[!UICONTROL Redis node roles timeline]** frame indica la pérdida de [!DNL Redis] en funciones específicas. Si una línea cae, indica que la función concreta que representa la línea ha perdido uno o varios nodos.

## [!UICONTROL Connection to Redis]

![Conexión a Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

La variable **[!UICONTROL Connection to Redis]** frame muestra el valor net.connectClients de la variable [!DNL New Relic Redis] datos de ejemplo. Muestra el número de conexiones por [!DNL New Relic] aplicación (entorno) y nodo.

## [!UICONTROL Commands per second by node]

![Comandos por segundo por nodo](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

La variable **[!UICONTROL Commands per second by node]** muestra el [!DNL Redis] comandos por nodo por segundo en el intervalo de tiempo seleccionado.

## [!UICONTROL Redis % of memory used]

![Redis % de memoria utilizada](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

La variable **[!UICONTROL Redis % of memory used]** frame muestra el porcentaje de memoria máxima utilizado por el [!DNL Redis] servidores.

## [!UICONTROL Redis used memory]

![Memoria utilizada de Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

La variable **[!UICONTROL Redis used memory]** frame muestra el uso del nodo de memoria en GB/MB.

## [!UICONTROL Redis changes since last db save]

![Modifica los cambios desde el último almacenamiento de la base de datos](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] reside en la memoria y guarda la información en el almacenamiento. La variable **[!UICONTROL Redis changes since last db save]** frame indica el número de cambios en la memoria que se han producido desde que se guardó en el almacenamiento la última base de datos. Consulte [Persistencia de Redis](https://redis.io/docs/manual/persistence/) para obtener más información sobre [!DNL Redis's] persistencia.

## [!UICONTROL Redis synchronization from Log]

![Redis synchronization from Log](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

La variable **[!UICONTROL Redis synchronization from Log]** frame se centra en los errores encontrados durante [!DNL Redis] sincronización o errores que se producen debido a problemas de sincronización. Para obtener más información, consulte [!DNL Redis], consulte [[!DNL Redis] Documentación](https://redis.io/docs/).
