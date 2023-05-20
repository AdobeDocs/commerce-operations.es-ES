---
title: El [!UICONTROL Redis] pestaña
description: Obtenga información acerca de [!UICONTROL Redis] pestaña de [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# El [!DNL Redis] pestaña

## [!UICONTROL Redis Node summary]

![Resumen del nodo Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

El **[!UICONTROL Redis Node summary]** incluye todos los nodos de un entorno. El ejemplo anterior incluye los nodos para el ensayo compartido. Hay una primaria y dos secundarias en producción y también una primaria y dos secundarias en ensayo.

## [!UICONTROL Redis node detail]

![Detalles del nodo Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

El **[!UICONTROL Redis node detail]** frame indica el entorno, [!DNL Redis] función, versión del software y tamaño del nodo.

## [!UICONTROL Redis node roles timeline]

![Escala de funciones del nodo Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

El **[!UICONTROL Redis node roles timeline]** frame indica la pérdida de [!DNL Redis] servicio en funciones específicas. Si una línea cae, indica que la función concreta que representa la línea ha perdido un nodo o nodos.

## [!UICONTROL Connection to Redis]

![Conexión a Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

El **[!UICONTROL Connection to Redis]** frame muestra el valor net.connectedClients de la variable [!DNL New Relic Redis] datos de ejemplo. Muestra el recuento de conexiones por [!DNL New Relic] aplicación (entorno) y nodo.

## [!UICONTROL Commands per second by node]

![Comandos por segundo por nodo](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

El **[!UICONTROL Commands per second by node]** El marco muestra el [!DNL Redis] comandos por nodo por segundo durante el periodo de tiempo seleccionado.

## [!UICONTROL Redis % of memory used]

![Redis % de memoria utilizada](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

El **[!UICONTROL Redis % of memory used]** frame muestra el porcentaje de memoria máxima utilizado por el [!DNL Redis] servidores.

## [!UICONTROL Redis used memory]

![Memoria usada de Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

El **[!UICONTROL Redis used memory]** La trama muestra el uso de nodos de memoria en GB/MB.

## [!UICONTROL Redis changes since last db save]

![Redis cambios desde el último guardado de la base de datos](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] es residente en memoria y guarda la información en el almacenamiento. El **[!UICONTROL Redis changes since last db save]** frame indica el número de cambios realizados en la memoria desde que se guardó la última base de datos en el almacenamiento. Consulte [Persistencia de Redis](https://redis.io/docs/manual/persistence/) para obtener más información sobre [!DNL Redis's] persistencia.

## [!UICONTROL Redis synchronization from Log]

![Redefine la sincronización desde el registro](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

El **[!UICONTROL Redis synchronization from Log]** frame se centra en los errores encontrados durante la [!DNL Redis] sincronización o errores que se producen debido a problemas de sincronización. Para obtener más información sobre [!DNL Redis], consulte [[!DNL Redis] Documentación](https://redis.io/docs/).
