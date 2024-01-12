---
title: El [!UICONTROL CDN] pestaña
description: Obtenga información acerca de [!UICONTROL CDN] pestaña de [!DNL Observation for Adobe Commerce].
exl-id: db22bbca-2033-4e9a-8799-b47d84bdd720
feature: Configuration, Observability
source-git-commit: e753528a1d74eda0a1393e2cc455f33f529db739
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# El [!UICONTROL CDN] pestaña

Esta pestaña contiene información que se centra en [!DNL content delivery network (CDN)]. En el caso de Adobe Commerce Cloud, este es el [!DNL Fastly] servicio.

## [!UICONTROL HIT rate]

![Tasa de aciertos](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

El **[!UICONTROL HIT rate]** frame muestra el número de solicitudes almacenables en caché que resultaron en [!UICONTROL HITS] en el último minuto. Esto indica un almacenamiento en caché correcto. La flecha a la derecha muestra el porcentaje por encima o por debajo de la misma hora hace una semana.

## [!UICONTROL HIT Processing]

![Procesamiento de VISITAS](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

Esta **[!UICONTROL HIT processing]** muestra el número de solicitudes almacenables en caché que resultaron en [!UICONTROL HITS] durante la semana.

## [!UICONTROL MISS rate]

![Tasa de PÉRDIDA](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

Esta **[!UICONTROL MISS rate]** muestra el número de errores de solicitudes almacenables en caché en el último minuto. Se produce un error cuando la solicitud no se almacena en caché y debe pasarse al servidor de origen para servir el contenido. El valor a la derecha es la comparación del aumento/disminución con el número de minutos por minuto una semana antes.

## [!UICONTROL MISS time]

![Hora de PÉRDIDA](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![Proporción de visitas](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![Porcentaje de error](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

El **[!UICONTROL Error Percentage]** El cuadro muestra el valor del porcentaje de ERROR de las solicitudes y muestra el aumento/disminución relativo en comparación con el mismo tiempo de la semana anterior.

## [!UICONTROL Total Requests]

![Total de solicitudes](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![Tasa de error](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![Respuesta promedio de caché rápida para el período de tiempo seleccionado en segundos](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

Este fotograma muestra la duración en segundos de las solicitudes que se pueden almacenar en caché, lo que significa que si `cache_response` es un [!UICONTROL MISS], muestra el promedio de respuestas en caché perdidas durante el tiempo seleccionado.

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![Respuesta promedio de caché rápida para el período de tiempo seleccionado en segundos faceteado por POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

*GOLPEAR* en este contexto hace referencia a un punto de presencia (POP) configurado para funcionar como grupo para el almacenamiento en caché. Consulte [Puntos de presencia](https://developer.fastly.com/learning/concepts/pop/).

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![Ancho de banda total (todos los POP) durante el lapso de tiempo seleccionado, en comparación con hace 1 semana (% de aumento/disminución)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![Solicitudes: desde el lapso de tiempo seleccionado en comparación con hace una semana](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

Este marco es similar al cuadro de resumen de [!UICONTROL Total Requests] en la parte superior, pero muestra los recuentos de solicitudes de las semanas anteriores. Estas son todas las solicitudes, no solo solicitudes almacenables en caché (donde `is_cacheable` es true).

## [!UICONTROL Response Count]

![Recuento de respuestas](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![Ancho de banda por POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![Las 5 direcciones URL principales (códigos de estado 5xx o 3xx)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

El **[!UICONTROL Top 5 URLs]** La vista muestra las 5 direcciones URL principales que experimentan respuestas de error 5xx o 3xx. Debido a la restricción de espacio, deberá pasar el ratón sobre la dirección URL para ver el código de error específico asociado a esa dirección URL. (ejemplo en el cuadro rojo de la figura anterior).

## [!UICONTROL Top 25 URLs (200 status)]

![Principales 25 direcciones URL (estado 200)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

El **[!UICONTROL Top 25 URLs]** frame muestra las direcciones URL que arrojaron un estado de 200 por recuento durante el periodo de tiempo seleccionado.

## [!UICONTROL Duration by Response Status]

![Duración por estado de respuesta](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

El **[!UICONTROL Duration by Response Status]** El gráfico muestra las respuestas de error por recuento durante el periodo de tiempo seleccionado, faceteadas por el código de estado de error.

## [!UICONTROL Duration by Response Status, top 25 urls]

![Duración por estado de respuesta, 25 direcciones URL principales](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

El **[!UICONTROL Duration by Response Status, top 25 URLs]** El gráfico muestra las 25 direcciones URL principales por la duración de la respuesta en segundos. Es posible que tenga que pasar el ratón sobre la dirección URL para ver la ruta completa. Además, para eliminar todas las direcciones URL excepto una, haga clic en esa dirección URL. A continuación, puede volver a añadir otras direcciones URL haciendo clic en ellas individualmente. Si desea eliminar direcciones URL individuales, puede mantener pulsada la tecla y hacer clic en cada dirección URL para eliminarlas del gráfico.

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![Duración por estado de respuesta, los 25 estados principales distintos de 200](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

El **[!UICONTROL Duration by Response Status, top 25 non-200 status]** El gráfico es similar al último, excepto que se centra en códigos de estado distintos de 200 o en códigos de estado de error. Se muestra el código de error y, a continuación, la dirección URL. Es posible que tenga que pasar el ratón sobre la dirección URL para ver la ruta completa. Además, para eliminar todas las direcciones URL excepto una, haga clic en esa dirección URL. A continuación, puede volver a añadir otras direcciones URL haciendo clic en ellas individualmente. Si desea eliminar direcciones URL individuales, puede mantener pulsada la tecla y hacer clic en cada dirección URL para eliminarlas del gráfico.

## [!UICONTROL Error Count by POP timeline]

![Recuento de errores por cronología POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

El **[!UICONTROL Error Count by POP timeline]** El gráfico muestra el recuento de los estados de error a lo largo de la cronología del periodo de tiempo seleccionado, faceteada por el código de error.

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![Duración por estado de respuesta, 25 direcciones IP de cliente principales, estado distinto de 200](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

El **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** El gráfico muestra las direcciones IP por la duración promedio en el periodo de tiempo seleccionado donde hubo códigos de error de estado.

## [!UICONTROL IP Frequency]

![Frecuencia IP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

El **[!UICONTROL IP Frequency]** frame cuenta los estados (&quot;MISS&quot; y &quot;PASS&quot;) para cada IP desde el [!DNL Fastly] registros. Las solicitudes web con estos estados llegarán al servidor de origen y añadirán carga al servidor. Muestra las veinte direcciones principales en frecuencia. Este marco se puede utilizar para detectar ataques IP o fuentes de carga pesada en un sitio web. Este gráfico también está presente en la pestaña Resumen y se coloca aquí para facilitar la comparación con más detalles en la [!DNL Fastly] información de registro mostrada en esta ficha.
