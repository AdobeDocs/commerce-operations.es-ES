---
title: Modos de aplicación
description: La aplicación Commerce puede funcionar en diferentes modos según sus necesidades. Vea una lista detallada de los modos de aplicación disponibles.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 0%

---


# Modos de aplicación

Puede ejecutar la aplicación Commerce en cualquiera de los siguientes _modos_:

| Nombre del módulo | Descripción |
| ----------- | ----------- |
| default | Permite implementar la aplicación Commerce en un solo servidor sin cambiar ninguna configuración. Sin embargo, el modo predeterminado no está optimizado para la producción.<br>Para implementar la aplicación Commerce en más de un servidor o para optimizarla para la producción, cambie a uno de los otros modos.<ul><li>El almacenamiento en caché de archivos de vista estática está habilitado</li><li>Las excepciones no se muestran al usuario; en su lugar, las excepciones se escriben en archivos de registro.</li><li>Oculta elementos personalizados `X-Magento-*` Encabezados de solicitud y respuesta HTTP</li></ul> |
| desarrollador | Solo para desarrollo, este modo:<ul><li>Desactiva el almacenamiento en caché de archivos de vista estática</li><li>Proporciona un registro detallado</li><li>Habilitación [compilación automática de código](../cli/code-compiler.md)</li><li>Habilita la depuración mejorada</li><li>Muestra las `X-Magento-*` Encabezados de solicitud y respuesta HTTP</li><li>Resultados con el rendimiento más lento</li><li>Muestra errores en el front-end</li></ul> |
| producción | Este modo está diseñado para la implementación en un sistema de producción:<ul><li>No muestra excepciones al usuario (las excepciones se escriben solo en registros).</li><li>Sirve archivos de vista estáticos solo desde la caché.</li><li>Evita la compilación automática de archivos de código. Los archivos nuevos o actualizados no se escriben en el sistema de archivos.</li><li>**No le permite habilitar o deshabilitar tipos de caché en Admin.** Consulte [activación y desactivación de la caché](../cli/manage-cache.md#enable-or-disable-cache-types).</li><li>Algunos campos, como las secciones Advanced y Developer system configuration de Admin, no están disponibles en el modo de producción.</li></ul> |
| mantenimiento | Con el fin de evitar el acceso a un sitio mientras se actualiza o reconfigura, este modo:<ul><li>Redirige a los visitantes del sitio a un valor predeterminado `Service Temporarily Unavailable` página.</li><li>Cuando el sitio está en modo de mantenimiento, la variable `var/` contiene el `.maintenance.flag` archivo.</li><li>Puede configurar el modo de mantenimiento para permitir el acceso de los visitantes desde una lista específica de direcciones IP.</li></ul> |

>[!INFO]
>
>[Adobe Commerce en infraestructura en la nube](https://devdocs.magento.com/cloud/bk-cloud.html) solo admite los modos de producción y mantenimiento.

## Modo predeterminado

Como su nombre indica, el modo predeterminado es cómo funciona Commerce si no se especifica otro modo. El modo predeterminado permite implementar la aplicación Commerce en un solo servidor sin cambiar ninguna configuración. Sin embargo, el modo predeterminado no está tan optimizado para la producción como el modo de producción.

Para implementar la aplicación Commerce en más de un servidor o para optimizarla para la producción, cambie a uno de los otros modos.

En modo predeterminado:

- Los errores se registran en los informes de archivos en el servidor y nunca se muestran a un usuario
- Los archivos de vista estáticos se almacenan en caché
- El modo predeterminado no está optimizado para un entorno de producción, principalmente debido al impacto negativo en el rendimiento de [archivos estáticos](https://glossary.magento.com/static-files) se generan de forma dinámica en lugar de materializarse. En otras palabras, la creación de archivos estáticos y el almacenamiento en caché tienen un impacto bueno en el rendimiento que generarlos con la herramienta de creación de archivos estáticos.

Consulte [Definir el modo de operación](../cli/set-mode.md).

## Modo de desarrollador

Ejecute la aplicación Commerce en modo de desarrollador cuando la amplíe o la personalice.

En modo de desarrollador:

- Los archivos de vista estáticos no se almacenan en caché; se escriben en el `pub/static` cada vez que se llaman
- Las excepciones no detectadas se muestran en el explorador
- Inicio de sesión en el sistema `var/report` is verbose
- Un [exception](https://glossary.magento.com/exception) se envía al controlador de error, en lugar de registrarse
- Se produce una excepción cuando se produce una [evento](https://glossary.magento.com/event) no se puede invocar al suscriptor

Consulte [Definir el modo de operación](../cli/set-mode.md).

## Modo de producción

Ejecute Commerce en modo de producción cuando se implemente en un servidor de producción. Después de optimizar el entorno del servidor, como la base de datos y el servidor web, debe ejecutar el [herramienta de implementación de archivos de vista estática](../cli/static-view-file-deployment.md) para escribir archivos de vista estáticos en `pub/static` directorio.

Esto mejora el rendimiento al proporcionar todos los archivos estáticos necesarios en la implementación, en lugar de forzar a Commerce a localizar y copiar (materializar) dinámicamente archivos estáticos bajo demanda durante el tiempo de ejecución.

En modo de producción:

- Los archivos de vista estáticos no se materializan y las direcciones URL para ellos se componen sobre la marcha. Los archivos de vista estáticos se proporcionan desde la variable [cache](https://glossary.magento.com/cache) solo.
- Los errores se registran en el sistema de archivos y nunca se muestran al usuario.
- Puede habilitar y deshabilitar los tipos de caché _only_ usando la variable [línea de comandos](../cli/manage-cache.md#config-cli-subcommands-cache-en).
- You _cannot_ habilite o deshabilite los tipos de caché mediante el administrador.

## Modo de mantenimiento

Ejecute la aplicación Commerce en modo de mantenimiento para desconectar el sitio mientras completa las tareas de mantenimiento, actualización o configuración. En el modo de mantenimiento, el sitio redirige a los visitantes a una `Service Temporarily Unavailable` página.

Puede crear un [página de mantenimiento personalizada](../../upgrade/troubleshooting/maintenance-mode-options.md), habilite y deshabilite manualmente el modo de mantenimiento y configure el modo de mantenimiento para permitir a los visitantes de direcciones IP autorizadas ver el almacén de forma normal. Consulte [activar y desactivar el modo de mantenimiento](../../installation/tutorials/maintenance-mode.md).

Si utiliza Commerce en la infraestructura de la nube, la aplicación Commerce se ejecuta en modo de mantenimiento durante la fase de implementación. Cuando la implementación se completa correctamente, la aplicación Commerce vuelve a ejecutarse en modo de producción. Consulte [Enlaces de implementación](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-hook) en el _guía del Commerce Cloud_.
