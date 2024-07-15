---
title: La ficha [!UICONTROL CDN]
description: Obtenga información acerca de la ficha [!UICONTROL CDN] de  [!DNL Observation for Adobe Commerce].
exl-id: db22bbca-2033-4e9a-8799-b47d84bdd720
feature: Configuration, Observability
source-git-commit: e753528a1d74eda0a1393e2cc455f33f529db739
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# La ficha [!UICONTROL CDN]

Esta ficha contiene información centrada en [!DNL content delivery network (CDN)]. En el caso de Adobe Commerce Cloud, este es el servicio [!DNL Fastly].

## [!UICONTROL HIT rate]

![Tasa de visitas](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

El fotograma **[!UICONTROL HIT rate]** muestra el número de solicitudes almacenables en caché que resultaron en [!UICONTROL HITS] en el último minuto. Esto indica un almacenamiento en caché correcto. La flecha a la derecha muestra el porcentaje por encima o por debajo de la misma hora hace una semana.

## [!UICONTROL HIT Processing]

![Procesamiento de visita](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

Este cuadro **[!UICONTROL HIT processing]** muestra el número de solicitudes almacenables en caché que resultaron en [!UICONTROL HITS] durante la semana.

## [!UICONTROL MISS rate]

![VELOCIDAD DE INCUMPLIMIENTO](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

Este cuadro **[!UICONTROL MISS rate]** muestra el número de solicitudes que no se pudieron almacenar en caché en el último minuto. Se produce un error cuando la solicitud no se almacena en caché y debe pasarse al servidor de origen para servir el contenido. El valor a la derecha es la comparación del aumento/disminución con el número de minutos por minuto una semana antes.

## [!UICONTROL MISS time]

![HORA DE INCUMPLIMIENTO](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![Proporción de visitas](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![Porcentaje de error](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

El cuadro **[!UICONTROL Error Percentage]** muestra el valor del porcentaje de ERROR de las solicitudes y muestra el aumento/disminución relativo en comparación con el mismo tiempo de la semana anterior.

## [!UICONTROL Total Requests]

![Solicitudes totales](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![Tasa de error](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![Respuesta promedio de caché rápida para el período de tiempo seleccionado en segundos](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

Este fotograma muestra la duración en segundos de las solicitudes almacenables en caché, lo que significa que si un(a) `cache_response` es un(a) [!UICONTROL MISS], muestra el promedio de respuestas en caché perdidas durante el tiempo seleccionado.

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![Respuesta promedio de caché rápida para el período de tiempo seleccionado en segundos faceteado por POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

*POP* en este contexto hace referencia a un punto de presencia (POP) configurado para funcionar como un grupo de almacenamiento de caché. Ver [Puntos de presencia](https://developer.fastly.com/learning/concepts/pop/).

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![Ancho de banda total (todos los POP) durante el lapso de tiempo seleccionado, en comparación con hace una semana (% de aumento/disminución)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![Solicitudes - Desde el lapso de tiempo seleccionado comparado con una semana atrás](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

Este fotograma es similar al cuadro de resumen de [!UICONTROL Total Requests] en la parte superior, pero muestra los recuentos de solicitudes de las semanas anteriores. Todas estas son solicitudes, no solo solicitudes almacenables en caché (donde `is_cacheable` es verdadero).

## [!UICONTROL Response Count]

![Recuento de respuestas](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![Ancho de banda por POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![Cinco direcciones URL principales (códigos de estado 5xx o 3xx)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

La vista **[!UICONTROL Top 5 URLs]** muestra las cinco direcciones URL principales que están experimentando respuestas de error 5xx o 3xx. Debido a la restricción de espacio, deberá pasar el ratón sobre la dirección URL para ver el código de error específico asociado a esa dirección URL. (ejemplo en el cuadro rojo de la figura anterior).

## [!UICONTROL Top 25 URLs (200 status)]

![25 direcciones URL principales (estado 200)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

El fotograma **[!UICONTROL Top 25 URLs]** muestra las direcciones URL que devolvieron un estado de 200 por recuento durante el intervalo de tiempo seleccionado.

## [!UICONTROL Duration by Response Status]

![Duración por estado de respuesta](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

El gráfico **[!UICONTROL Duration by Response Status]** muestra las respuestas de error por recuento durante el periodo de tiempo seleccionado, faceteado por el código de estado de error.

## [!UICONTROL Duration by Response Status, top 25 urls]

![Duración por estado de respuesta, 25 direcciones URL principales](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

El gráfico **[!UICONTROL Duration by Response Status, top 25 URLs]** muestra las 25 direcciones URL principales según la duración de la respuesta en segundos. Es posible que tenga que pasar el ratón sobre la dirección URL para ver la ruta completa. Además, para eliminar todas las direcciones URL excepto una, haga clic en esa dirección URL. A continuación, puede volver a añadir otras direcciones URL haciendo clic en ellas individualmente. Si desea eliminar direcciones URL individuales, puede mantener pulsada la tecla y hacer clic en cada dirección URL para eliminarlas del gráfico.

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![Duración por estado de respuesta, principales 25 estados distintos de 200](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

El gráfico **[!UICONTROL Duration by Response Status, top 25 non-200 status]** es similar al último, excepto que se centra en códigos de estado que no son 200 o en códigos de estado de error. Se muestra el código de error y, a continuación, la dirección URL. Es posible que tenga que pasar el ratón sobre la dirección URL para ver la ruta completa. Además, para eliminar todas las direcciones URL excepto una, haga clic en esa dirección URL. A continuación, puede volver a añadir otras direcciones URL haciendo clic en ellas individualmente. Si desea eliminar direcciones URL individuales, puede mantener pulsada la tecla y hacer clic en cada dirección URL para eliminarlas del gráfico.

## [!UICONTROL Error Count by POP timeline]

![Recuento de errores por escala de tiempo POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

El gráfico **[!UICONTROL Error Count by POP timeline]** muestra el recuento de los estados de error a lo largo de la cronología del periodo de tiempo seleccionada, faceteada por el código de error.

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![Duración por estado de respuesta, 25 direcciones IP de cliente principales, estado no 200](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

El gráfico **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** muestra las direcciones IP según la duración promedio en el periodo de tiempo seleccionado en el que hubo códigos de error de estado.

## [!UICONTROL IP Frequency]

![Frecuencia IP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

El fotograma **[!UICONTROL IP Frequency]** cuenta los estados (&quot;MISS&quot; y &quot;PASS&quot;) para cada IP de los registros [!DNL Fastly]. Las solicitudes web con estos estados llegarán al servidor de origen y añadirán carga al servidor. Muestra las veinte direcciones principales en frecuencia. Este marco se puede utilizar para detectar ataques IP o fuentes de carga pesada en un sitio web. Este gráfico también está presente en la ficha Resumen y se coloca aquí para facilitar la comparación con más detalles sobre la información de registro [!DNL Fastly] que se muestra en esta ficha.
