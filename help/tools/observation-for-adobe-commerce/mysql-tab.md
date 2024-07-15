---
title: La ficha [!UICONTROL MySQL]
description: Obtenga información acerca de la ficha [!UICONTROL MySQL] de  [!DNL Observation for Adobe Commerce].
exl-id: 1d8dd07c-15fd-4ffd-ad10-0d886bf1579e
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 0%

---

# La ficha [!UICONTROL MySQL]

## [!UICONTROL MySQL% free storage by node]

![MySQL% de almacenamiento gratuito por nodo](../../assets/tools/observation-for-adobe-commerce/mysql-tab-1.jpg)

Muchos problemas se deben a que MySQL se está quedando sin almacenamiento en el almacenamiento asignado a MySQL (`datadir` configuración de MySQL, el valor predeterminado es `/data/mysql`) o a que `tmpdir` se está quedando sin espacio. El valor predeterminado `tmpdir` (configuración de MySQL) es `/tmp`. El fotograma **[!UICONTROL MySQL% free storage by node]** examina `/, /tmp` (si se define como un montaje independiente) y el porcentaje `/data/mysql` de almacenamiento libre. A partir de MySQL versión 5.7 (MariaDB versión 10.2), las tablas `tmp` sin comprimir se escriben en un tablespace `tmp` en el directorio `/data/mysql` del archivo (ibtmp1). Este archivo se expande automáticamente sin límite de forma predeterminada. Como es un tablespace, no disminuirá de tamaño y se restablecerá a 12 MB cuando se reinicie MySQL.

## [!UICONTROL MySQL Connections by Node]

![Conexiones MySQL por nodo](../../assets/tools/observation-for-adobe-commerce/mysql-tab-2.jpg)

El marco **[!UICONTROL MySQL Connections by Node]** indica períodos de interrupciones en el nodo de la base de datos o volúmenes altos de conexiones.

## [!UICONTROL MySQL Node Summary]

![Resumen de nodos MySQL](../../assets/tools/observation-for-adobe-commerce/mysql-tab-3.jpg)

La tabla **[!UICONTROL MySQL Node Summary]** muestra detalles del nodo de la base de datos, como la versión del software y el tipo de instancia (tamaño).

## [!UICONTROL Galera Number of Nodes in cluster]

![Número de nodos de galera en el clúster](../../assets/tools/observation-for-adobe-commerce/mysql-tab-4.jpg)

El marco **[!UICONTROL Galera Number of Nodes in cluster]** muestra información de los registros MySQL. A medida que los nodos se unen y salen de un clúster, solo se mostrarán los mensajes del periodo de tiempo seleccionado. Si un nodo abandona el clúster antes del periodo de tiempo, no aparecerá ningún mensaje durante ese periodo de tiempo. Si cree que la base de datos puede estar quedando corta de un nodo, expanda el periodo de tiempo a un periodo mayor para ver si puede ver información adicional. Si hay información durante el período de tiempo que indica menos que todos los nodos del clúster [!DNL Galera], expanda el intervalo de tiempo para ver si puede determinar cuándo abandonó el nodo el clúster.

## [!UICONTROL MySQL shutdowns and starts]

![MySQL cierra e inicia](../../assets/tools/observation-for-adobe-commerce/mysql-tab-5.jpg)

El marco **[!UICONTROL MySQL shutdowns and starts]** detecta cuándo se apaga un nodo. Los nodos [!DNL Galera] se expulsarán y se autoexpulsarán del nodo [!DNL Galera]. Esto generalmente resulta en un reinicio del servicio MySQL.

## [!UICONTROL Galera log]

![Registro de galeras](../../assets/tools/observation-for-adobe-commerce/mysql-tab-6.jpg)

El marco **[!UICONTROL Galera log]** muestra el recuento de señales particulares de los registros MySQL relacionados con [!DNL Galera] nodos, sus estados y los cambios de estado del clúster [!DNL Galera].

* &#39;%1047 WSREP aún no ha preparado el nodo para el uso de la aplicación (%) como &#39;node_not_prep_for_use&#39;
* &#39;%\[ERROR\] WSREP: No se pudo leer de: wsrep_sst_xtrabackup-v2%&#39;) como &#39;xtrabackup_read_fail&#39;
* &#39;%\[ERROR\] WSREP: Proceso completado con error: wsrep_sst_xtrabackup-v2 %&#39;) as &#39;xtrabackup_compl_w_err&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) as &#39;rbr_write_fail&#39;
* &#39;%self-left%&#39;) como &#39;susp_node&#39;
* &#39;%members = 3/3 (unidos/total)%&#39;) as&#39;3de3&#39;
* &#39;%members = 2/3 (unidos/total)%&#39;) as&#39;2of3&#39;
* &#39;%members = 2/2%&#39;) como &#39;2of2&#39;
* &#39;%members = 1/2%&#39;) como &#39;1of2&#39;
* &#39;%members = 1/3%&#39;) como &#39;1of3&#39;
* &#39;%members = 1/1%&#39;) como &#39;1of1&#39;
* &#39;%\[Nota\] /usr/sbin/mysqld (mysqld 10.%&#39;) as&#39;sql_restart&#39;
* &#39;%Quorum: no hay ningún nodo con estado completo:%&#39;) como &#39;no_node_count&#39;
* &#39;%WSREP: miembro 0%&#39;) como &#39;mem_0&#39;
* &#39;%WSREP: miembro 1,0%&#39;) como &#39;mem_1&#39;
* &#39;%WSREP: miembro 2%&#39;) as&#39;mem2&#39;
* &#39;%WSREP: sincronizado con el grupo, listo para conexiones%&#39;) como &#39;listo&#39;
* &#39;%/usr/sbin/mysqld, Version:%&#39;) as &#39;mysql_restart_mysql.slow&#39;
* &#39;%\[Nota\] WSREP: Nueva vista de clúster: estado global:%&#39;) como &#39;galera_cluster_view_chang&#39;

## [!UICONTROL Galera Log by Host]

![Registro de Galera por el host](../../assets/tools/observation-for-adobe-commerce/mysql-tab-7.jpg)

El marco **[!UICONTROL Galera Log by Host]** es el mismo que el marco **[!UICONTROL Galera log]**, con la diferencia de que está dividido por nodos para ayudar a solucionar problemas.

## [!UICONTROL Database performance]

![Rendimiento de la base de datos](../../assets/tools/observation-for-adobe-commerce/mysql-tab-8.jpg)

El marco **[!UICONTROL Database performance]** muestra el rendimiento de la base de datos durante solicitudes específicas. Puede ver cada métrica haciendo clic en ella en los iconos de color debajo del gráfico. Muchas de las métricas llamadas en [Monitorización del rendimiento de la base de datos MySQL con New Relic](https://newrelic.com/blog/how-to-relic/how-to-monitor-mysql) se encuentran en este marco.

* average(query.queriesPerSecond)
* average(query.slowQueriesPerSecond)
* average(db.createdTmpDiskTablesPerSecond)
* average(db.createdTmpFilesPerSecond)
* average(db.tablesLocksWaitedPerSecond)
* average(db.innodb.rowLockTimeAvg)
* average(db.innodb.rowLockWaitsPerSecond)

## [!UICONTROL Transaction Database Call Count]

![Recuento de llamadas a base de datos de transacciones](../../assets/tools/observation-for-adobe-commerce/mysql-tab-9.jpg)

El marco **[!UICONTROL Transaction Database Call Count]** muestra el número de llamadas a la base de datos realizadas por cada faceta de transacción. Esto parece estar centrado en la fila y no en las instrucciones.

## [!UICONTROL Cron_schedule table updates]

![Actualizaciones de tabla Cron_schedule](../../assets/tools/observation-for-adobe-commerce/mysql-tab-10.jpg)

El marco **[!UICONTROL Cron_schedule table updates]** muestra la duración máxima de las actualizaciones de la base de datos en la tabla cron_schedule durante el período de tiempo seleccionado.

## [!UICONTROL Slow Query Traces]

![Seguimientos de consultas lentas](../../assets/tools/observation-for-adobe-commerce/mysql-tab-11.jpg)

El marco **[!UICONTROL Slow Query Traces]** muestra la tabla y el tipo de solicitud donde existen trazos de consulta lentos. Se crea un seguimiento de consulta lento para las transacciones de consulta que tardan más de cinco segundos. De importancia para este marco son las consultas de actualización. Si una tabla se actualiza mediante las instrucciones `UPDATE`, `DELETE` y `INSERT`, pueden bloquear las tablas durante un período de tiempo.

Incluso las instrucciones `SELECT` pueden bloquear filas si se utilizan con FOR UPDATE.

## [!UICONTROL Datastore Operations tables]

![Tablas de operaciones del almacén de datos](../../assets/tools/observation-for-adobe-commerce/mysql-tab-12.jpg)

## [!UICONTROL Cron table change]

![Cambio de tabla Cron](../../assets/tools/observation-for-adobe-commerce/mysql-tab-13.jpg)

El marco **[!UICONTROL Cron table change]** busca mensajes de error &quot;no se pudo adquirir el bloqueo para el trabajo cron:&quot;, junto con un error específico de memoria PHP y bloqueos que involucran la tabla `cron_schedule`. Si la tabla `cron_schedule` está bloqueada (por ejemplo, por una consulta `DELETE` que se está ejecutando en ella), bloqueará la ejecución de otros crons.

## [!UICONTROL Deadlocks]

![Interbloqueos](../../assets/tools/observation-for-adobe-commerce/mysql-tab-14.jpg)

El marco **[!UICONTROL Deadlocks]** observa las siguientes cadenas analizadas desde los registros MySQL:

* &#39;%PHP Error grave: tamaño de memoria permitido (%) como php_mem_error
* &#39;%get lock; intente reiniciar la transacción, la consulta era: DELETE FROM \`cron_schedule%&#39;) as cron_sched_lock_del
* &#39;% lock para el trabajo cron: indexer_reindex_all_invalid%&#39;) as &#39;lock_indexer_reindex_all_invalid%&#39;
* &#39;% lock para trabajo cron: cron_schedule%&#39;) as &#39;lock_cron_schedule&#39;
* &#39;% lock para trabajo cron:%&#39;) como &#39;total_cron_lock&#39;
* &#39;%Error general: 1205 Se superó el tiempo de espera de bloqueo (%) como &#39;sql_1205_lock&#39;
* &#39;%ERROR 1213 (40001): se encontró un interbloqueo al intentar obtener el bloqueo (%) como &#39;sql_1213_lock&#39;
* &#39;%SQLSTATE[40001]: Error de serialización: se encontró un interbloqueo 1213%&#39;) como &#39;sql_1213_lock2&#39;
* &#39;% lock para el trabajo cron: indexer_update_all_views%&#39;) as &#39;lock_indexer_update_all_views&#39;
* &#39;% lock para trabajo cron: sales_grid_order_invoice_async_insert%&#39;) as &#39;lock_sales_grid_order_invoice_async_insert&#39;,
* &#39;% lock para el trabajo cron: staging_remove_updates%&#39;) as &#39;lock_staging_remove_updates&#39;
* &#39;% lock para trabajo cron: sales_grid_order_shipping_async_insert%&#39;) as &#39;lock_sales_grid_order_shipping_async_insert&#39;
* &#39;% lock para trabajo cron: amazon_payments_process_queued_reembolsos%&#39;) como &#39;lock_amazon_payments_process_queued_reembolsos&#39;
* &#39;% lock para trabajo cron: sales_send_order_shipping_emails%&#39;) as &#39;lock_sales_send_order_shipping_emails&#39;
* &#39;% lock para el trabajo cron: staging_sync_entities_period%&#39;) as &#39;lock_staging_sync_entities_period&#39;
* &#39;% bloqueo para trabajo cron: indexer_clean_all_changelogs%&#39;) como &#39;lock_indexer_clean_all_changelogs&#39;
* &#39;% lock para trabajo cron: magento_targetrule_index_reindex%&#39;) as &#39;lock_magento_targetrule_index_reindex&#39;
* &#39;% lock para trabajo cron: newsletter_send_all%&#39;) as &#39;lock_newsletter_send_all&#39;
* &#39;% lock para trabajo cron: newsletter_send_all%&#39;) as &#39;lock_newsletter_send_all&#39;
* &#39;% lock para trabajo cron: sales_send_order_emails%&#39;) as &#39;lock_sales_send_order_emails&#39;
* &#39;% lock para trabajo cron: sales_send_order_creditmemo_emails%&#39;) as &#39;lock_sales_send_order_creditmemo_emails&#39;
* &#39;% lock para trabajo cron: sales_grid_order_creditmemo_async_insert%&#39;) as &#39;lock_sales_grid_order_creditmemo_async_insert&#39;
* &#39;% lock para el trabajo cron: bulk_cleanup%&#39;) as &#39;lock_bulk_cleanup&#39;
* &#39;% lock para el trabajo cron: flush_preview_quotas%&#39;) as &#39;lock_flush_preview_quotas&#39;
* &#39;% lock para el trabajo cron: sales_send_order_invoice_emails%&#39;) as &#39;lock_sales_send_order_invoice_emails&#39;
* &#39;% lock para el trabajo cron: sales_send_order_invoice_emails%&#39;) as &#39;lock_sales_send_order_invoice_emails&#39;
* &#39;% lock para trabajo cron: captcha_delete_expire_images%&#39;) as &#39;lock_captcha_delete_expire_images&#39;
* &#39;% lock para trabajo cron: magento_newrelicreporting_cron%&#39;) as &#39;lock_magento_newrelicreporting_cron&#39;
* &#39;% lock para el trabajo cron: outdated_authentication_failures_cleanup%&#39;) as &#39;lock_outdated_authentication_failures_cleanup&#39;
* &#39;% lock para trabajo cron: send_notification%&#39;) as &#39;lock_send_notification&#39;
* &#39;% lock para trabajo cron: magento_giftcardaccount_generage_codes_pool%&#39;) as &#39;lock_magento_giftcardaccount_generage_codes_pool&#39;
* &#39;% lock para trabajo cron: catalog_product_frontend_actions_flush%&#39;) as &#39;lock_catalog_product_frontend_actions_flush&#39;
* &#39;% bloqueo para trabajo cron: mysqlmq_clean_messages%&#39;) como &#39;mysqlmq_clean_messages&#39;
* &#39;% lock para el trabajo cron: catalog_product_attribute_value_sync%&#39;) as &#39;lock_catalog_product_attribute_value_sync&#39;
* &#39;% lock para trabajo cron: ddg_automation_importer%&#39;) como &#39;lock_ddg_automation_importer&#39;
* &#39;% de bloqueo para el trabajo cron: ddg_automation_review_and_wishlist%&#39;) como &#39;lock_ddg_automation_review_and_wishlist&#39;
* &#39;% lock para trabajo cron: captcha_delete_old_tries%&#39;) as &#39;lock_captcha_delete_old_tries&#39;
* &#39;% lock para trabajo cron: catalog_product_outdated_price_values_cleanup%&#39;) as &#39;lock_catalog_product_outdated_price_values_cleanup&#39;
* &#39;% lock para el trabajo cron: consumer_runner%&#39;) as &#39;lock_consumer_runner&#39;
* &#39;% de bloqueo para el trabajo cron: ddg_automation_customer_subscriber_guest_sync%&#39;) como &#39;lock_ddg_automation_customer_subscriber_guest_sync&#39;
* &#39;% lock para trabajo cron: get_amazon_capture_updates%&#39;) as &#39;lock_get_amazon_capture_updates&#39;
* &#39;% lock para trabajo cron: get_amazon_authorization_updates%&#39;) as &#39;lock_send_get_amazon_authorization_updates&#39;
* &#39;% lock para cron job: temando_process_platform_events%&#39;) as &#39;lock_temando_process_platform_events&#39;
* &#39;% lock para trabajo cron: ddg_automation_status%&#39;) as &#39;lock_ddg_automation_status&#39;
* &#39;% lock para trabajo cron: ddg_automation_status%&#39;) as &#39;lock_ddg_automation_status&#39;
* &#39;% lock para trabajo cron: sales_clean_orders%&#39;) as &#39;lock_sales_clean_orders&#39;
* &#39;% lock para el trabajo cron: catalog_index_refresh_price%&#39;) como &#39;lock_catalog_index_refresh_price&#39;
* &#39;% lock para trabajo cron: magento_premio_balance_warning_notification%&#39;) como &#39;lock_magento_recompensa_balance_warning_notification&#39;
* &#39;% lock para trabajo cron: analytics_update%&#39;) as &#39;lock_analytics_update&#39;
* &#39;% lock para trabajo cron: messagequeue_clean_outdated_locks%&#39;) as &#39;lock_messagequeue_clean_outdated_locks&#39;
* &#39;% lock para trabajo cron: messagequeue_clean_outdated_locks%&#39;) as &#39;lock_messagequeue_clean_outdated_locks&#39;
* &#39;% lock para el trabajo cron: staging_apply_version%&#39;) as &#39;lock_staging_apply_version&#39;
* &#39;% lock para trabajo cron: magento_recompensa_expira_points%&#39;) as &#39;lock_magento_recompensa_expira_points&#39;
* &#39;% lock para trabajo cron: yotpo_yotpo_orders_sync%&#39;) as &#39;lock_yotpo_yotpo_orders_sync&#39;
* &#39;% lock para el trabajo cron: catalog_event_status_checker%&#39;) como &#39;lock_catalog_event_status_checker&#39;
* &#39;% lock para trabajo cron: ddg_automation_campaign%&#39;) as &#39;lock_ddg_automation_campaign&#39;
* &#39;% lock para trabajo cron: visitor_clean%&#39;) as &#39;lock_visitor_clean&#39;
* &#39;% lock para el trabajo cron: scconnector_verify_website%&#39;) as &#39;lock_scconnector_verify_website&#39;
* &#39;% lock para trabajo cron: ddg_automation_email_templates%&#39;) as &#39;lock_ddg_automation_email_templates&#39;
* &#39;% lock para trabajo cron: aggregate_sales_report_order_data%&#39;) as &#39;lock_aggregate_sales_report_order_data&#39;
* &#39;% lock para trabajo cron: ddg_automation_catalog_sync%&#39;) as &#39;lock_ddg_automation

## [!UICONTROL DB Statistics]

![Estadísticas de BD](../../assets/tools/observation-for-adobe-commerce/mysql-tab-15.jpg)

El marco **[!UICONTROL DB Statistics]** muestra eliminaciones, escrituras, filas leídas, actualizaciones y consultas lentas por segundo.

## [!UICONTROL Request frequency]

![Frecuencia de solicitud](../../assets/tools/observation-for-adobe-commerce/mysql-tab-16.jpg)

## [!UICONTROL Database Errors]

![Errores de base de datos](../../assets/tools/observation-for-adobe-commerce/mysql-tab-17.jpg)

El marco **[!UICONTROL Database Errors]** muestra diversas [advertencias y errores](https://mariadb.com/kb/en/mariadb-error-codes/) de la base de datos:

* &#39;%El tamaño de memoria asignado para la tabla temporal es superior al 20% de innodb_buffer_pool_size%&#39; como &#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) as &#39;rbr_write_fail&#39;
* &#39;%mysqld: Disco lleno%&#39;) como &#39;disk_full&#39;
* &#39;%Error número 28%&#39;) como &#39;err_28&#39;
* &#39;%rollback%&#39;) como &#39;rollback&#39;
* &#39;%Foreign key constraint falla para table%&#39;) como &#39;Foreign_key_constraint&#39;
* &#39;%Error_code: 1114%&#39;) as &#39;sql_1114_full&#39;%CRITICAL: SQLSTATE[HY000] [2006] El servidor MySQL ha desaparecido%&#39;) as &#39;sql_gone&#39;
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
* &#39;%SQLSTATE[42000]: error de sintaxis o infracción de acceso:%&#39;) as&#39;sql_42000&#39;
* &#39;%SQLSTATE[21000]: Infracción de cardinalidad:%&#39;) como &#39;sql_1241&#39;
* &#39;%SQLSTATE[22003]:%&#39;) como &#39;sql_22003&#39;
* &#39;%SQLSTATE[HY000] [9000] cliente con dirección IP%&#39;) como &#39;sql_9000&#39;
* &#39;%SQLSTATE[HY000]: Error general: 2014%&#39;) como &#39;sql_2014&#39;
* &#39;%1927 Conexión se eliminó%&#39;) como &#39;sql_1927&#39;
* &#39;%1062 \[ERROR\] InnoDB:%&#39;) como &#39;sql_1062_e&#39;
* &#39;&#39;%[Nota] WSREP: vaciando asignación de memoria al disco...%&#39;) como &#39;mem_map_flush&#39;
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
* &#39;%InnoDB: Error (clave duplicada)%&#39;) as &#39;innodb_dup_key&#39; FROM Log TIMESERIES

## [!UICONTROL DB Error Table]

![Tabla de errores de BD](../../assets/tools/observation-for-adobe-commerce/mysql-tab-18.jpg)

El marco **[!UICONTROL DB Error Table]** muestra la misma información que el marco **[!UICONTROL Database Errors]**, pero puede verlo por nodo y en formato de tabla. Consulte [Códigos de error de MariaDB](https://mariadb.com/kb/en/mariadb-error-codes/) para obtener más información.

## [!UICONTROL Database Traces]

![seguimientos de base de datos](../../assets/tools/observation-for-adobe-commerce/mysql-tab-19.jpg)

El fotograma **[!UICONTROL Database Traces]** muestra los seguimientos de la base de datos por tipo en la escala de tiempo seleccionada.

## [!UICONTROL Database processes]

![Procesos de base de datos](../../assets/tools/observation-for-adobe-commerce/mysql-tab-20.jpg)

El marco **[!UICONTROL Database processes]** muestra los procesos, entornos e identificadores de nodo de la base de datos.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![Threads no inactivo de MySQL por nodo](../../assets/tools/observation-for-adobe-commerce/mysql-tab-21.jpg)

El marco **[!UICONTROL MySQL Non-Sleeping Threads by Node]** muestra los subprocesos de conexión con la base de datos. Este marco muestra los hilos activos.

## [!UICONTROL MySQL Running and Sleeping Threads by environment]

![MySQL Running and Sleeping Threads por entorno](../../assets/tools/observation-for-adobe-commerce/mysql-tab-22.jpg)

El marco **[!UICONTROL MySQL Running and Sleeping Threads by environment]** muestra las conexiones activas y en espera a la base de datos. Si hay conexiones a la base de datos en las que las consultas lentas se han suspendido, habrá conexiones en suspensión. Las conexiones durmientes pueden ser consultas de base de datos bloqueadas por filas o tablas bloqueadas. Estas conexiones durmientes también tienen conexiones de trabajo PHP.

## [!UICONTROL MySQL mem used by node]

![Mem MySQL utilizado por el nodo](../../assets/tools/observation-for-adobe-commerce/mysql-tab-23.jpg)

El marco **[!UICONTROL MySQL mem used by node]** muestra el uso de memoria del nodo por MySQL. En sitios más grandes, este cuadro puede ser barras continuas con GB de memoria utilizados.

## [!UICONTROL Database mysql-slow.log]

![Base de datos mysql-slow.log](../../assets/tools/observation-for-adobe-commerce/mysql-tab-24.jpg)

El fotograma **[!UICONTROL Database mysql-slow.log]** muestra los tipos de instrucciones de consulta que estaban en el archivo `mysql-slow.log` en el periodo de tiempo seleccionado.
