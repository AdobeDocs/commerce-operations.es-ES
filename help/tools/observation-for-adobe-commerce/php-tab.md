---
title: '"El [!UICONTROL PHP] tab"'
description: Obtenga información sobre [!UICONTROL PHP] ficha de [!DNS Observation for Adobe Commerce].
source-git-commit: f71fc3b2a66a4cc0b0d7865138184135e4a874e0
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---


# La variable [!UICONTROL PHP] ficha

La variable **PHP** La pestaña muestra los problemas del proceso PHP para proporcionar un análisis más profundo de los problemas de PHP.

## [!UICONTROL PHP active process details]

![Detalles del proceso activo PHP](../../assets/tools/php-active-process-details.jpg)

La variable **[!UICONTROL PHP active process details]** frame muestra los procesos PHP, incluyendo php-fpm, en el intervalo de tiempo seleccionado.

## [!UICONTROL PHP process load (# of PHP processes and % of CPU load)]

![Carga del proceso PHP](../../assets/tools/php-process-load.jpg)

Este fotograma muestra la carga de CPU de los procesos PHP-FPM en el intervalo de tiempo seleccionado.

## [!UICONTROL PHP Memory detail]

![Detalles de memoria de PHP](../../assets/tools/php-memory-detail.jpg)

La variable **[!UICONTROL PHP Memory detail]** frame muestra el uso de memoria de los procesos PHP en el periodo seleccionado.

## [!UICONTROL PHP CPU Utilization]

![Uso de CPU PHP](../../assets/tools/php-cpu-utilization.jpg)

La variable **[!UICONTROL PHP CPU Utilization]** frame muestra la utilización del % de CPU de los procesos PHP a través del intervalo de tiempo seleccionado.

## [!UICONTROL PHP Process states]

![Estados del proceso PHP](../../assets/tools/php-process-states-image-1.jpg)

La variable **[!UICONTROL PHP Process states]** frame muestra los estados del proceso PHP en el periodo seleccionado. Se mostrará cuando los procesos PHP terminen y se reinicien. Tenga cuidado con los procesos PHP terminados que no muestran reinicios.

* &#39;%AVISO: Finalizando ...%&#39;) como &#39;php_term&#39;
* &#39;% AVISO: saliendo, adiós!%&#39;) como &#39;php_exit&#39;
* &#39;% AVISO: fpm se está ejecutando, pid%) como &#39;fpm_start&#39;
* &#39;%AVISO: listo para gestionar conexiones%) como &#39;php_ready&#39;

## [!UICONTROL PHP Errors]

![Errores de PHP](../../assets/tools/php-errors-image-1.jpg)

La variable **[!UICONTROL PHP Errors]** frame muestra el número de errores de trabajo de PHP en el intervalo de tiempo seleccionado. Los mensajes de error analizados y mostrados incluyen:

* &#39;%worker_connectors no es suficiente%&#39;) como &#39;secundario&#39;
* &#39;%PHP Error irrecuperable: ¡Tamaño de memoria permitido!%&#39;) como &#39;mem_size&#39;
* &#39;%salió en la señal 11 (SIGSEGV)%&#39; como &#39;sig_11&#39;
* &#39;%se cerró en la señal 7 (SIGBUS)%&#39; como &#39;sig_7&#39;
* &#39;%incremente pm.start_servers%&#39;) como &#39;pmstart_serv&#39;
* &#39;%max_children%&#39;) como &#39;max_children_cnt&#39;
* &#39;%PHP Error irrecuperable: Tamaño de memoria permitido de%&#39;) como &#39;mem_exhst_coun&#39;
* &#39;%No se puede asignar memoria para pool%&#39;) como &#39;opc_mem_count&#39;
* &#39;%Warning Interstring buffer overflow%&#39;) como &#39;opc_str_buf&#39;
* &#39;%Desconexión de cadena no válida%&#39;) como &#39;opc_sv_comments&#39;
* &#39;%PHP Error irrecuperable: RedisException no detectada: error de lectura en connection%&#39;) como &#39;php_exc&#39;

## [!UICONTROL PHP processes count]

![Recuento de procesos PHP](../../assets/tools/php-processes-count.jpg)

La variable **[!UICONTROL PHP processes count]** frame muestra un recuento de los procesos PHP en el intervalo de tiempo seleccionado.

## [!UICONTROL Database Errors]

![Errores de base de datos](../../assets/tools/php-tab-database-errors.jpg)

La variable **[!UICONTROL Database Errors]** muestra errores de base de datos en el intervalo de tiempo seleccionado. Los errores analizados incluyen:

* &#39;%El tamaño de memoria asignado para la tabla temporal es superior al 20% de innodb_buffer_pool_size%&#39;) como &#39;temp_tbl_buff_pool&#39;
* WSREP &#39;%\[ERROR\]: error de escritura de rbr%) como &#39;rbr_write_failed&#39;
* &#39;%mysqld: Disco lleno%&#39;) como &#39;disk_full&#39;
* &#39;%Error número 28%&#39;) como &#39;err_28&#39;
* &#39;%rollback%&#39;) como &#39;rollback&#39;
* &#39;%La restricción de clave externa falla para la tabla%&#39;) como &#39;external_key_constraint&#39;
* &#39;%Error_code: 1114%) como &#39;sql_1114_full&#39;
* &#39;%CRÍTICO: SQLSTATE[HY000] [2006] El servidor MySQL ha desaparecido%) como &#39;sql_away&#39;
* &#39;%SQLSTATE[HY000] [1040] Demasiadas conexiones%) como &#39;sql_1040&#39;
* &#39;%CRÍTICO: SQLSTATE[HY000] [2002]%&#39;) como &#39;sql_2002&#39;
* &#39;%SQLSTATE[08S01]:%) como &#39;sql_1047&#39;
* &#39;%[Advertencia] Aborted connection%&#39;) como &#39;aborted_conn&#39;
* &#39;%SQLSTATE[23000]: Infracción de restricción de integridad:%) como &#39;sql_23000&#39;
* &#39;%1205 Bloquear tiempo de espera%&#39;) como &#39;sql_1205&#39;
* &#39;%SQLSTATE[HY000] [1049] Base de datos desconocida%) como &#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02]: No se encuentra la tabla o vista base:%) como &#39;sql_42S02&#39;
* &#39;%Error general: 1114%) como &#39;sql_1114&#39;
* &#39;%SQLSTATE[40001]%&#39;) como &#39;sql_1213&#39;
* &#39;%SQLSTATE[42S22]: Columna no encontrada: 1054 (Columna desconocida%) como &#39;sq1_1054&#39;
* &#39;%SQLSTATE[42000]: Error de sintaxis o infracción de acceso:%) como &#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]: Infracción de cardinalidad:%) como &#39;sql_1241&#39;
* &#39;%SQLSTATE[2003]:%) como &#39;sql_22003&#39;
* &#39;%SQLSTATE[HY000] [9000] Cliente con dirección IP%) como &#39;sql_9000&#39;
* &#39;%SQLSTATE[HY000]: Error general: 2014%) como &#39;sql_2014&#39;
* &#39;%1927 Se mató la conexión%&#39;) como &#39;sql_1927&#39;
* &#39;%1062 \[ERROR\] InnoDB:%&#39;) como &#39;sql_1062_e&#39;
* &#39;%[Nota] WSREP: Vaciando el mapa de memoria al disco...%&#39;) como &#39;mem_map_flush&#39;
* &#39;%Código de error interno de MariaDB: 1146%) como &#39;sql_1146&#39;
* &#39;%Código de error interno de MariaDB: 1062%) como &#39;sql_1062&#39; ・ &#39;%1062 [Advertencia] InnoDB:%&#39;) como &#39;sql_1062_w&#39;
* &#39;%Código de error interno de MariaDB: 1064%) como &#39;sql_1064&#39;
* &#39;%InnoDB: Error de aserción en el archivo%) como &#39;assertion_err&#39;
* &#39;%mysqld_safe Número de procesos en ejecución ahora: 0%) como &#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld obtuvo la señal%&#39;) como &#39;mysql_sigterm&#39;
* &#39;%1452 No se puede agregar%&#39;) como &#39;sql_1452&#39;
* &#39;%ERROR 1698%&#39;) como &#39;sql_1698&#39;
* &#39;%SQLSTATE[HY000]: Error general: 3%) como &#39;cnt_wrt_tmp&#39;
* &#39;%Error general: 1 %&#39;) como &#39;sql_sintaxis&#39;
* &#39;%42S22%&#39;) como &#39;sql_42S22&#39;
* &#39;%InnoDB: Error (Duplicate key)%&#39;) como &#39;innodb_dup_key&#39;

## [!UICONTROL Database traces]

![Rastreos de base de datos](../../assets/tools/php-tab-database-traces.jpg)

La variable **[!UICONTROL Database traces]** frame muestra la información de seguimiento de la base de datos. Este fotograma se alinea con la vista de resumen de transacciones APM para la cronología seleccionada.

## [!UICONTROL Database mysql-slow.log]

![Base de datos mysql-slow.log](../../assets/tools/php-tab-database-mysql-slow-log.jpg)

La variable **[!UICONTROL Database mysql-slow.log]** muestra los tipos de instrucciones de consulta que estaban en el `mysql-slow.log` en el intervalo de tiempo seleccionado.
