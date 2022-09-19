---
user-guide-title: Guía de instalación
user-guide-description: Obtenga información sobre cómo instalar Adobe Commerce y Magento Open Source para implementaciones locales.
source-git-commit: 949ef8d2036ceeef3cc892a5063ddecc2586a6a9
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---


# Guía de instalación {#installation-guide}

- [Información general](overview.md)
- [Requisitos del sistema](system-requirements.md)
- Requisitos previos {#prerequisites}
   - [Información general](prerequisites/overview.md)
   - Sistema de archivos {#file-system}
      - [Información general](prerequisites/file-system/overview.md)
      - [Configuración de permisos](prerequisites/file-system/configure-permissions.md)
   - Servidor web {#web-server}
      - [Nginx](prerequisites/web-server/nginx.md)
      - [Apache](prerequisites/web-server/apache.md)
   - Servidor de bases de datos {#database-server}
      - [MySQL](prerequisites/database/mysql.md)
      - [Conexiones remotas](prerequisites/database/mysql-remote.md)
   - Motor de búsqueda {#search-engine}
      - [Información general](prerequisites/search-engine/overview.md)
      - [AWS OpenSearch](prerequisites/search-engine/aws-opensearch.md)
      - [Configurar Nginx](prerequisites/search-engine/configure-nginx.md)
      - [Configurar Apache](prerequisites/search-engine/configure-apache.md)
   - [PHP](prerequisites/php-settings.md)
   - [Agente de mensajes](prerequisites/rabbitmq.md)
   - [Seguridad](prerequisites/security.md)
   - [Claves de autenticación](prerequisites/authentication-keys.md)
   - [Adobe Commerce](prerequisites/commerce.md)
   - [Software opcional](prerequisites/optional-software.md)
- [Instalación rápida](composer.md)
- [Instalación avanzada](advanced.md)
- Pasos posteriores a la instalación {#next-steps}
   - [Verifique la instalación](next-steps/verify.md)
   - [Configuración de la aplicación](next-steps/configuration.md)
   - [Establecer una máscara (opcional)](next-steps/set-umask.md)
   - Instalación de datos de ejemplo (opcional) {#sample-data}
      - [Información general](sample-data/overview.md)
      - [Descargar paquetes del Compositor](sample-data/composer-packages.md)
      - [Clonar repositorios Git](sample-data/git-repositories.md)
      - [Eliminar o actualizar módulos](sample-data/remove-or-update.md)
- Tutoriales {#tutorials}
   - [Copia de seguridad y reversión del sistema de archivos, medios y base de datos](tutorials/backup.md)
   - [Comprobar el estado de la base de datos](tutorials/database-status.md)
   - [Configurar el comportamiento del consumidor de mensajes](tutorials/message-consumers.md)
   - [Configuración del proveedor de bloqueo](tutorials/lock-provider.md)
   - [Configuración de la tienda](tutorials/store.md)
   - [Crear, editar o desbloquear cuentas de administrador](tutorials/admin.md)
   - [Crear o actualizar la configuración de implementación](tutorials/deployment.md)
   - [Crear el esquema de la base de datos](tutorials/database.md)
   - [Mostrar o cambiar el URI de administración](tutorials/admin-uri.md)
   - [Habilitar o deshabilitar el modo de mantenimiento](tutorials/maintenance-mode.md)
   - [Habilitar o deshabilitar módulos](tutorials/manage-modules.md)
   - [Instalación de una extensión](tutorials/extensions.md)
   - [Instalar Commerce](tutorials/install.md)
   - [Modificar docroot para mejorar la seguridad](tutorials/docroot.md)
   - [Desinstalación de paquetes de idiomas](tutorials/language-packages.md)
   - [Desinstalar módulos](tutorials/uninstall-modules.md)
   - [Desinstalar o reinstalar Commerce](tutorials/uninstall.md)
   - [Desinstalación de temas](tutorials/themes.md)
   - [Actualizar el esquema de la base de datos](tutorials/database-upgrade.md)