---
user-guide-title: Guía de configuración
user-guide-description: Configure las funciones y servicios de la aplicación de Adobe Commerce o de Magento Open Source.
feature: Configuration
source-git-commit: b61a2726e1a26229515d28332bbd88ba3d416a98
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---


# Guía de configuración {#configuration-guide}

+ [Información general](overview.md)
+ Configuración general {#setup}
   + [Inicialización de aplicaciones y bootstrap](bootstrap/initialization.md)
   + [Modos de aplicación](bootstrap/application-modes.md)
   + [Parámetros de Bootstrap](bootstrap/set-parameters.md)
   + [Perfilado](bootstrap/mage-profiler.md)
   + [Rutas de directorio base](bootstrap/mage-directory.md)
+ Implementación {#deployment}
   + [Información general de implementación](deployment/overview.md)
   + [Implementación de una sola máquina](deployment/single-machine.md)
   + [Implementación de canalización](deployment/technical-details.md)
   + [Requisitos previos](deployment/prerequisites.md)
   + [Configuración del sistema de desarrollo](deployment/development-system.md)
   + [Configuración del sistema de compilación](deployment/build-system.md)
   + [Configuración del sistema de producción](deployment/production-system.md)
   + [Permisos de acceso a sistemas de archivos](deployment/file-system-permissions.md)
   + Ejemplos {#examples}
      + [Uso de una configuración compartida](deployment/example-shared-configuration.md)
      + [Uso de comandos CLI](deployment/example-using-cli.md)
      + [Uso de variables de entorno](deployment/example-environment-variables.md)
+ Caché {#cache}
   + [Resumen del almacenamiento en caché](cache/caching-overview.md)
   + [Tipos de caché](cache/cache-types.md)
   + [Opciones de caché](cache/cache-options.md)
   + [Caché L2](cache/level-two-cache.md)
   + Redis {#redis}
      + [Configurar Redis](cache/config-redis.md)
      + [Usar Redis para la caché predeterminada](cache/redis-pg-cache.md)
      + [Usar Redis para el almacenamiento de sesión](cache/redis-session.md)
   + Barniz {#varnish}
      + [Descripción general del barniz](cache/config-varnish.md)
      + [Instalar barniz](cache/config-varnish-install.md)
   + [Servidor web](cache/config-varnish-server.md)
   + [Configurar la aplicación de Commerce](cache/configure-varnish-commerce.md)
   + [Configuración avanzada de barniz](cache/config-varnish-advanced.md)
   + [Borrado de caché](cache/use-varnish-cache.md)
   + [Caché que borra varias instancias de Varnish](cache/use-multiple-varnish-cache.md)
   + [Verificar configuración de barniz](cache/config-varnish-final.md)
   + [Barniz Bloque ESI](cache/use-varnish-esi.md)
   + [Caché de contenido estático](cache/static-content-signing.md)
+ Línea de comandos {#cli}
   + [Herramienta de línea de comandos](cli/config-cli.md)
   + [Comandos comunes](cli/common-cli-commands.md)
   + [Habilitar registro](cli/enable-logging.md)
   + [Administrar la caché](cli/manage-cache.md)
   + [Administrar indexadores](cli/manage-indexers.md)
   + [Configuración de trabajos cron](cli/configure-cron-jobs.md)
   + [Compilar código](cli/code-compiler.md)
   + [Modo de funcionamiento](cli/set-mode.md)
   + [Iniciar consumidores de cola de mensajes](cli/start-message-queues.md)
   + [Marcador URN](cli/urn-highlighter.md)
   + [Informes de dependencias](cli/dependency-reports.md)
   + [Localización](cli/localization.md)
   + Administración de configuración {#configuration-management}
      + [Establecer valores](cli/set-configuration-values.md)
      + [Configuración de exportación](cli/export-configuration.md)
      + [Importar datos](cli/import-configuration.md)
   + Vista estática {#static-view}
      + [Estrategias de implementación](cli/static-view-file-strategy.md)
      + [Implementación de archivos de vista estática](cli/static-view-file-deployment.md)
   + [Crear enlaces simbólicos](cli/create-symlinks.md)
   + [Ejecutar pruebas unitarias](cli/unit-tests.md)
   + [Convertir archivos de diseño](cli/convert-layout-files.md)
   + [Generar datos para pruebas de rendimiento](cli/generate-data.md)
   + [Ejecutar utilidades de soporte (solo Commerce)](cli/run-support-utilities.md)
+ Archivos de configuración {#files}
   + [Archivos de configuración para implementación](reference/deployment-files.md)
   + [Tipos de configuración](reference/config-create-types.md)
   + [Archivos de módulo](reference/module-files.md)
   + [Salida de módulo](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [ignorar](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ Rutas de configuración {#paths}
   + [General](reference/config-reference-general.md)
   + [Extensión B2B](reference/config-reference-b2b.md)
   + [Catálogo](reference/config-reference-catalog.md)
   + [Clientes](reference/config-reference-customers.md)
   + [Métodos de pago](reference/config-reference-payment.md)
   + [Ventas](reference/config-reference-sales.md)
   + [Servicios](reference/config-reference-services.md)
   + [Configuración confidencial y específica del sistema](reference/config-reference-sens.md)
   + [Anular los ajustes de configuración](reference/override-config-settings.md)
+ Cron Jobs {#crons}
   + [Trabajos y grupos de Cron](cron/custom-cron.md)
   + [Personalización de la referencia de crons](cron/custom-cron-reference.md)
   + [Configuración de un trabajo cron personalizado](cron/custom-cron-tutorial.md)
+ Registros {#logs}
   + [Registros personalizados](logs/custom-logging.md)
   + [Interfaz de registrador](logs/logger-interface.md)
   + [Registrar actividad de base de datos](logs/database-activity.md)
   + [Escribir en un archivo de registro personalizado](logs/custom-log-files.md)
+ Colas de mensajes {#message-queues}
   + [Marco de cola de mensajes](queues/message-queue-framework.md)
   + [Administrar colas de mensajes](queues/manage-message-queues.md)
   + [Configuración de Amazon MQ](queues/aws-mq.md)
   + [Consumidores](queues/consumers.md)
+ Varios sitios {#multi-sites}
   + [Varios sitios y vistas](multi-sites/ms-overview.md)
   + [ID de incremento de entidad de base de datos](multi-sites/change-increment-id.md)
   + [Configure en el administrador](multi-sites/ms-admin.md)
   + [Configuración con Nginx](multi-sites/ms-nginx.md)
   + [Configuración con Apache](multi-sites/ms-apache.md)
+ Motor de búsqueda {#search}
   + [Descripción general de los motores de búsqueda](search/overview-search.md)
   + [Configuración del motor de búsqueda](search/configure-search-engine.md)
   + [Filtrar con palabras de parada](search/search-stopwords.md)
+ Seguridad {#security}
   + [Información general de seguridad](security/overview.md)
   + [Hashing de contraseñas](security/password-hashing.md)
   + [Intoxicación de caché](security/cache-poisoning.md)
   + [Secure cron PHP](security/secure-cron-php.md)
   + [TXT de seguridad](security/security-txt.md)
   + [Explosiones de secuestro de clics](security/xframe-options.md)
+ Almacenamiento {#storage}
   + [Database profiler](storage/db-profiler.md)
   + Almacenamiento remoto {#remote-storage}
      + [Módulo de almacenamiento remoto](remote-storage/remote-storage.md)
      + [AWS S3 bucket](remote-storage/remote-storage-aws-s3.md)
      + [Cambio de tamaño de imagen](remote-storage/remote-storage-image-resize.md)
      + [Almacenamiento remoto para la nube](remote-storage/cloud-support.md)
   + Almacenamiento de sesión {#session-storage}
      + [Ubicación de almacenamiento de sesión](storage/sessions.md)
      + [memcached para almacenamiento de sesión](storage/memcached.md)
      + [memcached en CentOS](storage/memcache-centos.md)
      + [memcached en Ubuntu](storage/memcache-ubuntu.md)
   + Dividir base de datos {#split-db}
      + [Resumen de base de datos dividida](storage/multi-master.md)
      + [Configuración automática](storage/multi-master-masterdb.md)
      + [Configuración manual](storage/multi-master-manual.md)
      + [Verificar base de datos dividida](storage/multi-master-verify.md)
      + [Replicación de base de datos](storage/multi-master-replication.md)
      + [Revertir a base de datos única](storage/revert-split-database.md)
+ [Volver a Guías operativas](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)