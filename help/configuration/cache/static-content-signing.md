---
title: Caché de contenido estático
description: Obtenga información sobre la firma de contenido estático y cómo habilitar o deshabilitar la función.
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Caché de contenido estático

Para mejorar el rendimiento, Commerce establece los encabezados `Expires` de los recursos estáticos, como imágenes, JavaScript y archivos CSS.
Al establecer el encabezado `Expires` en un recurso estático, se indica al explorador que almacene en caché el recurso en esa dirección URL y proporcione la versión en caché hasta que caduque.
Esta es una [práctica recomendada](https://developer.yahoo.com/performance/rules.html#expires=) común para almacenar en caché recursos estáticos.

Cuando el explorador almacena en caché un recurso estático y ese recurso cambia en el servidor, debe borrar la caché del explorador para que pueda descargar la nueva versión.
La eliminación manual de la caché del explorador funciona si es administrador de un sitio web, pero no es una solicitud adecuada para realizar a los usuarios cuando desea que descarguen nuevas versiones de un recurso estático.

## Firma de contenido estático

La firma de contenido estático es una función de Commerce que le permite invalidar la memoria caché del explorador para los recursos estáticos.
Commerce lo consigue añadiendo una versión de implementación a la dirección URL de los archivos estáticos.

El siguiente es un ejemplo de una dirección URL firmada con una versión:

```
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Cuando ejecuta el comando [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) para implementar contenido estático, Commerce cambia automáticamente la versión de implementación.
Esto cambia la dirección URL de los archivos estáticos y fuerza al explorador a cargar la nueva versión de los archivos.

Commerce habilita esta función de forma predeterminada y Adobe recomienda mantenerla habilitada para evitar problemas relacionados con los exploradores que sirven recursos estáticos antiguos.

La configuración para la firma de contenido estático se encuentra en [**[!UICONTROL Stores]**> Configuración > Configuración >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

- **Solo local**: esta configuración está disponible si el sitio es **no** en [modo de producción](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html#production-mode).
- **Cloud**: esta configuración está oculta porque el modo de producción se aplica estrictamente; por lo tanto, debe utilizar la línea de comandos como se muestra a continuación.

![Configuración de archivos estáticos](../../assets/configuration/static-files-settings.png)

Determine el estado:

```bash
bin/magento config:show dev/static/sign
```

Habilitar o deshabilitar la firma de contenido estático:

```bash
bin/magento config:set dev/static/sign <value>
```

Donde `<value>` es 1 (habilitado) o 0 (deshabilitado).

## Firmas de versión

Commerce anexa la firma de versión como un componente de ruta de acceso directamente después de la dirección URL base de los archivos de vista estática para preservar la integridad de las direcciones URL relativas en los recursos estáticos.
Esto también obliga al explorador a resolver una dirección URL relativa al origen firmado correcto, manteniendo al mismo tiempo su contenido independiente de la presencia/ausencia del valor de firma.

Cuando un explorador solicita un origen firmado del servidor, este utiliza las reescrituras de URL para eliminar el componente de firma de la URL.

## Uso durante las implementaciones

Después de actualizar o modificar los recursos estáticos, debe ejecutar el comando `setup:static-content:deploy` para implementar la versión y actualizar el contenido estático, lo que obliga al explorador a cargar los recursos actualizados.

Si implementa el código en un servidor independiente y lo mueve a producción mediante un repositorio de código para reducir el tiempo de inactividad, también debe agregar el archivo `pub/static/deployed_version.txt` al repositorio.
Este archivo contiene la nueva versión del contenido estático implementado.
