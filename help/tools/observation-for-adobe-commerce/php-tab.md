---
title: La ficha [!UICONTROL PHP]
description: Obtenga información acerca de la ficha [!UICONTROL PHP] de  [!DNL Observation for Adobe Commerce].
exl-id: 0989a7f5-75b0-4fb5-ac5e-2618603bf548
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# La ficha [!UICONTROL PHP]

La pestaña **PHP** muestra problemas de procesos de PHP para proporcionar un análisis más profundo de los problemas de PHP.

## [!UICONTROL PHP active process details]

![Detalles del proceso activo de PHP](../../assets/tools/php-active-process-details.jpg)

El fotograma **[!UICONTROL PHP active process details]** muestra los procesos de PHP, incluido php-fpm, en el periodo de tiempo seleccionado.

## [!UICONTROL PHP process load (# of PHP processes and % of CPU load)]

![Carga del proceso PHP](../../assets/tools/php-process-load.jpg)

El fotograma **[!UICONTROL PHP process load (# of PHP processes and % of CPU load)]** muestra la carga de CPU de los procesos PHP-FPM en el periodo de tiempo seleccionado.

## [!UICONTROL PHP Memory detail]

![Detalle de memoria PHP](../../assets/tools/php-memory-detail.jpg)

El fotograma **[!UICONTROL PHP Memory detail]** muestra el uso de memoria de los procesos PHP en el periodo de tiempo seleccionado.

## [!UICONTROL PHP CPU Utilization]

![Utilización de PHP CPU](../../assets/tools/php-cpu-utilization.jpg)

El fotograma **[!UICONTROL PHP CPU Utilization]** muestra el porcentaje de uso de CPU de los procesos PHP en el periodo de tiempo seleccionado.

## [!UICONTROL PHP Process states]

![Estados del proceso PHP](../../assets/tools/php-process-states-image-1.jpg)

El fotograma **[!UICONTROL PHP Process states]** muestra los estados del proceso PHP a lo largo del periodo de tiempo seleccionado. Se muestra cuando los procesos de PHP finalizan y se reinician. Tenga cuidado con los procesos PHP terminados que no muestran reinicios.

* &#39;%NOTICE: finalizando ...%&#39;) como &#39;php_term&#39;
* &#39;% AVISO: saliendo, ¡adiós!%&#39;) como &#39;php_exit&#39;
* &#39;% NOTICE: fpm se está ejecutando, pid%&#39;) como &#39;fpm_start&#39;
* &#39;%NOTICE: listo para gestionar conexiones (%) como &#39;php_ready&#39;

## [!UICONTROL PHP Errors]

![Errores de PHP](../../assets/tools/php-errors-image-1.jpg)

El fotograma **[!UICONTROL PHP Errors]** muestra el número de errores de trabajo de PHP en el periodo de tiempo seleccionado. Los mensajes de error analizados y mostrados incluyen:

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

## [!UICONTROL PHP processes count]

![Recuento de procesos PHP](../../assets/tools/php-processes-count.jpg)

El fotograma **[!UICONTROL PHP processes count]** muestra un recuento de procesos PHP a lo largo del periodo de tiempo seleccionado.

## [!UICONTROL Database Errors]

![Errores de base de datos](../../assets/tools/php-tab-database-errors.jpg)

El fotograma **[!UICONTROL Database Errors]** muestra errores de base de datos en el periodo de tiempo seleccionado. Los errores analizados incluyen:

* &#39;%El tamaño de memoria asignado para la tabla temporal es superior al 20% de innodb_buffer_pool_size%&#39;) como &#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) as &#39;rbr_write_fail&#39;
* &#39;%mysqld: Disco lleno%&#39;) como &#39;disk_full&#39;
* &#39;%Error número 28%&#39;) como &#39;err_28&#39;
* &#39;%rollback%&#39;) como &#39;rollback&#39;
* &#39;%Foreign key constraint falla para table%&#39;) como &#39;Foreign_key_constraint&#39;
* &#39;%Error_code: 1114%&#39;) como &#39;sql_1114_full&#39;
* &#39;%CRITICAL: SQLSTATE[HY000] [2006] El servidor MySQL se ha ido%&#39;) como &#39;sql_gone&#39;
* &#39;%SQLSTATE[HY000] [1040] Demasiadas conexiones%&#39;) como &#39;sql_1040&#39;
* &#39;%CRITICAL: SQLSTATE[HY000] [2002]%&#39;) como &#39;sql_2002&#39;
* &#39;%SQLSTATE[08S01]:%&#39;) como &#39;sql_1047&#39;
* &#39;%[Advertencia] (conexión anulada%) como &#39;aborted_conn&#39;
* &#39;%SQLSTATE[23000]: infracción de restricción de integridad:%&#39;) como &#39;sql_23000&#39;
* &#39;%1205 Bloquear tiempo de espera (%) como &#39;sql_1205&#39;
* &#39;%SQLSTATE[HY000] [1049] Base de datos desconocida%&#39;) como &#39;sql_1049&#39;
* &#39;%SQLSTATE[42S02]: no se encontró la tabla o vista base:%&#39;) como &#39;sql_42S02&#39;
* &#39;%Error general: 1114%&#39;) como &#39;sql_1114&#39;
* &#39;%SQLSTATE[40001]%&#39;) como &#39;sql_1213&#39;
* &#39;%SQLSTATE[42S22]: Columna no encontrada: 1054 Columna desconocida%&#39;) como &#39;sq1_1054&#39;
* &#39;%SQLSTATE[42000]: error de sintaxis o infracción de acceso:%&#39;) como &#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]: Infracción de cardinalidad:%&#39;) como &#39;sql_1241&#39;
* &#39;%SQLSTATE[22003]:%&#39;) como &#39;sql_22003&#39;
* &#39;%SQLSTATE[HY000] [9000] cliente con dirección IP%&#39;) como &#39;sql_9000&#39;
* &#39;%SQLSTATE[HY000]: Error general: 2014%&#39;) como &#39;sql_2014&#39;
* &#39;%1927 Conexión se eliminó%&#39;) como &#39;sql_1927&#39;
* &#39;%1062 \[ERROR\] InnoDB:%&#39;) como &#39;sql_1062_e&#39;
* &#39;%[Nota] WSREP: vaciando asignación de memoria al disco...%&#39;) como &#39;mem_map_flush&#39;
* &#39;%Internal MariaDB error code: 1146%&#39;) as &#39;sql_1146&#39;
* &#39;%Internal MariaDB error code: 1062%&#39;) as &#39;sql_1062&#39; * &#39;%1062 [Warning] InnoDB:%&#39;) as &#39;sql_1062_w&#39;
* &#39;%Internal MariaDB error code: 1064%&#39;) as &#39;sql_1064&#39;
* &#39;%InnoDB: error de aserción en el archivo &#39;%&#39;) como &#39;assertion_err&#39;
* &#39;%mysqld_safe Número de procesos que se ejecutan ahora: 0%&#39;) como &#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld tiene señal%&#39;) como &#39;mysql_sigterm&#39;
* &#39;%1452 No se puede agregar%&#39;) como &#39;sql_1452&#39;
* &#39;%ERROR 1698%&#39;) como &#39;sql_1698&#39;
* &#39;%SQLSTATE[HY000]: Error general: 3%&#39;) como &#39;cnt_wrt_tmp&#39;
* &#39;%Error general: 1 %&#39;) como &#39;sql_syntax&#39;
* &#39;%42S22%&#39;) como &#39;sql_42S22&#39;
* &#39;%InnoDB: Error (clave duplicada)%&#39;) como &#39;innodb_dup_key&#39;

## [!UICONTROL Database traces]

![Seguimientos de base de datos](../../assets/tools/php-tab-database-traces.jpg)

El marco **[!UICONTROL Database traces]** muestra información de seguimiento de la base de datos. Este fotograma se alinea con la vista Resumen de transacciones de APM para la cronología seleccionada.

## [!UICONTROL Database mysql-slow.log]

![Base de datos mysql-slow.log](../../assets/tools/php-tab-database-mysql-slow-log.jpg)

El fotograma **[!UICONTROL Database mysql-slow.log]** muestra los tipos de instrucciones de consulta que estaban en el archivo `mysql-slow.log` en el periodo de tiempo seleccionado.
