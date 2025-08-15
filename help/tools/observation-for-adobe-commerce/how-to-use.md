---
title: Cómo usar  [!DNL Observation for Adobe Commerce] nerdlet
description: Aprenda a utilizar el  [!DNL Observation for Adobe Commerce] nerdlet.
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Cómo usar el nerdlet [!DNL Observation for Adobe Commerce]

## Enfoque general para ver los problemas

Comprobar estados de recursos del entorno:

* Examine el % de **[!UICONTROL Storage Free and MySQL % free storage by node]** fotogramas.

   * Siga los vínculos del encabezado del marco si ve poco almacenamiento.

* Examine el % de **[!UICONTROL free system memory and Swap memory free in bytes]** fotogramas.

   * Si estos estados muestran estados de memoria muy bajos, pueden contribuir a que se produzcan problemas.

* Examine el marco **[!UICONTROL Alerts during the timeframe]**.

   * Adobe Commerce en la infraestructura en la nube proporciona [!DNL Managed alerts]. Puede hacer clic en el vínculo del encabezado para ver [!DNL Support Knowledge Base] artículos que le ayudarán a determinar las acciones por su parte para alertas específicas.

* Examine el fotograma **[!UICONTROL CPU % by host]**: si muestra una alta utilización de CPU, busque el fotograma en el artículo [!DNL Support Knowledge Base] del encabezado. Compruebe también que las importaciones/exportaciones o las copias de seguridad de la base de datos no se realicen durante los períodos de tráfico máximo.

* Compruebe el marco **[!UICONTROL Web Traffic volume compared to one week ago]**: si el tráfico es mucho mayor que la semana anterior durante el mismo período, ¿se puede explicar (campaña de venta o nuevos productos que se han comercializado, por ejemplo)?
   * Si no se puede explicar un aumento en el tráfico, observe el Tiempo de respuesta promedio (milisegundos) para el entorno de producción. ¿Es diferente el mayor tráfico que contribuye a un tiempo de respuesta de lo normal? Expanda el periodo de tiempo para ver si se trata de una anomalía.
   * ¿El aumento del tráfico afecta a las transacciones web? Compruebe si hay errores en el marco **[!UICONTROL Response Code]**. Si el sitio no está operativo, puede hacer clic en el vínculo `Site Down?` del encabezado del marco. El marco identificará cualquier error que se esté produciendo y su frecuencia.
   * ¿Ha implementado alguien cambios en su sitio web? El marco **[!UICONTROL Deployment Log Entries]** indicará si se han realizado implementaciones durante el periodo de tiempo del problema. Si el problema se produce inmediatamente después de la implementación, es posible que las actividades de implementación estén agregando carga adicional al sitio (cachés borradas, servicios reiniciados, etc.).
   * ¿Se ha producido un aumento o una reducción de tamaño? Si el sitio se ha convertido temporalmente, es posible que se haya devuelto a su tamaño de clúster original. Si se solicita aumentar la capacidad del sitio, puede producirse un aumento de tamaño. Compruebe el fotograma **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]**. Este marco a veces detecta una interrupción en un nodo en particular. Si ve la disminución de tamaño, puede indicar un problema con uno o más nodos.

* La pestaña **[!UICONTROL IP Frequency]** identifica la frecuencia de solicitud de las direcciones IP que se realizan con los servidores de origen (lo que significa que la solicitud no se pudo entregar desde [!DNL Fastly] porque 74 no se almacenó en caché).

   * Para cualquier problema relacionado con [!DNL Fastly], compruebe el marco **[!UICONTROL Fastly Cache]** y seleccione la faceta Error para ver el porcentaje de solicitudes que son errores. Pueden indicar un problema de back-end si coinciden con la carga no web.
   * Si la carga no parece deberse al tráfico web, puede haber errores o una acumulación de solicitudes que no sean web, como consultas lentas o [!DNL crons].

* Compruebe si hay errores en el fotograma **[!UICONTROL Database Errors]** que puedan coincidir con la cronología del problema.
* Compruebe el marco **[!UICONTROL Database mysql-slow.log]** para identificar las sentencias SQL que se están produciendo. Los comandos `INSERT`, `UPDATE` y `DELETE` pueden tardar un poco si la consulta no está optimizada. Incluso las instrucciones `SELECT` pueden ser muy ineficientes si se realizan en tablas grandes.
* **[!UICONTROL PHP States]** y **[!UICONTROL PHP Errors]** fotogramas mostrarán posibles problemas con PHP. El marco **[!UICONTROL PHP States]** mostrará las terminaciones del proceso de PHP, los inicios y cuando el servicio alcance el estado de preparado por nodo. El marco **[!UICONTROL PHP Errors]** puede ayudar a aislar dónde está el problema con PHP, como el tamaño de la memoria, los trabajadores o el número de servidores.
* Para ver la latencia de las transacciones, la tabla Transactions - Avg, Max, Min se puede ordenar por columna para mostrar la duración de transacción de más larga ejecución. Un clúster sobrecargado tendrá duraciones latentes en las transacciones, pero también mostrará anomalías que podrían indicar un problema con un método o [!DNL cron].
* El marco **[!UICONTROL Cron error]** mostrará [!DNL cron] bloqueos, errores SQL que pueden estar asociados con [!DNL cron] registros y ensayo compartido [!DNL crons] que pueden estar ejecutándose en entornos de producción cuando hay un entorno de ensayo dedicado.
* El marco [!UICONTROL ElasticSearch Errors] muestra errores que pueden indicar problemas importantes con [!DNL Elasticsearch] consultas, datos o índices.
