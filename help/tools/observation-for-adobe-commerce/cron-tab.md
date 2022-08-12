---
title: '"El [!UICONTROL Cron] tab"'
description: Obtenga información sobre [!UICONTROL Cron] pestaña [!DNL Observation for Adobe Commerce].
source-git-commit: 3c1e50b3bff1bd2b2760e2e763173275161b0044
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# La variable [!UICONTROL Cron] ficha

Esta pestaña es un intento de aislar rápidamente los problemas y las causas de los problemas cron.

## [!UICONTROL Cron transaction duration in seconds]

![Duración de la transacción cron en segundos](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

La variable **[!UICONTROL Cron transaction duration in seconds]** frame muestra la duración de la transacción crons en segundos. Esto mostrará las transacciones que tienen largos tiempos de ejecución. Una profundización en APM mostrará más detalles sobre qué consulta se está ejecutando la transacción/operación.

## [!UICONTROL MySql Non-Sleeping Threads by Node]

![Subprocesos no duraderos MySql por nodo](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

La variable **[!UICONTROL MySql Non-Sleeping Threads by Node]** frame muestra los subprocesos no duraderos de MySql por nodo en el intervalo de tiempo seleccionado.

## [!UICONTROL SQL Trace count by path]

![Recuento de seguimiento SQL por ruta](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

La variable **[!UICONTROL SQL Trace count by path]** frame observa los recuentos de rastreo de MySql por ruta, lo que puede ayudar a rastrear las instrucciones SQL en un intervalo de tiempo seleccionado.

## [!UICONTROL Cron database call]

![Llamada a la base de datos Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

La variable **[!UICONTROL Cron database call]** frame observa el número de crons que llaman a la base de datos en un intervalo de tiempo seleccionado.

## [!UICONTROL Cron schedule table locks]

![Bloqueos de tabla de programación cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

La variable **[!UICONTROL Cron schedule table locks]** frame observa los bloqueos de tabla de programación de cron en un periodo de tiempo seleccionado.

## [!UICONTROL Cron schedule clean cron fired]

![Bloqueos de tabla de programación cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

La variable **[!UICONTROL Cron schedule clean cron fired]** frame busca el número de crons limpiados en un intervalo de tiempo seleccionado. Si no se muestran datos en este fotograma, podría indicar un problema con crons que se ejecuta correctamente. Si no se limpia la programación de trabajos cron, los crons no se ejecutarán de forma óptima y puede tardar más en ejecutarse.

## [!UICONTROL Cron schedule clean records details table]

![Tabla de detalles de registros limpios de programación de cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

La variable **[!UICONTROL Cron schedule clean records details table]** la tabla proporciona detalles sobre el trabajo para limpiar registros de la `cron_schedule` en un intervalo de tiempo seleccionado.

## [!UICONTROL cron_schedule table updates]

![actualizaciones de tabla cron_schedule](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

La variable **[!UICONTROL cron_schedule table updates]** frame busca el número de actualizaciones de tabla programadas de cron en un intervalo de tiempo seleccionado. La alta actividad en la eliminación o actualización de esta tabla puede indicar un problema con crons. Además, crons actualiza esta tabla cuando se ejecutan y completan, por lo que si no hay actividad en esta tabla y hay crons configurados, podría haber un problema con crons.

## [!UICONTROL Datastore Operations Tables]

![Tablas de operaciones del almacén de datos](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

La variable **[!UICONTROL Datastore Operations Tables]** busca las operaciones de tablas de base de datos, incluyendo `SELECT`, `DELETE`y `UPDATE` en un intervalo de tiempo seleccionado. Este marco muestra las tablas de la base de datos con la frecuencia de operación más alta contra ellas.
