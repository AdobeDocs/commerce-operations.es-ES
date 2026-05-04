---
title: Optimización de archivos de recursos CSS y JS
description: Aprenda a combinar y minificar archivos CSS y JavaScript (JS) para proyectos de Adobe Commerce desde el administrador o desde la línea de comandos.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Optimización de archivos de recursos

Para un sitio de Commerce más interactivo, optimice los archivos de recursos CSS y JavaScript (JS) y elimine los recursos que bloquean el procesamiento.

- **Optimizar archivos CSS y JS**: Reduzca el tiempo necesario para cargar archivos CSS y JavaScript (JS) configurando Adobe Commerce para minificar y agrupar archivos.
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

Para habilitar la combinación o minificación de CSS, vaya a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL CSS Settings]**.

### Uso de la línea de comandos

Para habilitar la combinación de CSS en Adobe Commerce en la infraestructura en la nube:

1. Ejecute este comando localmente:

   ```shell
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Confirme los cambios realizados en el archivo `app/etc/config.php` y vuelva a implementarlo.

Para habilitar la minificación CSS en Adobe Commerce en la infraestructura en la nube:

1. Ejecute este comando localmente:

   ```shell
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Confirme los cambios realizados en el archivo `app/etc/config.php` y vuelva a implementarlo.

## Minimizar archivos JS

### Usando [!UICONTROL Admin]

En la barra lateral [!UICONTROL Admin], vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**.

### Uso de la línea de comandos

Para habilitar la minificación de JS en Adobe Commerce en la infraestructura en la nube:

1. Ejecute este comando localmente:

   ```shell
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Confirme los cambios realizados en el archivo `app/etc/config.php` y vuelva a implementarlo.

## Paquete de archivos JS

Puede habilitar el agrupamiento en Commerce [!UICONTROL Admin]: **[!UICONTROL Stores]** > ***[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**.

>[!NOTE]
>
>La combinación y el agrupamiento no se pueden habilitar al mismo tiempo.

También puede habilitar el paquete integrado de Adobe Commerce (paquete básico) desde la línea de comandos:

```shell
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Combinar archivos JS (no recomendado) {#merge-js-files}

>[!WARNING]
>
>No se recomienda habilitar **[!UICONTROL Merge JavaScript Files]**. Esta configuración se diseñó únicamente para JavaScript cargados sincrónicamente en la sección **[!UICONTROL HEAD]** de la página y puede hacer que el agrupamiento y la lógica [!DNL RequireJS] funcionen incorrectamente. Se mantiene solo para la compatibilidad con versiones anteriores y no proporciona ninguna ventaja de rendimiento cuando HTTP/2 está habilitado.
>
>Si tiene **[!UICONTROL Merge JavaScript Files]** habilitado y tiene problemas, intente deshabilitarlo antes de aplicar los parches. Consulte [ACSD-67908](../../../tools/quality-patches-tool/patches-available-in-qpt/v1-1-73/acsd-67908.md) si no puede deshabilitar la combinación.

## Más información

- [Configuración de optimización del lado del cliente](../../../performance/configuration.md#client-side-optimization-settings)
- [Sugerencias de agrupación](../../../performance/configuration.md#bundling-tips) en *Prácticas recomendadas de configuración*—herramientas de agrupación de terceros, HTTP/2 e instrucciones sobre la combinación de JS y CSS obsoletas
- [Guía del usuario: Optimización de archivos de recursos](https://experienceleague.adobe.com/es/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [Guía para desarrolladores de Frontend: Combinación, minificación y rendimiento del sitio CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Paquete de JavaScript avanzado](../../../performance/advanced-js-bundling.md)
