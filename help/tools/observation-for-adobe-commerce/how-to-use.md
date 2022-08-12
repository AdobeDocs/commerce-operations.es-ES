---
title: '"Cómo usar la variable [!DNL Observation for Adobe Commerce] nerdlet"'
description: Aprenda a utilizar la variable [!DNL Observation for Adobe Commerce] nerdlet.
source-git-commit: 69bcb755c3c1f9a820856ac69ce12eb85c686213
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# Cómo usar la variable [!DNL Observation for Adobe Commerce] nerdlet

## Enfoque general para examinar las cuestiones

Compruebe los estados de los recursos de entorno:

* Examine el % de **[!UICONTROL Storage Free and MySQL % free storage by node]** marcos.

   * Siga los vínculos del encabezado del marco si observa un almacenamiento bajo.

* Examine el % de **[!UICONTROL free system memory and Swap memory free in bytes]** marcos.

   * Si estos estados de memoria son muy bajos, pueden contribuir a problemas.

* Examine el **[!UICONTROL Alerts during the timeframe]** cuadro.

   * Adobe Commerce proporciona infraestructura en la nube [!DNL Managed alerts]. Puede hacer clic en el vínculo del encabezado para ver [!DNL Support Knowledge Base] artículos que ayudarán a determinar acciones de su parte para alertas específicas.

* Examine el **[!UICONTROL CPU % by host]** cuadro: Si está mostrando una alta utilización de la CPU, compruebe el [!DNL Support Knowledge Base] artículo en el encabezado del marco. Además, asegúrese de que las importaciones/exportaciones de bases de datos o las copias de seguridad no se realicen durante los períodos de tráfico máximo.

* Marque la **[!UICONTROL Web Traffic volume compared to one week ago]** cuadro: Si el tráfico es mucho mayor que el de la semana anterior durante el mismo período, ¿se puede explicar (campaña de venta o nuevos productos que se han comercializado, por ejemplo)?
   * Si no se puede explicar un aumento en el tráfico, observe el tiempo de respuesta promedio (milisegundos) para el entorno de producción. ¿El mayor tráfico contribuye a un tiempo de respuesta diferente al normal? Expanda el periodo para ver si se trata de una anomalía.
   * ¿El aumento del tráfico afecta a las transacciones web? Marque la **[!UICONTROL Response Code]** para errores. Si el sitio está inactivo, puede hacer clic en la *[!UICONTROL Site Down?]* en el encabezado del marco. El marco identificará cualquier error que se esté produciendo y su frecuencia.
   * ¿Ha implementado alguien cambios en el sitio web? La variable **[!UICONTROL Deployment Log Entries]** indicará si se han realizado implementaciones durante el periodo de tiempo del problema. Si el problema es inmediato después de la implementación, puede ser que las actividades de implementación estén agregando carga adicional al sitio (caché borrada, servicios reiniciados, etc.).
   * ¿Se ha producido un aumento o una reducción del tamaño? Si el sitio se amplió temporalmente, es posible que se haya devuelto a su tamaño de clúster original. Si se realiza una solicitud para aumentar la capacidad del sitio, podría producirse un aumento de tamaño. Marque la **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** cuadro. Este fotograma a veces detecta una interrupción en un nodo en particular. Si ve que el tamaño disminuye, eso puede indicar un problema con uno o más nodos.

* La variable **[!UICONTROL IP Frequency]** identifica la frecuencia de solicitud de las direcciones IP que se realizan con los servidores de origen (lo que significa que la solicitud no se pudo proporcionar desde [!DNL Fastly] como 74 no se almacenó en caché).

   * Para cualquier [!DNL Fastly] problemas relacionados, consulte la **[!UICONTROL Fastly Cache]** y seleccione la faceta Error para ver el porcentaje de solicitudes que son errores. Pueden indicar un problema de backend si coinciden con una carga no web.
   * Si la carga no parece deberse al tráfico web, puede haber errores o una acumulación de solicitudes que no sean de web, como consultas lentas o crons.

* Marque la **[!UICONTROL Database Errors]** para errores que puedan coincidir con la línea de tiempo del problema/problema.
* Marque la **[!UICONTROL Database mysql-slow.log]** para identificar las instrucciones SQL que se están produciendo. `INSERT`, `UPDATE`y `DELETE` puede tardar un rato si la consulta no está optimizada. Even `SELECT` las instrucciones pueden ser muy ineficientes si se realizan en tablas grandes.
* **[!UICONTROL PHP States]** y **[!UICONTROL PHP Errors]** frames mostrarán posibles problemas con PHP. La variable **[!UICONTROL PHP States]** frame mostrará las terminaciones del proceso PHP, inicios y cuando el servicio alcance el estado listo por nodo. La variable **[!UICONTROL PHP Errors]** frame puede ayudar a aislar dónde está el problema con PHP, como el tamaño de la memoria, los trabajadores o el número de servidores.
* Para ver la latencia en las transacciones, la tabla Transactions - Avg, Max, Min se puede ordenar por columna para mostrar la duración de la transacción que se ejecuta más larga. Un clúster sobrecargado tendrá duraciones latentes en las transacciones, pero también mostrará anomalías que podrían señalar un problema con un método o cron.
* La variable **[!UICONTROL Cron error]** muestra bloqueos cron, errores SQL que pueden estar asociados con registros cron y crons de ensayo compartidos que pueden estar ejecutándose en entornos de producción cuando hay un entorno de ensayo dedicado.
* La variable [!UICONTROL ElasticSearch Errors] frame muestra errores que pueden indicar problemas importantes con [!DNL Elasticsearch] consultas, datos o índices.
