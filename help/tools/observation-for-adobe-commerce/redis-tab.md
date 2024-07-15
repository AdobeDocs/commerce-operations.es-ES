---
title: La ficha [!UICONTROL Redis]
description: Obtenga información acerca de la ficha [!UICONTROL Redis] de  [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: 06f015139683f319f11317f8d7f0029cbd2548e3
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# La ficha [!DNL Redis]

## [!UICONTROL Redis Node summary]

![Resumen del nodo Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

**[!UICONTROL Redis Node summary]** incluye todos los nodos de un entorno. El ejemplo anterior incluye los nodos para el ensayo compartido. Hay una primaria y dos secundarias en producción y también una primaria y dos secundarias en ensayo.

## [!UICONTROL Redis node detail]

![Detalle del nodo Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

El marco **[!UICONTROL Redis node detail]** indica el entorno, el rol [!DNL Redis], la versión del software y el tamaño del nodo.

## [!UICONTROL Redis node roles timeline]

![Escala de tiempo de funciones de nodo de Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

El fotograma **[!UICONTROL Redis node roles timeline]** indica la pérdida del servicio [!DNL Redis] en roles particulares. Si una línea cae, indica que la función concreta que representa la línea ha perdido un nodo o nodos.

## [!UICONTROL Connection to Redis]

![Conexión a Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

El marco **[!UICONTROL Connection to Redis]** muestra el valor net.connectedClients de los datos de ejemplo [!DNL New Relic Redis]. Muestra el recuento de conexiones por aplicación (entorno) y nodo [!DNL New Relic].

## [!UICONTROL Commands per second by node]

![Comandos por segundo por nodo](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

El fotograma **[!UICONTROL Commands per second by node]** muestra los comandos [!DNL Redis] por nodo por segundo durante el periodo de tiempo seleccionado.

## [!UICONTROL Redis % of memory used]

![Redis % de memoria usada](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

El fotograma **[!UICONTROL Redis % of memory used]** muestra el porcentaje de memoria máxima que utilizan los servidores [!DNL Redis].

## [!UICONTROL Redis used memory]

![Redis utilizó memoria](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

El fotograma **[!UICONTROL Redis used memory]** muestra el uso de memoria del nodo en GB/MB.

## [!UICONTROL Redis changes since last db save]

![Redis cambios desde el último db save](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] reside en la memoria y guarda la información en el almacenamiento. El marco **[!UICONTROL Redis changes since last db save]** indica el número de cambios en la memoria que se han producido desde que se guardó la última base de datos en el almacenamiento. Consulte [Redis persistence](https://redis.io/docs/latest/operate/oss_and_stack/management/persistence/) para obtener más información sobre la persistencia de [!DNL Redis's].

## [!UICONTROL Redis synchronization from Log]

![Reanuda la sincronización desde el registro](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

El marco **[!UICONTROL Redis synchronization from Log]** se centra en los errores encontrados durante la sincronización de [!DNL Redis] o en los errores que se producen debido a problemas de sincronización. Para obtener más información sobre [!DNL Redis], consulte [[!DNL Redis] Documentación](https://redis.io/docs/).
