---
title: Optimización de archivos de recursos CSS y JS
description: Aprenda a combinar y minificar archivos CSS y JavaScript (JS) para proyectos de Adobe Commerce desde el administrador o desde la línea de comandos.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Optimización de archivos de recursos

Para un sitio de Commerce más interactivo, optimice los archivos de recursos CSS y JavaScript (JS) y elimine los recursos que bloquean el procesamiento.

- **Optimización de archivos CSS y JS**: reduzca el tiempo necesario para cargar archivos CSS y JavaScript (JS) configurando Adobe Commerce para combinar, minificar y agrupar archivos independientes en un solo archivo.
- **Eliminación de los recursos que bloquean el procesamiento**: considere la posibilidad de ofrecer funciones JS y CSS críticas en línea y aplazar todos los estilos JS/CSS no críticos. Para obtener instrucciones, consulte [Eliminación de los recursos que bloquean el procesamiento](https://web.dev/render-blocking-resources/).

## Productos y versiones afectados

[Todas las versiones compatibles, 2.3 y posteriores](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local
- Magento Open Source

## Combinar o minimizar archivos CSS

El tiempo que se tarda en cargar archivos CSS y JavaScript (JS) se puede reducir combinando, minimizando y agrupando archivos independientes en un solo archivo.

>[!IMPORTANT]
>
>Adobe Commerce en la infraestructura en la nube siempre se ejecuta en el modo de producción y no es posible configurarlo de otra manera, por lo que debe utilizar el método de línea de comandos para habilitar la combinación, la minificación y el agrupamiento.

### Uso de Admin

Para habilitar la combinación o minificación de CSS, vaya a [!UICONTROL **Administrador** > **Tiendas** > **Configuración** > **Configuración** > **Avanzadas** > **Desarrollador** > **Configuración de CSS**].

### Uso de la línea de comandos

Para habilitar la combinación de CSS en Adobe Commerce en la infraestructura en la nube:

1. Ejecute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Confirme los cambios en la `app/etc/config.php` y vuelva a implementarlo.

Para habilitar la minificación CSS en Adobe Commerce en la infraestructura en la nube:

1. Ejecute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Confirme los cambios en la `app/etc/config.php` y vuelva a implementarlo.

## Minimizar archivos JS

### Uso de Admin

En el *Administrador* barra lateral, vaya a **Tiendas** > **Configuración** > **Configuración** > **Avanzadas** > **Desarrollador** > **Configuración de JavaScript**.

### Uso de la línea de comandos

Para habilitar la minificación de JS en Adobe Commerce en la infraestructura en la nube:

1. Ejecute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Confirme los cambios en la `app/etc/config.php` y vuelva a implementarlo.

## Combinar y empaquetar archivos JS

Puede activar la combinación o el agrupamiento en la administración de Commerce (la combinación y el agrupamiento no se pueden activar al mismo tiempo): [!UICONTROL **Tiendas** > **Configuración** > **Configuración** > **Avanzadas** > **Desarrollador** > **Configuración de JavaScript**].

También puede habilitar el paquete integrado de Adobe Commerce (paquete básico) desde la línea de comandos:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Información adicional

- [Configuración de optimización del lado del cliente](../../../performance/configuration.md#client-side-optimization-settings)
- [Guía del usuario: Optimización de archivos de recursos](https://docs.magento.com/user-guide/system/file-optimization.html)
- [Guía para desarrolladores de Frontend: Combinación, minificación y rendimiento del sitio CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Paquete de JavaScript avanzado](../../../performance/advanced-js-bundling.md)
