---
title: Modos de aplicación
description: La aplicación Commerce puede funcionar en diferentes modos según sus necesidades. Vea una lista detallada de los modos de aplicación disponibles.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: 5003e8dcbb3736201ea19ebe30d5e56775096157
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 0%

---

# Modos de aplicación

Puede ejecutar la aplicación Commerce en cualquiera de las siguientes opciones _modos_:

| Nombre del modo | Descripción | Compatibilidad con Cloud |
| ------------------------ | ------------------- | ------------- |
| [predeterminado](#default-mode) | Implemente y ejecute la aplicación Commerce en un solo servidor sin cambiar la configuración. _No_ optimizado para la producción. | no |
| [promotor](#developer-mode) | Ideal para el desarrollo al ampliar o personalizar la aplicación Commerce. | no |
| [producción](#production-mode) | Implemente y ejecute la aplicación Commerce en un sistema de producción. | Sí |
| [mantenimiento](#maintenance-mode) | Impida el acceso a un sitio mientras realiza actualizaciones y configuraciones. | Sí |

Consulte [Definición del modo de funcionamiento](../cli/set-mode.md) para aprender a cambiar manualmente los modos de funcionamiento de Adobe Commerce.

## Compatibilidad con Cloud

Debido al sistema de archivos de solo lectura, no puede cambiar los modos en los entornos de nube remotos. No intente cambiar los modos modificando la variable `app/etc/env.php` porque la variable `ece-tools` sobrescribe el archivo en función de varios orígenes de configuración.

Adobe Commerce en la infraestructura en la nube ejecuta automáticamente la aplicación en _mantenimiento_ durante una implementación, lo que desconecta el sitio hasta que se completa la implementación. De lo contrario, la aplicación permanece en _producción_ modo. Consulte [Proceso de implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) en el _Guía de Commerce en infraestructura en la nube_.

Si utiliza Cloud Docker para Commerce como herramienta de desarrollo, puede implementar su proyecto de infraestructura en la nube en un entorno de Docker en _promotor_ modo, pero el rendimiento es más lento debido a las operaciones de sincronización de archivos adicionales. Consulte [Implementación del entorno de Docker](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) en el _Guía de Cloud Docker para Commerce_.

## Modo predeterminado

El _predeterminado_ Este modo permite implementar la aplicación Commerce en un solo servidor sin cambiar la configuración. Sin embargo, el modo predeterminado no está optimizado para la producción debido al impacto negativo en el rendimiento de los archivos estáticos. La creación de archivos estáticos y su almacenamiento en caché tienen un mayor impacto en el rendimiento que su generación con la herramienta de creación de archivos estáticos.

En modo predeterminado:

- Las excepciones se escriben en archivos de registro en lugar de mostrarse
- Los archivos de vista estática se almacenan en caché
- Oculta personalizado `X-Magento-*` Encabezados de solicitud y respuesta HTTP

Commerce funciona en modo predeterminado si no se especifica otro modo.

## Modo de desarrollador

El _promotor_ se recomienda el modo para ampliar y personalizar la aplicación de Commerce. Los archivos de vista estática no se almacenan en caché, sino que se escriben en `pub/static` directorio bajo demanda.

En modo de desarrollador:

- Habilita [compilación automática de código](../cli/code-compiler.md) y depuración mejorada
- Las excepciones no capturadas se muestran en el explorador
- Inicio de sesión del sistema `var/report` es detallado
- Se produce una excepción en el controlador de errores, en lugar de registrarse
- Se produce una excepción cuando no se puede invocar a un suscriptor de eventos
- Muestra personalizado `X-Magento-*` Encabezados de solicitud y respuesta HTTP

## Modo de producción

El _producción_ El modo es mejor para implementar la aplicación Commerce en un sistema de producción. Después de optimizar el entorno del servidor, como la base de datos y el servidor web, debe ejecutar el [herramienta de implementación de archivos de vista estática](../cli/static-view-file-deployment.md) para escribir archivos de vista estática en `pub/static` directorio. Esto mejora el rendimiento al proporcionar todos los archivos estáticos necesarios en la implementación en lugar de obligar a la aplicación Commerce a localizar y copiar (materializar) dinámicamente archivos estáticos bajo demanda durante el tiempo de ejecución.

Algunos campos, como las secciones Avanzado y Configuración del sistema del desarrollador en Admin, no están disponibles en el modo de producción. Por ejemplo, puede _no puede_ habilite o deshabilite los tipos de caché mediante el Administrador. Puede habilitar y deshabilitar los tipos de caché _solamente_ uso del [línea de comandos](../cli/manage-cache.md#config-cli-subcommands-cache-en).

En modo de producción:

- Los archivos de vista estática solo se proporcionan desde la caché
- Los errores y excepciones se registran en el sistema de archivos y nunca se muestran al usuario
- Algunos campos de configuración del Administrador no están disponibles

## Modo de mantenimiento

El _mantenimiento_ limita o impide el acceso a un sitio durante las mejoras, actualizaciones y tareas de configuración. De forma predeterminada, el sitio redirige a los visitantes a una ubicación predeterminada `Service Temporarily Unavailable` página.

Puede crear un [página de mantenimiento personalizada](../../upgrade/troubleshooting/maintenance-mode-options.md), habilite y deshabilite manualmente el modo de mantenimiento, y configure el modo de mantenimiento para permitir que los visitantes de direcciones IP autorizadas vean la tienda normalmente. Consulte [activar y desactivar el modo de mantenimiento](../../installation/tutorials/maintenance-mode.md) en el _Guía de instalación_.

Si utiliza Commerce en la infraestructura de la nube, la aplicación Commerce se ejecuta en modo de mantenimiento durante la fase de implementación. Cuando la implementación se completa correctamente, la aplicación de Commerce vuelve a ejecutarse en el modo de producción. Consulte [Enlaces de implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) en el _Guía de Commerce en infraestructura en la nube_.

En modo de mantenimiento:

- Los visitantes del sitio se redirigen a un valor predeterminado `Service Temporarily Unavailable` página
- El `var/` El directorio contiene `.maintenance.flag` archivo
- Puede limitar el acceso de los visitantes en función de las direcciones IP
