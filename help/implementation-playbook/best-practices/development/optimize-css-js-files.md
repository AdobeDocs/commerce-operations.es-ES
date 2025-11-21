---
title: Optimización de archivos de recursos CSS y JS
description: Aprenda a combinar y minificar archivos CSS y JavaScript (JS) para proyectos de Adobe Commerce desde el administrador o desde la línea de comandos.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 5f4edc2e694c9bdbdffbe48b0e5d69907cbc0027
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Optimización de archivos de recursos

Para un sitio de Commerce más interactivo, optimice los archivos de recursos CSS y JavaScript (JS) y elimine los recursos que bloquean el procesamiento.

- **Optimizar archivos CSS y JS**: reduzca el tiempo necesario para cargar archivos CSS y JavaScript (JS) configurando Adobe Commerce para combinar, minificar y agrupar archivos independientes en un solo archivo.
- **Eliminar recursos que bloquean el procesamiento**: considere la posibilidad de ofrecer funciones JS y CSS críticas en línea y aplazar todos los estilos JS/CSS no críticos. Para obtener instrucciones, consulte [Eliminar recursos que bloquean el procesamiento](https://web.dev/render-blocking-resources/).

## Productos y versiones afectados

[Todas las versiones compatibles, 2.3 y posteriores](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Combinar o minimizar archivos CSS

El tiempo que se tarda en cargar archivos CSS y JavaScript (JS) se puede reducir combinando, minimizando y agrupando archivos independientes en un solo archivo.

>[!IMPORTANT]
>
>Adobe Commerce en la infraestructura en la nube siempre se ejecuta en el modo de producción y no es posible configurarlo de otra manera, por lo que debe utilizar el método de línea de comandos para habilitar la combinación, la minificación y el agrupamiento.

No combine ni agrupe archivos si la implementación utiliza HTTP/2. HTTP/2 descarga los archivos estáticos de forma asíncrona. Los exploradores deben descargar un archivo combinado completo antes de procesar el contenido del archivo.

### Uso de Admin

Para habilitar la combinación o minificación de CSS, ve a [!UICONTROL **Administración** > **Tiendas** > **Configuración** > **Configuración** > **Avanzado** > **Desarrollador** > **Configuración de CSS**].

### Uso de la línea de comandos

Para habilitar la combinación de CSS en Adobe Commerce en la infraestructura en la nube:

1. Ejecute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Confirme los cambios realizados en el archivo `app/etc/config.php` y vuelva a implementarlo.

Para habilitar la minificación CSS en Adobe Commerce en la infraestructura en la nube:

1. Ejecute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Confirme los cambios realizados en el archivo `app/etc/config.php` y vuelva a implementarlo.

## Minimizar archivos JS

### Uso de Admin

En la barra lateral de *Administración*, ve a **Tiendas** > **Configuración** > **Configuración** > **Avanzada** > **Desarrollador** > **Configuración de JavaScript**.

### Uso de la línea de comandos

Para habilitar la minificación de JS en Adobe Commerce en la infraestructura en la nube:

1. Ejecute este comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Confirme los cambios realizados en el archivo `app/etc/config.php` y vuelva a implementarlo.

## Combinar y empaquetar archivos JS

Puede activar la combinación o el agrupamiento en la administración de Commerce (la combinación y el agrupamiento no se pueden habilitar al mismo tiempo): [!UICONTROL **Tiendas** > **Configuración** > **Configuración** > **Avanzado** > **Desarrollador** > **Configuración de JavaScript**].

También puede habilitar el paquete integrado de Adobe Commerce (paquete básico) desde la línea de comandos:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Más información

- [Configuración de optimización del lado del cliente](../../../performance/configuration.md#client-side-optimization-settings)
- [Guía del usuario: optimizando archivos de recursos](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [Guía para desarrolladores de Frontend: combinación, minificación y rendimiento del sitio de CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Paquete de JavaScript avanzado](../../../performance/advanced-js-bundling.md)
