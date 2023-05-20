---
title: Cómo usar el [!DNL Observation for Adobe Commerce] empollón
description: Aprenda a utilizar el [!DNL Observation for Adobe Commerce] nerdlet.
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Cómo usar el [!DNL Observation for Adobe Commerce] empollón

## Enfoque general para ver los problemas

Comprobar estados de recursos del entorno:

* Examine el % de **[!UICONTROL Storage Free and MySQL % free storage by node]** marcos.

   * Siga los vínculos del encabezado del marco si ve poco almacenamiento.

* Examine el % de **[!UICONTROL free system memory and Swap memory free in bytes]** marcos.

   * Si estos estados muestran estados de memoria muy bajos, pueden contribuir a que se produzcan problemas.

* Examine la **[!UICONTROL Alerts during the timeframe]** marco.

   * Adobe Commerce en la infraestructura en la nube proporciona [!DNL Managed alerts]. Puede hacer clic en el vínculo del encabezado para ver lo siguiente [!DNL Support Knowledge Base] artículos que le ayudarán a determinar las acciones que debe realizar para las alertas específicas.

* Examine la **[!UICONTROL CPU % by host]** frame: Si muestra un alto uso de la CPU, compruebe el [!DNL Support Knowledge Base] artículo en el encabezado del marco. Compruebe también que las importaciones/exportaciones o las copias de seguridad de la base de datos no se realicen durante los períodos de tráfico máximo.

* Compruebe la **[!UICONTROL Web Traffic volume compared to one week ago]** frame: Si el tráfico es mucho mayor que la semana anterior durante el mismo periodo, ¿se puede explicar (campaña de venta o nuevos productos que se han comercializado, por ejemplo)?
   * Si no se puede explicar un aumento en el tráfico, observe el Tiempo de respuesta promedio (milisegundos) para el entorno de producción. ¿Es diferente el mayor tráfico que contribuye a un tiempo de respuesta de lo normal? Expanda el periodo de tiempo para ver si se trata de una anomalía.
   * ¿El aumento del tráfico afecta a las transacciones web? Compruebe la **[!UICONTROL Response Code]** marco para errores. Si el sitio está caído, puede hacer clic en el `Site Down?` en el encabezado del marco. El marco identificará cualquier error que se esté produciendo y su frecuencia.
   * ¿Ha implementado alguien cambios en su sitio web? El **[!UICONTROL Deployment Log Entries]** frame indicará si se han realizado implementaciones durante el periodo de tiempo del problema. Si el problema se produce inmediatamente después de la implementación, es posible que las actividades de implementación estén agregando carga adicional al sitio (cachés borradas, servicios reiniciados, etc.).
   * ¿Se ha producido un aumento o una reducción de tamaño? Si el sitio se ha convertido temporalmente, es posible que se haya devuelto a su tamaño de clúster original. Si se solicita aumentar la capacidad del sitio, puede producirse un aumento de tamaño. Compruebe la **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** marco. Este marco a veces detecta una interrupción en un nodo en particular. Si ve la disminución de tamaño, puede indicar un problema con uno o más nodos.

* El **[!UICONTROL IP Frequency]** identifica la frecuencia de solicitud de las direcciones IP que se realizan con los servidores de origen (lo que significa que la solicitud no se pudo atender desde [!DNL Fastly] como 74, no se almacenó en caché).

   * Para cualquier [!DNL Fastly] problemas relacionados, consulte **[!UICONTROL Fastly Cache]** marco y seleccione la faceta Error para ver el porcentaje de solicitudes que son errores. Pueden indicar un problema de back-end si coinciden con la carga no web.
   * Si la carga no parece deberse al tráfico web, puede haber errores o una acumulación de solicitudes no web, como consultas lentas o [!DNL crons].

* Compruebe la **[!UICONTROL Database Errors]** marco para errores que pueden coincidir con la cronología del problema o la incidencia.
* Compruebe la **[!UICONTROL Database mysql-slow.log]** para identificar las sentencias SQL que se están produciendo. `INSERT`, `UPDATE`, y `DELETE` Los comandos de pueden tardar un poco si la consulta no está optimizada. Uniforme `SELECT` las instrucciones pueden ser muy ineficientes si se realizan contra tablas grandes.
* **[!UICONTROL PHP States]** y **[!UICONTROL PHP Errors]** Los marcos mostrarán posibles problemas con PHP. El **[!UICONTROL PHP States]** frame mostrará las terminaciones de los procesos de PHP, los inicios y cuándo el servicio alcanza el estado de preparado por nodo. El **[!UICONTROL PHP Errors]** frame puede ayudar a aislar dónde está el problema con PHP, como el tamaño de la memoria, los trabajadores o el número de servidores.
* Para ver la latencia de las transacciones, la tabla Transactions - Avg, Max, Min se puede ordenar por columna para mostrar la duración de transacción de más larga ejecución. Un clúster sobrecargado tendrá duraciones latentes en las transacciones, pero también mostrará anomalías que podrían señalar un problema con un método o [!DNL cron].
* El **[!UICONTROL Cron error]** el marco se mostrará [!DNL cron] bloqueos, errores SQL que pueden estar asociados con [!DNL cron] registros y ensayo compartido [!DNL crons] que pueden estar ejecutándose en entornos de producción cuando hay un entorno de ensayo dedicado.
* El [!UICONTROL ElasticSearch Errors] frame muestra errores que pueden indicar problemas importantes con [!DNL Elasticsearch] consultas, datos o índices.
