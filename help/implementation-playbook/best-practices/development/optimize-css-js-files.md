---
title: Optimización de archivos de recursos CSS y JS
description: Aprenda a combinar y minificar archivos CSS y JavaScript (JS) para proyectos de Adobe Commerce desde el administrador o desde la línea de comandos.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Optimice los archivos de recursos

Para un sitio de comercio más adaptable, optimice los archivos de recursos CSS y JavaScript (JS) y elimine los recursos de bloqueo de procesamiento.

- **Optimice los archivos** CSS y JS: reduzca el tiempo necesario para cargar archivos CSS y JavaScript (JS) configurando Adobe Systems Commerce para fusionar, minimizar y paquete archivos separados en un solo archivo.
- **Elimine los recursos** que bloquean el procesamiento: considere la posibilidad de ofrecer esencial funciones JS y CSS en línea y aplazar todos los estilos JS/CSS que no sean esencial. Para obtener instrucciones, consulte [Eliminación de recursos que bloquean el](https://web.dev/render-blocking-resources/) procesamiento.

## Productos y versiones afectados

[Todas las versiones compatibles, 2.3 y posteriores](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Combinar o minimizar archivos CSS

El tiempo que se tarda en cargar archivos CSS y JavaScript (JS) se puede reducir combinando, minimizando y agrupando archivos independientes en un solo archivo.

>[!IMPORTANT]
>
>Adobe Systems Commerce en infraestructura en la nube siempre se ejecuta en modo Producción y no es posible configurarlo de otra manera, por lo tanto, debe usar el método de línea de comandos para habilitar la combinación, minimización y agrupación.

No combine ni paquete archivos si el implementación utiliza HTTP/2. HTTP/2 descarga archivos estáticos de forma asíncrona. Los navegadores deben descargar un archivo combinado completo antes de procesar su contenido.

### Uso de Administración

Para habilitar la fusión o minimización de CSS, vaya a Admin [!UICONTROL **** > **Stores** > **Setting** > **Configuration** > **Avanzadas** > **Developer** > **CSS Configuración**].

### Uso de la línea de comandos

Para habilitar la fusión de CSS en Adobe Systems Commerce en infraestructura en la nube:

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

1. Confirme los cambios en el `app/etc/config.php` archivo y vuelva a implementarlo.

## Minifique los archivos JS

### Uso de Administración

En la *barra lateral del administrador*, ve a **Tiendas** > **Configuración >** Configuración **>****Avanzadas** > **>** de desarrollador **JavaScript Configuración**.

### Uso de la línea de comandos

Para habilitar la minimización de JS en Adobe Systems Commerce en infraestructura en la nube:

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
- [Guía del usuario: Optimización de archivos de recursos](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [Guía para desarrolladores frontend: fusión, minimización y rendimiento del sitio de CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Avanzadas JavaScript paquetes](../../../performance/advanced-js-bundling.md)
