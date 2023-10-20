---
title: El [!UICONTROL Summary] pestaña
description: Obtenga información acerca de [!UICONTROL Summary] pestaña de [!DNL Observation for Adobe Commerce].
exl-id: b07ed898-a211-4353-a1d4-1b71d4898b93
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '2653'
ht-degree: 0%

---

# El [!UICONTROL Summary] pestaña

El [!UICONTROL Summary] pestaña de [!DNL Observation for Adobe Commerce] tiene como objetivo ver rápidamente algunos de los problemas que experimentan los sitios para ayudarle a resolver automáticamente o identificar las posibles causas raíz de los problemas del sitio. Las pestañas adicionales proporcionan información a nivel más profundo sobre los servicios de componentes, la base de datos, la infraestructura y los estados de proceso.

## [!UICONTROL Transaction Overview]

![Resumen de transacciones](../../assets/tools/transaction-overview.jpg)

### [¿Qué es una transacción?](https://docs.newrelic.com/docs/apm/transactions/intro-transactions/transactions-new-relic-apm/#:%7E:text=transactions%20are%20reported.-,What%20is%20a%20transaction%3F,work%20in%20a%20software%20application.&amp;text=For%20APM%2C%20it%20will%20frequency,when%20the%20response%20is%20sent)

&quot;En [!DNL New Relic], una transacción se define como una unidad lógica de trabajo en una aplicación de software. Específicamente, hace referencia a las llamadas de función y las llamadas de método que conforman esa unidad de trabajo. A menudo hace referencia a una transacción web, que representa una actividad que se produce desde el momento en que la aplicación recibe una solicitud web hasta el momento en que se envía la respuesta&quot;.

### Tipos de transacciones:

**Web:** Las transacciones web se inician con una solicitud HTTP. Para la mayoría de las organizaciones, estas representan interacciones centradas en el cliente y, por lo tanto, son las transacciones más importantes que se deben monitorizar.

**Fuera de la web:** Las transacciones que no son de web no se inician con una solicitud web. Pueden incluir procesos de trabajo que no son de web, procesos en segundo plano, secuencias de comandos, actividad de cola de mensajes y otras tareas.

Si mira el **[!UICONTROL Transaction Overview]** En el cuadro anterior, hubo casi 53.000 transacciones con una puntuación media APDEX de 0,76, y el 95% de esas transacciones se produjeron en menos de 2.313 segundos. Este sería un fotograma en el que un periodo de tiempo más ajustado podría mostrar una desviación de ese promedio actual si hay una visita de APDEX durante un periodo de tiempo corto.

## [!UICONTROL 404 page errors frame]

![Marco de errores de página 404](../../assets/tools/404-page-errors.jpg)

El **[!UICONTROL 404 page errors]** frame enumera las variables [URI](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) y el recuento de errores de página 404 para un periodo de tiempo seleccionado.

## [!UICONTROL % of Storage Free frame]

![Porcentaje de cuadro de almacenamiento libre](../../assets/tools/percent-of-storage-free.jpg)

El **[!UICONTROL % of Storage Free]** frame muestra el porcentaje promedio de libre de los montajes de almacenamiento en todos los nodos del clúster. Por ejemplo, si tiene un clúster de tres nodos, el marco muestra el símbolo \&lt;mount point=&quot;&quot;>, \&lt;environment name=&quot;&quot;>. Este marco puede resultar engañoso si hay una variación entre tres nodos. Un ejemplo de variación sería si la variable `/data/mysql` punto de montaje libre era un valor diferente en el clúster de tres nodos. Hay un marco debajo de la [!UICONTROL MySQL] que faceta los puntos de montaje por nombre de nodo para ver con mayor precisión lo que `/data/mysql` el almacenamiento disponible en cada nodo es realmente correcto.

## [!UICONTROL % of system memory that is free frame]

![porcentaje de memoria del sistema que está libre](../../assets/tools/percent-of-system-memory-that-is-free.jpg)

El **% de memoria del sistema libre** frame muestra, por nodo, la cantidad de memoria del sistema disponible en cada nodo.

## [!UICONTROL Swap memory free in bytes]

![memoria de intercambio libre en bytes](../../assets/tools/swap-memory-free-in-bytes.jpg)

El **[!UICONTROL Swap memory free in bytes]** frame muestra, por nodo, la cantidad de memoria SWAP libre en el nodo.

## [!UICONTROL CPU % by host]

![Porcentaje de CPU por host](../../assets/tools/cpu-percent-by-host.jpg)

La suma de todos los entornos y nodos se muestra en la variable **[!UICONTROL CPU % by host]** marco. Debe deseleccionar los entornos que no sean de producción. Tenga en cuenta también cualquier instancia en la que no estén presentes todos los nodos del entorno de producción. Para obtener más sugerencias sobre el uso elevado de la CPU, consulte [Solución de problemas de rendimiento con New Relic en Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-performance-using-new-relic-on-magento-commerce.html).

## [!UICONTROL Alerts during timeframe]

![alertas durante el periodo de tiempo](../../assets/tools/alerts-during-timeframe.jpg)

El **[!UICONTROL Alerts during timeframe]** muestra todas las alertas, incluida la [!UICONTROL Managed Alerts] añadido por el soporte de Adobe Commerce.

## [!UICONTROL CPU Usage]

![uso de CPU](../../assets/tools/cpu-usage.jpg)

Si la variable **[!UICONTROL CPU Usage]** marco está en blanco, lo que indica que la aplicación de infraestructura de [!DNL New Relic] no está activada. Si el sitio está en Inicio, no verá esta información. Si su sitio está en Pro, abra un [ticket de asistencia](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html) por tener [!DNL New Relic Infrastructure] habilitado para el sitio.

## [!UICONTROL Average Response Time]

![tiempo medio de respuesta](../../assets/tools/average-response-time.jpg)

El **[!UICONTROL Average Response Time]** el gráfico muestra el tiempo de respuesta promedio para las transacciones (web y otras).

## [!UICONTROL Long duration cron_schedule updates]

![actualizaciones cron_schedule de larga duración](../../assets/tools/long-duration-cron-schedule-updates.jpg)

El **[!UICONTROL cron_schedule]** se escribe al principio y al final de los trabajos cron. Los trabajos cron de larga duración podrían indicar latencia al actualizar esta tabla, lo que puede indicar una pila cron o un problema con la programación de cron.

## [!UICONTROL Response Code]

![código de respuesta](../../assets/tools/response-code.jpg)

El **[!UICONTROL Response Code]** frame es una buena indicación del tráfico web y el código de respuesta de las solicitudes. Lo es [!DNL New Relic's] datos de transacción, y se faceta con la variable `httpResponseCode` devuelto.

## [!UICONTROL Web Traffic volume compared with one week ago Magento Managed Alerts Information]

![volumen de tráfico web comparado con hace una semana](../../assets/tools/web-traffic-volume-compared.jpg)

Este marco muestra el volumen de tráfico web comparativo de la semana anterior y la semana actual.

## [!UICONTROL Deployment Log Entries]

![entradas del registro de implementación](../../assets/tools/deployment-log-entries.jpg)

El **[!UICONTROL Deployment Log Entries]** frame muestra un recuento de las entradas y facetas del registro de implementación y nube de los recuentos por nombre del registro de implementación.

## [!UICONTROL Deployment State]

![estado de implementación](../../assets/tools/deployment-state.jpg)

El **[!UICONTROL Deployment State]** facetas de marco fases de implementación específicas de los registros de implementación. A continuación, se muestran algunos ejemplos de fases contadas en el registro y el nombre de faceta:

**Fases del registro de implementación:**

* &#39;%Starting generate command%&#39;) as &#39;start_gen&#39;
* &#39;%git apply /app/seller/magento/ece-tools/patch%&#39;) como &#39;apply_patch&#39;
* &#39;%Set flag: .static_content_deploy%&#39;) as &#39;SCD&#39;
* &#39;%NOTICE: Generación de comando completada (%) como &#39;gen_compl&#39;
* &#39;%NOTICE: implementación completada (%) como &#39;deploy_compl&#39;
* &#39;%NOTICE: iniciando posterior a la implementación.%&#39;) como &#39;start_deploy&#39;
* &#39;%NOTICE: la implementación posterior se ha completado (%) como &#39;deploy&#39;
* &#39;%deploy-complete%&#39;) como &#39;cl_deploy_compl&#39;

## [!UICONTROL IP Frequency]

![Frecuencia IP](../../assets/tools/ip-frequency.jpg)

El **[!UICONTROL IP Frequency]** frame cuenta los estados (&quot;MISS&quot; y &quot;PASS&quot;) para cada IP desde el [!DNL Fastly] registros. Las solicitudes web con estos estados llegan al servidor de origen y añaden carga al servidor. Muestra las veinte direcciones principales en frecuencia. Este marco se puede utilizar para detectar ataques IP o fuentes de carga pesada en un sitio web.

## [!UICONTROL IP Response – top 20 URLs in duration]

![respuesta ip: las 20 direcciones url principales en duración](../../assets/tools/ip-response-top-20-urls.jpg)

El **[!UICONTROL IP Response – top 20 URLs in duration]** frame muestra las direcciones URL con la mayor duración en respuesta. Puede indicar páginas o archivos de imagen grandes, API o páginas con la mayor duración de respuesta.

## [!UICONTROL API Calls by IP]

![llamadas api por dirección ip](../../assets/tools/api-calls-by-ip.jpg)

El **[!UICONTROL API Calls by IP]** El marco de ayuda a identificar el tráfico intenso en las API y las direcciones IP que realizan solicitudes desde las URL de las API.

## [!UICONTROL API Calls by IP, details by URL]

![llamadas api por detalles ip por dirección url](../../assets/tools/api-calls-by-ip-details-by-url.jpg)

El **[!UICONTROL API Calls by IP, details by URL]** proporciona detalles del tráfico intenso de las API y de las direcciones URL que realizan las solicitudes.

## [!UICONTROL IP Frequency Rate per minute]

![frecuencia de ip por minuto](../../assets/tools/ip-frequency-rate-per-minute.jpg)

A veces es difícil saber qué dirección IP tiene la mayor cantidad de solicitudes en los otros fotogramas. El **[!UICONTROL IP Frequency Rate per minute]** El fotograma muestra la velocidad por minuto por dirección IP.

## [!UICONTROL Potential Bots]

![bots potenciales](../../assets/tools/potential-bots.jpg)

El **[!UICONTROL Potential Bots]** frame busca solicitudes con un nombre request_user_agent como NULL o &#39;%bot%&#39;. Normalmente, request_user_agent de &#39;%bot%&#39; sigue la configuración de directivas en `robots.txt` archivo.

## [!UICONTROL Transaction Errors]

![errores de transacción](../../assets/tools/transaction-errors.jpg)

El **[!UICONTROL Transaction Errors]** frame muestra el recuento de errores de transacción de [!DNL New Relic].

## [!UICONTROL Nginx access by node]

![nginx access by node](../../assets/tools/nginx-access-by-node.jpg)

El **[!UICONTROL Nginx access by node]** el marco examina los recuentos del `access.log` por nodo. Es útil ver si la carga se distribuye uniformemente. A menudo se muestra cuando se suelta un nodo. El marco también muestra la carga a través del sitio.

## [!UICONTROL Galera Log]

![registro de galera](../../assets/tools/galera-log.jpg)

[[!DNL Galera]](https://galeracluster.com/library/galera-documentation.pdf) se utiliza para el clúster de base de datos. Este cuadro se centra en señales particulares de la [!UICONTROL Galera] clúster. Las señales se centran en los nodos que entran y salen del clúster, lo que es un comportamiento normal para mantener la integridad de los datos de la base de datos. Los nodos se mantienen sincronizados como [!UICONTROL Galera] cambios de estado de clúster.

**Lista de [!UICONTROL Galera] cambios de estado:**

* &#39;%1047 WSREP aún no ha preparado el nodo para el uso de la aplicación (%) como &#39;node_not_prep_for_use&#39;
* &#39;%\[ERROR\] WSREP: No se pudo leer de: wsrep_sst_xtrabackup-v2%&#39;) como &#39;xtrabackup_read_fail&#39;
* &#39;%\[ERROR\] WSREP: Proceso completado con error: wsrep_sst_xtrabackup-v2 %&#39;) as &#39;xtrabackup_compl_w_err&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) as &#39;rbr_write_fail&#39;
* &#39;%self-left%&#39;) como &#39;susp_node&#39;
* &#39;%members = 3/3 (unidos/total)%&#39;) como &#39;3de3&#39;
* &#39;%members = 2/3 (unidos/total)%&#39;) como &#39;2of3&#39;
* &#39;%members = 2/2%&#39;) como &#39;2of2&#39; * &#39;%members = 1/2%&#39;) como &#39;1of2&#39; * &#39;%members = 1/3%&#39;) como &#39;1of3&#39;
* &#39;%members = 1/1%&#39;) como &#39;1of1&#39;
* &#39;%\[Nota\] /usr/sbin/mysqld (mysqld 10.%&#39;) como &#39;sql_restart&#39;
* &#39;%Quorum: no hay ningún nodo con estado completo:%&#39;) como &#39;no_node_count&#39;
* &#39;%WSREP: miembro 0%&#39;) como &#39;mem_0&#39;
* &#39;%WSREP: miembro 1,0%&#39;) como &#39;mem_1&#39;
* &#39;%WSREP: miembro 2%&#39;) como &#39;mem2&#39;
* &#39;%WSREP: sincronizado con el grupo, listo para conexiones%&#39;) como &#39;listo&#39;
* &#39;%/usr/sbin/mysqld, Version:%&#39;) as &#39;mysql_restart_mysql.slow&#39;
* &#39;%\[Nota\] WSREP: Nueva vista de clúster: estado global:%&#39;) como &#39;galera_cluster_view_chang&#39;

Estas señales pueden indicar problemas de almacenamiento, memoria o consulta si el estado cambia con frecuencia.

## [!UICONTROL Database errors]

![errores de base de datos](../../assets/tools/database-errors.jpg)

**Lista de mensajes o errores de base de datos detectados:**

* &#39;%El tamaño de memoria asignado para la tabla temporal es superior al 20% de innodb_buffer_pool_size%&#39;) como &#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) as &#39;rbr_write_fail&#39;
* &#39;%mysqld: Disco lleno%&#39;) como &#39;disk_full&#39;
* &#39;%Error número 28%&#39;) como &#39;err_28&#39;
* &#39;%rollback%&#39;) como &#39;rollback&#39;
* &#39;%Foreign key constraint falla para table%&#39;) como &#39;Foreign_key_constraint&#39;
* &#39;%Error_code: 1114%&#39;) como &#39;sql_1114_full&#39;
* &#39;%CRITICAL: SQLSTATE\[HY000\] \[2006\] El servidor MySQL se ha ido%&#39;) como &#39;sql_gone&#39;
* &#39;%SQLSTATE\[HY000\] \[1040\] Demasiadas conexiones%&#39;) como &#39;sql_1040&#39;
* &#39;%CRITICAL: SQLSTATE\[HY000\] \[2002\]%&#39;) as &#39;sql_2002&#39;
* &#39;%SQLSTATE\[08S01\]:%&#39;) como &#39;sql_1047&#39;
* &#39;%\[Advertencia\] Conexión anulada%&#39;) como &#39;aborted_conn&#39;
* &#39;%SQLSTATE\[23000\]: infracción de restricción de integridad:%&#39;) como &#39;sql_23000&#39;
* &#39;%1205 Bloquear tiempo de espera (%) como &#39;sql_1205&#39;
* &#39;%SQLSTATE\[HY000\] \[1049\] Base de datos desconocida%&#39;) como &#39;sql_1049&#39;
* &#39;%SQLSTATE\[42S02\]: tabla base o vista no encontrada:%&#39;) como &#39;sql_42S02&#39;
* &#39;%Error general: 1114%&#39;) como &#39;sql_1114&#39;
* &#39;%SQLSTATE\[40001\]%&#39;) como &#39;sql_1213&#39;
* &#39;%SQLSTATE\[42S22\]: Columna no encontrada: 1054 (columna desconocida%) como &#39;sq1_1054&#39;
* &#39;%SQLSTATE\[42000\]: error de sintaxis o infracción de acceso:%&#39;) como &#39;sql_42000&#39;
* &#39;%SQLSTATE\[21000\]: Infracción de cardinalidad:%&#39;) como &#39;sql_1241&#39;
* &#39;%SQLSTATE\[22003\]:%&#39;) como &#39;sql_22003&#39;
* &#39;%SQLSTATE\[HY000\] \[9000\] Cliente con dirección IP%&#39;) como &#39;sql_9000&#39;
* &#39;%SQLSTATE\[HY000\]: Error general: 2014%&#39;) as &#39;sql_2014&#39;
* &#39;%1927 Conexión se eliminó%&#39;) como &#39;sql_1927&#39;
* &#39;%1062 \[\ERROR\] InnoDB:%&#39;) como &#39;sql_1062_e&#39;
* &#39;%\[Nota\] WSREP: Vaciando asignación de memoria al disco...%&#39;) como &#39;mem_map_flush&#39;
* &#39;%Internal MariaDB error code: 1146%&#39;) as &#39;sql_1146&#39;
* &#39;%Internal MariaDB error code: 1062%&#39;) as &#39;sql_1062&#39; * &#39;%1062 \[Warning\] InnoDB:%&#39;) as &#39;sql_1062_w&#39;
* &#39;%Internal MariaDB error code: 1064%&#39;) as &#39;sql_1064&#39;
* &#39;%InnoDB: error de aserción en el archivo &#39;%&#39;) como &#39;assertion_err&#39;
* &#39;%mysqld_safe Número de procesos que se ejecutan ahora: 0%&#39;) como &#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld tiene señal%&#39;) como &#39;mysql_sigterm&#39;
* &#39;%1452 No se puede agregar%&#39;) como &#39;sql_1452&#39;
* &#39;%ERROR 1698%&#39;) como &#39;sql_1698&#39;
* &#39;%SQLSTATE\[HY000\]: Error general: 3%&#39;) as &#39;cnt_wrt_tmp&#39;
* &#39;%Error general: 1 %&#39;) como &#39;sql_syntax&#39;
* &#39;%42S22%&#39;) como &#39;sql_42S22&#39;
* &#39;%InnoDB: Error (clave duplicada)%&#39;) como &#39;innodb_dup_key&#39;

## [!UICONTROL Database traces]

![seguimiento de base de datos](../../assets/tools/database-traces.jpg)

El **[!UICONTROL Database traces]** frame busca datos de la variable [seguimiento de sql](https://docs.newrelic.com/docs/apm/transactions/transaction-traces/transaction-traces-database-queries-page/) entidad de [!DNL New Relic] y devuelve la ruta del seguimiento.

## [!UICONTROL Database mysql-slow.log]

![base de datos mysql-slow.log](../../assets/tools/database-mysql-slow-log.jpg)

El **[!UICONTROL Database mysql-slow.log]** marco hace un recuento de entradas en el [mysql-slow.log](https://dev.mysql.com/doc/refman/5.7/en/slow-query-log.html) por tipo de solicitud de consulta. Aísla visualmente los marcos de tiempo que puedan ser de interés en mysql-slow.log (registro de consulta lenta). Las consultas de tablas sin índices o consultas que actualizan tablas grandes pueden bloquear otras consultas.

## [!UICONTROL Redis synchronization from Log]

![redis sincronización desde registro](../../assets/tools/redis-synchronization-from-log.jpg)

[[!DNL Redis]](https://redis.io/docs/about/) es un almacén de estructura de datos en memoria de código abierto (con licencia BSD) que se utiliza como base de datos, caché y agente de mensajes. Puede realizar el almacenamiento en caché de sesión y base de datos si está configurado. El **[!UICONTROL Redis synchronization from Log]** frame se centra en [[!DNL Redis] sincronización](https://redis.io/docs/manual/replication/). Cuanto más grande sea el [!DNL Redis] conjunto de datos, es más probable que haya problemas con la sincronización (más datos para mantener sincronizados).

**[!DNL Redis]errores y mensajes:**

* &#39;%SLAVE synchronization: No queda espacio en el dispositivo%&#39;) como &#39;espacio&#39;
* &#39;%Server iniciado, Redis version%&#39;) como &#39;serv_start&#39;
* &#39;%El servidor está listo para aceptar conexiones (%) como &#39;preparado&#39;
* &#39;%Se ha perdido la conexión con el maestro.%&#39;) como &#39;mstr_loss&#39;
* &#39;%+centinela descendente%&#39;) como &#39;+centinela&#39;
* &#39;%-sdown centinela%&#39;) como &#39;-sentinal&#39;
* &#39;%-sdown esclavo%&#39;) como &#39;-esclavo&#39;, &#39;%+sdown esclavo%&#39;) como &#39;+esclavo&#39;
* &#39;%-failover-abort-not-selected master (mymaster%) como &#39;-failover&#39;
* &#39;%+failover-abort-not-selected master (mymaster%) como &#39;+failover&#39;
* &#39;%No es posible la resincronización parcial (no hay maestro en caché)%&#39;) como &#39;part_sync_err&#39;
* &#39;%MASTER anuló la replicación con un error: ERR (puede%) como &#39;mstr_sync_err&#39;
* &#39;%Master no admite PSYNC o está en estado de error (%) como &#39;mstr_psync_err&#39;
* &#39;%SLAVE sync: Finished with success%&#39;) as &#39; slv_sync_suc&#39;
* &#39;%MASTER anuló la replicación con un error: ERR (puede%) como &#39;mstr_sync_err,count&#39;
* &#39;%OOM comando no permitido cuando se usa la memoria%&#39;) como &#39; max_mem_err&#39;
* &#39;%CredisException(code: 0): error de lectura en la conexión%&#39;) como &#39;credis_read_error&#39;
* &#39;%Uncatch RedisException:%&#39;) como &#39;redis_excp_err&#39;
* &#39;%psync programado para cerrarse lo antes posible para superar el búfer de salida (%) como &#39;output_buf_err&#39;

## [!UICONTROL PHP process states]

![Estados de proceso PHP](../../assets/tools/php-process-states.jpg)

La manera en que los procesos de PHP se comportan depende de la [configuración](https://www.php.net/manual/en/install.fpm.configuration.php). La configuración es compleja, con muchas variables y opciones. El **[!UICONTROL PHP process states]** frame le ayuda a comprender cuándo se terminan y reinician los procesos de PHP.

### [!UICONTROL PHP errors]

![errores de php](../../assets/tools/php-errors.jpg)

El **[!UICONTROL PHP errors]** frame muestra el número de errores de PHP con trabajadores a lo largo del periodo de tiempo seleccionado. Para obtener más información, consulte [Configuración de Adobe Commerce PHP](../../installation/prerequisites/php-settings.md).

**Errores y mensajes de PHP:**

* &#39;%worker_connections are not ough (%) as &#39;worker&#39;
* &#39;%PHP Error grave: tamaño de memoria permitido%&#39;) como &#39;mem_size&#39;
* &#39;%salía en la señal 11 (SIGSEGV)%&#39;) como &#39;sig_11&#39;
* &#39;%saliente en la señal 7 (SIGBUS)%&#39;) como &#39;sig_7&#39;
* &#39;%increased pm.start_servers%&#39;) como &#39;pmstart_serv&#39;
* &#39;%max_children%&#39;) como &#39;max_children_cnt&#39;
* &#39;%PHP Error grave: tamaño de memoria permitido de%&#39;) como &#39;mem_exhst_count&#39;
* &#39;%No se puede asignar memoria para el grupo%&#39;) como &#39;opc_mem_count&#39;
* &#39;%Warning Interned string buffer overflow%&#39;) as &#39;opc_str_buf&#39;
* &#39;%Offset de cadena no válido%&#39;) como &#39;opc_sv_comments&#39;
* &#39;%PHP Error grave: RedisException no detectada: error de lectura en la conexión (%) como &#39;php_exc&#39;

## [!UICONTROL PHP processes]

![procesos php](../../assets/tools/php-processes.jpg)

[PHP-FPM](https://php-fpm.org/) es un [!UICONTROL FastCGI Process Manager] utilizado por [!DNL Nginx]. Para conocer los requisitos del sistema, consulte [Requisitos de versión de PHP asignados a versiones de Adobe Commerce](../../installation/system-requirements.md). El **[!UICONTROL PHP processes]** El cuadro muestra el número de procesos PHP ejecutándose en un momento particular en la línea de tiempo seleccionada.

## [!UICONTROL Secondary processes]

![procesos secundarios](../../assets/tools/secondary-processes.jpg)

Los procesos secundarios pueden afectar a la respuesta del sitio. El **[!UICONTROL Secondary processes]** frame indica un proceso o procesos que pueden estar agregando carga al sitio. La base de datos tiene principalmente los procesos más secundarios en ejecución.

## [!UICONTROL Traffic vs Week Ago]

![tráfico vs semana atrás](../../assets/tools/traffic-vs-week-ago.jpg)

El **[!UICONTROL Traffic vs Week Ago]** frame busca el tráfico del sitio web (solicitudes) desde el [!DNL Fastly] Registra con estados de caché (&quot;MISS&quot;, &quot;PASS&quot;). Estas solicitudes añaden carga a los servidores de origen. Este marco muestra el volumen comparativo de solicitudes web de la semana actual y de la semana pasada durante el mismo período de tiempo.

## [!UICONTROL Fastly Cache]

![Caché rápida](../../assets/tools/fastly-cache.jpg)

El **[!UICONTROL Fastly Cache]** frame muestra una vista agregada del estado de caché de las solicitudes de [!DNL Fastly] registros. Si selecciona ERROR, se mostrará el porcentaje de errores en las solicitudes. Esto suele aumentar cuando el servidor de origen no responde con la rapidez suficiente a las solicitudes de página.

## [!UICONTROL Page Rendering]

![procesamiento de páginas](../../assets/tools/page-rendering.jpg)

El **[!UICONTROL Page Rendering]** frame muestra la duración promedio de procesamiento de páginas de la semana actual desde el origen de vista de página de [!DNL New Relic] comparado con la semana anterior durante el mismo período de tiempo.

## [!UICONTROL Page loading detail]

![detalles de carga de página](../../assets/tools/page-loading-detail.png)

El **[!UICONTROL Page loading detail]** frame describe los eventos de carga de página. Detalla los significados de estas facetas. Esta es la consulta que se ejecuta para este marco:

`SELECT percentile(timeToResponseStart, 50) AS 'first byte', percentile(firstPaint, 50) as 'First paint', percentile(firstContentfulPaint, 50) as 'First contentful paint', percentile(timeToDomContentLoadedEventEnd, 50) AS 'DOM content loaded', percentile(duration, 50) AS 'Window load + AJAX' FROM BrowserInteraction TIMESERIES`

## [!UICONTROL Transactions – Avg, Max, Min]

![transacciones: avg, max, min](../../assets/tools/transactions-avg-max-min.jpg)

La duración de la transacción es en segundos. Según la transacción, puede afectar a otras transacciones si es de larga duración. Las transacciones enumeradas bajo nombre y las duraciones son para el período de tiempo específico. Si hay un periodo de tiempo de problema conciso, cambie el tamaño del [!DNL Observation for Adobe Commerce] selector de fecha y hora a ese estrecho periodo de tiempo.

## [!UICONTROL Admin Activities]

![actividades de administración](../../assets/tools/admin-activities.jpg)

El **[!UICONTROL Admin Activities]** marco identifica las transacciones con un usuario administrador.

## [!UICONTROL Order transactions (default?)]

![Transacciones de pedido predeterminadas](../../assets/tools/order-transactions-default.jpg)

El **[!UICONTROL Order transactions (default?)]** marco busca transacciones `request.headers.host` de transacciones, donde el nombre = `WebTransaction/Action/checkout/onepage/success`. Si la dirección URL de éxito del pedido es diferente, este marco no tendrá datos.

## [!UICONTROL Elasticsearch Index information]

![información del índice de elasticsearch](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

**[Estados del Elasticsearch:](https://www.elastic.co/guide/en/elasticsearch/reference/current/cluster-health.html)**

* Verde: se asignan todos los fragmentos.
* Amarillo: todos los fragmentos principales se asignan, pero uno o más fragmentos de réplica no se asignan. Si falla un nodo del clúster, algunos datos podrían no estar disponibles hasta que se repare ese nodo.
* Rojo: uno o más fragmentos principales no están asignados, por lo que algunos datos no están disponibles. Esto puede ocurrir brevemente durante el inicio del clúster a medida que se asignan los fragmentos principales.

## [!UICONTROL Elasticsearch Errors]

![errores de elasticsearch](../../assets/tools/elasticsearch-errors.jpg)

**[!DNL Elasticsearch]errores:**

* &#39;%all_shards failed%&#39; como &#39;all_shards_failed&#39;
* &#39;%NoNodesAvailableException%&#39; como &#39;no_alive_nodes&#39;
* &#39;%PHP Error grave: Error no capturado: Parámetros incorrectos para Elasticsearch%&#39; como &#39;wrong_param&#39;
* &#39;%Puede solucionar este problema actualizando el servicio de Elasticsearch en su infraestructura de Magento Cloud a la versión%&#39; como &#39;ver_err&#39;
* &#39;%el estado de mantenimiento del clúster ha cambiado de \[AMARILLO\] a \[ROJO\] (motivo:%&#39; como &#39;yel_red&#39;
* &#39;%No queda espacio en el dispositivo%&#39; como &#39;no_space&#39;
* &#39;% no pudo ejecutar &lbrack;SearchRequest&lbrace;searchType=%&#39; como &#39;failed_query&#39;

## [!UICONTROL Cron view]

![vista de cron](../../assets/tools/cron-view.jpg)

El **[!UICONTROL Cron view]** frame busca en el registro de cron el equilibrio entre el número de crones iniciados frente al número de crones que finalizan.


## [!UICONTROL Cron error]

![error cron](../../assets/tools/cron-error.png)

**Errores de Cron de cron.log:**

* &#39;%_stg%&#39; como &#39;stg_crons&#39;
* &#39;%No se pudo adquirir el bloqueo para el trabajo cron%&#39; como &#39;cron_lock&#39;
* &#39;%Error general: 2006 El servidor MySQL ha desaparecido%&#39; como &#39;mysql_has_gone_away&#39;
* &#39;%error%&#39; como &#39;error&#39;
* &#39;%Error general: 1205 Se superó el tiempo de espera de bloqueo%&#39; como sql_1205_cron

## [!UICONTROL cron_schedule table updates]

![cron_schedule: actualizaciones de tabla](../../assets/tools/cron-schedule-table-updates.jpg)

El **[!UICONTROL cron_schedule table updates]** frame busca la duración máxima en segundos cuando las actualizaciones de operaciones del almacén de datos implican la tabla cron_schedule. Se faceta en el tipo de solicitud SQL.

## [!UICONTROL Datastore Operations Tables]

![tablas de operaciones del almacén de datos](../../assets/tools/datastore-operations-tables.jpg)

Esta **[!UICONTROL Datastore Operations Tables]** frame muestra las 25 operaciones principales por duración, tiempo, nombre de tabla y tipo de solicitud SQL. Pase el ratón sobre los picos para ver los detalles de a qué tabla se estaba accediendo y por qué tipo de solicitud.

## [!UICONTROL Cache Flush]

![vaciado de caché](../../assets/tools/cache-flush.jpg)

**Vaciados de caché detectados:**

* &#39;%config%&#39; como &#39;config_cache_flushing&#39;
* &#39;%layout%&#39; como &#39;layout_cache_flush&#39;
* &#39;%block_html%&#39; como &#39;block_html_cache_flush&#39;
* &#39;%collections%&#39; como &#39;collections_cache_flush&#39;
* &#39;%reflect%&#39; como &#39;mirror_cache_flush&#39;
* &#39;%db_ddl%&#39; como &#39;db_ddl_cache_flush&#39;
* &#39;%compilation_config%&#39; como &#39;compilation_config_cache_flush&#39;
* &#39;%eav%&#39; como &#39;eav_cache_flush&#39;
* &#39;%customer_notification%&#39; como &#39;cust_notif_cache_flush&#39;
* &#39;%config_integration%&#39; como &#39;config_integ_cache_flush&#39;
* &#39;%config_integration_api%&#39; como &#39;config_integ_api_cache_flush&#39;
* &#39;%full_page%&#39; como &#39;full_page_cache_flush&#39;
* &#39;%config_webservice%&#39; como &#39;config_webserv_cache_flush&#39;
* &#39;%translate%&#39; como &#39;translate_cache_flush&#39;
