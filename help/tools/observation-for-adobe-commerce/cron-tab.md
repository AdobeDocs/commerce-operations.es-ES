---
title: La  [!DNL Cron] pestaña
description: Obtenga información acerca de la ficha  [!DNL Cron] de [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# La ficha [!DNL Cron]

Esta ficha es un intento de aislar rápidamente los problemas y las causas de [!DNL cron] problemas.

## [!UICONTROL Cron transaction duration in seconds]

![Duración de la transacción Cron en segundos](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

El fotograma **[!UICONTROL Cron transaction duration in seconds]** muestra la duración de la transacción [!DNL crons] en segundos. Esto mostrará las transacciones que tienen tiempos de ejecución largos. Una profundización en APM mostrará más detalles sobre qué consulta puede estar ejecutando la transacción/operación.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![MySQL Non Sleeping Threads by Node](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

El fotograma **[!UICONTROL MySQL Non-Sleeping Threads by Node]** muestra los subprocesos MySQL no suspendidos por nodo en el periodo de tiempo seleccionado.

## [!UICONTROL SQL Trace count by path]

![Recuento de seguimiento SQL por ruta](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

El marco **[!UICONTROL SQL Trace count by path]** examina los recuentos de seguimiento de MySQL por ruta, lo que puede ayudar a rastrear las sentencias SQL en un periodo de tiempo seleccionado.

## [!UICONTROL Cron database call]

![Llamada a base de datos Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

El marco **[!UICONTROL Cron database call]** observa el número de llamadas de [!DNL crons] a la base de datos en un intervalo de tiempo seleccionado.

## [!UICONTROL Cron schedule table locks]

![Bloqueos de tabla de programación Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

El fotograma **[!UICONTROL Cron schedule table locks]** observa [!DNL cron] bloqueos de tabla de programación en un intervalo de tiempo seleccionado.

## [!UICONTROL Cron schedule clean cron fired]

![Bloqueos de tabla de programación Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

El fotograma **[!UICONTROL Cron schedule clean cron fired]** observa el número de [!DNL crons] limpiados en un fotograma seleccionado. Si no se muestran datos en este marco, podría indicar un problema con [!DNL crons], que se ejecuta correctamente. Si no se limpia la programación del trabajo [!DNL cron], [!DNL crons] no se ejecutará de manera óptima y puede tardar más tiempo en ejecutarse.

## [!UICONTROL Cron schedule clean records details table]

![Tabla de detalles de registros limpios de programación de Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

La tabla **[!UICONTROL Cron schedule clean records details table]** proporciona detalles sobre el trabajo para limpiar registros de la tabla `cron_schedule` en un intervalo de tiempo seleccionado.

## [!UICONTROL cron_schedule table updates]

![actualizaciones de tabla cron_schedule](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

El fotograma **[!UICONTROL cron_schedule table updates]** observa el número de [!DNL cron] actualizaciones de tabla programadas en un intervalo de tiempo seleccionado. Una actividad alta en la eliminación o actualización de esta tabla puede indicar un problema con [!DNL crons]. Además, [!DNL crons] actualizará esta tabla cuando se ejecuten y se completen, de modo que si no hay actividad en esta tabla y hay [!DNL crons] configuradas, podría haber un problema con [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![Tablas de operaciones del almacén de datos](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

**[!UICONTROL Datastore Operations Tables]** consulta las operaciones de tabla de base de datos, incluidas `SELECT`, `DELETE` y `UPDATE` en un intervalo de tiempo seleccionado. Este marco muestra las tablas de base de datos con la frecuencia de operación más alta en ellas.
