---
title: Optimizar archivos de recursos CSS y JS
description: Obtenga información sobre cómo combinar y minimizar archivos CSS y JavaScript (JS) para proyectos de Adobe Commerce desde Admin o desde la línea de comandos.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 052aa61e2bb59ae11b90b5401ce6426dec9c6046
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Optimización de archivos de recursos

Para un sitio de comercio más interactivo, optimice los archivos de recursos CSS y JavaScript (JS) y elimine los recursos de bloqueo de procesamiento.

- **Optimización de archivos CSS y JS**: reduzca el tiempo necesario para cargar archivos CSS y JavaScript (JS) configurando Adobe Commerce para combinar, minimizar y agrupar archivos independientes en un solo archivo.
- **Eliminación de los recursos de bloqueo de renderizado**: considere la posibilidad de ofrecer en línea funciones críticas de JS y CSS y de aplazar todos los estilos no críticos de JS/CSS. Para obtener instrucciones, consulte [Eliminación de los recursos de bloqueo de renderizado](https://web.dev/render-blocking-resources/).

## Productos y versiones afectados

[Todas las versiones compatibles, 2.3 y posteriores](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local
- Magento Open Source

## Combinar o minimizar archivos CSS

El tiempo que se tarda en cargar archivos CSS y JavaScript (JS) se puede reducir combinando, minimizando y agrupando archivos independientes en un solo archivo.

>[!IMPORTANT]
>
>Adobe Commerce en la infraestructura de la nube siempre se ejecuta en modo Producción y no es posible configurarlo de lo contrario, por lo que debe utilizar el método de la línea de comandos para habilitar la combinación, minificación y agrupación.

### Uso del administrador

Para habilitar la combinación o minificación de CSS, vaya a la [!UICONTROL **Administrador** > **Almacenes** > **Configuración** > **Configuración** > **Avanzadas** > **Desarrollador** > **Configuración de CSS**].

### Uso de la línea de comandos

Para habilitar la combinación de CSS en Adobe Commerce en la infraestructura de la nube:

1. Ejecute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Confirmar cambios en `app/etc/config.php` y vuelva a implementar.

Para habilitar la minificación de CSS en Adobe Commerce en la infraestructura de la nube:

1. Ejecute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Confirmar cambios en `app/etc/config.php` y vuelva a implementar.

## Minificar archivos JS

### Uso del administrador

En el *Administrador* barra lateral, vaya a **Almacenes** > **Configuración** > **Configuración** > **Avanzadas** > **Desarrollador** > **Configuración de JavaScript**.

### Uso de la línea de comandos

Para habilitar la minificación de JS en Adobe Commerce en la infraestructura de nube:

1. Ejecute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Confirmar cambios en `app/etc/config.php` y vuelva a implementar.

## Combinar y empaquetar archivos JS

Puede activar la combinación o agrupación en el administrador de comercio (la combinación y el agrupamiento no se pueden habilitar al mismo tiempo): [!UICONTROL **Almacenes** > **Configuración** > **Configuración** > **Avanzadas** > **Desarrollador** > **Configuración de JavaScript**].

También puede habilitar el paquete integrado de Adobe Commerce (paquete básico) desde la línea de comandos:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Información adicional

- [Configuración de optimización del lado del cliente](../../../performance/configuration.md#client-side-optimization-settings)
- [Guía del usuario: Optimización de archivos de recursos](https://docs.magento.com/user-guide/system/file-optimization.html)
- [Guía para desarrolladores de Frontend: Combinación, minificación y rendimiento del sitio de CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
