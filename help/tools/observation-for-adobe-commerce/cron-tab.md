---
title: El [!DNL Cron] pestaña
description: Obtenga información acerca de [!DNL Cron] pestaña de [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# El [!DNL Cron] pestaña

Esta pestaña es un intento de aislar rápidamente los problemas y las causas de [!DNL cron] problemas.

## [!UICONTROL Cron transaction duration in seconds]

![Duración de la transacción Cron en segundos](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

El **[!UICONTROL Cron transaction duration in seconds]** visualizaciones de cuadros [!DNL crons] duración de la transacción en segundos. Esto mostrará las transacciones que tienen tiempos de ejecución largos. Una profundización en APM mostrará más detalles sobre qué consulta puede estar ejecutando la transacción/operación.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![MySQL Non Sleeping Threads por nodo](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

El **[!UICONTROL MySQL Non-Sleeping Threads by Node]** frame muestra los hilos MySQL Non-Sleeping por nodo en el periodo de tiempo seleccionado.

## [!UICONTROL SQL Trace count by path]

![Recuento de seguimiento SQL por ruta](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

El **[!UICONTROL SQL Trace count by path]** frame busca los recuentos de seguimiento de MySQL por ruta, lo que puede ayudar a rastrear las sentencias SQL en un periodo de tiempo seleccionado.

## [!UICONTROL Cron database call]

![Llamada de base de datos Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

El **[!UICONTROL Cron database call]** el marco observa el número de [!DNL crons] llamadas a la base de datos en un periodo de tiempo seleccionado.

## [!UICONTROL Cron schedule table locks]

![Bloqueos de tabla de programación de Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

El **[!UICONTROL Cron schedule table locks]** el marco mira [!DNL cron] programar bloqueos de tabla en un periodo de tiempo seleccionado.

## [!UICONTROL Cron schedule clean cron fired]

![Bloqueos de tabla de programación de Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

El **[!UICONTROL Cron schedule clean cron fired]** el marco observa el número de [!DNL crons] limpiado en un periodo de tiempo seleccionado. Si no se muestran datos en este marco, podría indicar un problema con [!DNL crons] se ejecuta correctamente. Si la variable [!DNL cron] la programación del trabajo no se ha limpiado, [!DNL crons] no se ejecutará de forma óptima y puede tardar más tiempo en ejecutarse.

## [!UICONTROL Cron schedule clean records details table]

![Tabla de detalles de registros limpios de programación Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

El **[!UICONTROL Cron schedule clean records details table]** proporciona detalles sobre el trabajo para limpiar registros de la `cron_schedule` en un periodo seleccionado.

## [!UICONTROL cron_schedule table updates]

![cron_schedule: actualizaciones de tabla](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

El **[!UICONTROL cron_schedule table updates]** el marco observa el número de [!DNL cron] actualizaciones de tabla programadas en un periodo de tiempo seleccionado. Una actividad elevada en la eliminación o actualización de esta tabla puede indicar un problema con [!DNL crons]. Además, [!DNL crons] actualice esta tabla cuando se ejecuten y se completen, de modo que si no hay actividad en esta tabla y no hay actividad en [!DNL crons] configurado, podría haber un problema con [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![Tablas de operaciones del almacén](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

El **[!UICONTROL Datastore Operations Tables]** busca las operaciones de tabla de la base de datos, incluyendo `SELECT`, `DELETE`, y `UPDATE` en un periodo de tiempo seleccionado. Este marco muestra las tablas de base de datos con la frecuencia de operación más alta en ellas.
