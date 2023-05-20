---
title: Caché de contenido estático
description: Obtenga información sobre la firma de contenido estático y cómo habilitar o deshabilitar la función.
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Caché de contenido estático

Para mejorar el rendimiento, Commerce establece el `Expires` encabezados para recursos estáticos, como imágenes, JavaScript y archivos CSS.
Configuración de la `Expires` en un recurso estático indica al explorador que almacene en caché el recurso en esa dirección URL y proporcione la versión en caché hasta que caduque.
Esto es común [práctica recomendada](https://developer.yahoo.com/performance/rules.html#expires=) para almacenar en caché recursos estáticos.

Cuando el explorador almacena en caché un recurso estático y ese recurso cambia en el servidor, debe borrar la caché del explorador para que pueda descargar la nueva versión.
La eliminación manual de la caché del explorador funciona si es administrador de un sitio web, pero no es una solicitud adecuada para realizar a los usuarios cuando desea que descarguen nuevas versiones de un recurso estático.

## Firma de contenido estático

La firma de contenido estático es una función de Commerce que le permite invalidar la caché del explorador para los recursos estáticos.
Commerce lo consigue añadiendo una versión de implementación a la URL de los archivos estáticos.

El siguiente es un ejemplo de una dirección URL firmada con una versión:

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Cuando ejecute el comando [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) para implementar contenido estático, Commerce cambia automáticamente la versión de implementación.
Esto cambia la dirección URL de los archivos estáticos y fuerza al explorador a cargar la nueva versión de los archivos.

Commerce habilita esta función de forma predeterminada y Adobe recomienda mantenerla habilitada para evitar problemas relacionados con los exploradores que usan recursos estáticos antiguos.

Puede encontrar la configuración de esta función en [**[!UICONTROL Stores]**> Configuración > Configuración >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

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

Commerce anexa la firma de versión como un componente de ruta directamente después de la URL base de los archivos de vista estática para preservar la integridad de las URL relativas en los recursos estáticos.
Esto también obliga al explorador a resolver una dirección URL relativa al origen firmado correcto, manteniendo al mismo tiempo su contenido independiente de la presencia/ausencia del valor de firma.

Cuando un explorador solicita un origen firmado del servidor, este utiliza las reescrituras de URL para eliminar el componente de firma de la URL.

## Uso durante las implementaciones

Después de actualizar o modificar los recursos estáticos, debe ejecutar el `setup:static-content:deploy` para implementar la versión y actualizar el contenido estático, lo que obliga al explorador a cargar los recursos actualizados.

Si implementa el código en un servidor independiente y lo mueve a producción mediante un repositorio de código para reducir el tiempo de inactividad, también debe agregar el archivo `pub/static/deployed_version.txt` al repositorio.
Este archivo contiene la nueva versión del contenido estático implementado.
