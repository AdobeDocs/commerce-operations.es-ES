---
title: Modos de aplicación
description: La aplicación de Commerce puede funcionar en diferentes modos según sus necesidades. Vea una lista detallada de los modos de aplicación disponibles.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: c415c3427f513255b9d4ebe1d24ba4024df21928
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Modos de aplicación

Puede ejecutar la aplicación Commerce en cualquiera de los _modos_ siguientes:

| Nombre del modo | Descripción | Compatibilidad con Cloud |
| ------------------------ | ------------------- | ------------- |
| [predeterminado](#default-mode) | Implemente y ejecute la aplicación de Commerce en un solo servidor sin cambiar la configuración. _No_ optimizado para la producción. | no |
| [desarrollador](#developer-mode) | Ideal para el desarrollo al ampliar o personalizar la aplicación de Commerce. | no |
| [producción](#production-mode) | Implemente y ejecute la aplicación de Commerce en un sistema de producción. | Sí |
| [mantenimiento](#maintenance-mode) | Impida el acceso a un sitio mientras realiza actualizaciones y configuraciones. | Sí |

Consulte [Establecer el modo de operación](../cli/set-mode.md) para obtener información sobre cómo cambiar manualmente los modos de operación de Adobe Commerce.

## Compatibilidad con Cloud

Debido al sistema de archivos de solo lectura, existe una estricta restricción contra el cambio de modos en entornos de nube remotos y el Soporte técnico de Adobe Commerce no puede anularlo. No intente cambiar los modos modificando el archivo `app/etc/env.php` porque el paquete `ece-tools` sobrescribe el archivo basándose en varios orígenes de configuración.

Adobe Commerce en la infraestructura en la nube ejecuta automáticamente la aplicación en modo _mantenimiento_ durante una implementación, lo que desconecta el sitio hasta que se completa la implementación. De lo contrario, la aplicación permanecerá en modo _producción_. Consulte [Proceso de implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=es#deploy-phase) en la guía de _Commerce en infraestructura de nube_.

Si usa Cloud Docker para Commerce como herramienta de desarrollo, puede implementar su proyecto de infraestructura en la nube en un entorno de Docker en modo _desarrollador_, pero el rendimiento es más lento debido a las operaciones de sincronización de archivos adicionales. Consulte [Implementar el entorno de Docker](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) en la guía de _Cloud Docker para Commerce_.


## Modo predeterminado

El modo _default_ le permite implementar la aplicación Commerce en un solo servidor sin cambiar la configuración. Sin embargo, el modo predeterminado no está optimizado para la producción debido al impacto negativo en el rendimiento de los archivos estáticos. La creación de archivos estáticos y su almacenamiento en caché tienen un mayor impacto en el rendimiento que su generación con la herramienta de creación de archivos estáticos.

En modo predeterminado:

- Las excepciones se escriben en archivos de registro en lugar de mostrarse
- Los archivos de vista estática se almacenan en caché
- Oculta los encabezados personalizados de solicitud y respuesta HTTP `X-Magento-*`

Commerce funciona en modo predeterminado si no se especifica otro modo.

## Modo de desarrollador

Se recomienda el modo _developer_ para ampliar y personalizar la aplicación Commerce. Los archivos de vista estática no se almacenan en caché, sino que se escriben en el directorio `pub/static` bajo demanda.

En modo de desarrollador:

- Habilita [compilación automática de código](../cli/code-compiler.md) y depuración mejorada
- Las excepciones no capturadas se muestran en el explorador
- El registro del sistema en `var/report` es detallado
- Se produce una excepción en el controlador de errores, en lugar de registrarse
- Se produce una excepción cuando no se puede invocar a un suscriptor de eventos
- Muestra encabezados de solicitud y respuesta HTTP `X-Magento-*` personalizados

>[!NOTE]
>
>Este modo no es compatible con el entorno de Adobe Commerce Cloud y la asistencia de Adobe Commerce no puede facilitar el cambio del modo de la aplicación.

## Modo de producción

El modo _production_ es el mejor para implementar la aplicación Commerce en un sistema de producción. Después de optimizar el entorno del servidor, como la base de datos y el servidor web, debe ejecutar la [herramienta de implementación de archivos de vista estática](../cli/static-view-file-deployment.md) para escribir archivos de vista estática en el directorio `pub/static`. Esto mejora el rendimiento al proporcionar todos los archivos estáticos necesarios en la implementación en lugar de obligar a la aplicación de Commerce a localizar y copiar (materializar) dinámicamente archivos estáticos bajo demanda durante el tiempo de ejecución.

Algunos campos, como las secciones Avanzado y Configuración del sistema del desarrollador en Admin, no están disponibles en el modo de producción. Por ejemplo, _no puede_ habilitar o deshabilitar tipos de caché usando el administrador. Puede habilitar y deshabilitar los tipos de caché _solamente_ mediante la [línea de comandos](../cli/manage-cache.md#config-cli-subcommands-cache-en).

En modo de producción:

- Los archivos de vista estática solo se proporcionan desde la caché
- Los errores y excepciones se registran en el sistema de archivos y nunca se muestran al usuario
- Algunos campos de configuración del Administrador no están disponibles

## Modo de mantenimiento

El modo _mantenimiento_ limita o impide el acceso a un sitio durante las mejoras, actualizaciones y tareas de configuración. De manera predeterminada, el sitio redirige a los visitantes a una página predeterminada de `Service Temporarily Unavailable`.

Puede crear una [página de mantenimiento personalizada](../../upgrade/troubleshooting/maintenance-mode-options.md), habilitar y deshabilitar manualmente el modo de mantenimiento y configurar el modo de mantenimiento para permitir que los visitantes de direcciones IP autorizadas vean la tienda normalmente. Consulte [habilitar y deshabilitar el modo de mantenimiento](../../installation/tutorials/maintenance-mode.md) en la _Guía de instalación_.

Si utiliza Commerce en la infraestructura de la nube, la aplicación de Commerce se ejecuta en modo de mantenimiento durante la fase de implementación. Cuando la implementación se completa correctamente, la aplicación de Commerce vuelve a ejecutarse en el modo de producción. Consulte [Vínculos de implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html?lang=es#phase-5%3A-deployment-hooks) en la guía de _Commerce en infraestructura de nube_.

En modo de mantenimiento:

- Los visitantes del sitio son redirigidos a una página predeterminada `Service Temporarily Unavailable`
- El directorio `var/` contiene el archivo `.maintenance.flag`
- Puede limitar el acceso de los visitantes en función de las direcciones IP
