---
title: Caché de contenido estático
description: Obtenga información sobre la firma de contenido estático y cómo habilitar o deshabilitar la función.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Caché de contenido estático

Para mejorar el rendimiento, Commerce configura la variable `Expires` encabezados para recursos estáticos, como imágenes, JavaScript y archivos CSS.
Configuración de la variable `Expires` en un recurso estático, indica al explorador que almacene en caché el recurso en esa dirección URL y que sirva la versión en caché hasta que caduque.
Esto es común [prácticas recomendadas](https://developer.yahoo.com/performance/rules.html#expires=) para almacenar en caché los recursos estáticos.

Cuando el explorador almacena en caché un recurso estático y ese recurso cambia en el servidor, debe borrar la caché del explorador para que pueda descargar la nueva versión.
La eliminación manual de la caché del explorador funciona si es un [sitio web](https://glossary.magento.com/website) administrador, pero esta no es una solicitud adecuada para hacer de los usuarios cuando desea que descarguen nuevas versiones de un recurso estático.

## Firma de contenido estático

[Contenido estático](https://glossary.magento.com/static-content) la firma es una función de comercio que le permite invalidar la caché del explorador para los recursos estáticos.
Commerce lo consigue añadiendo una versión de implementación a la dirección URL de [archivos estáticos](https://glossary.magento.com/static-files).

A continuación se muestra un ejemplo de una URL firmada con una versión:

```terminal
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Al ejecutar el comando [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) para implementar contenido estático, Commerce cambia automáticamente la versión de implementación.
Esto cambia la dirección URL de los archivos estáticos y obliga al explorador a cargar la nueva versión de los archivos.

Commerce habilita esta función de forma predeterminada y Adobe recomienda mantener esta función habilitada para evitar problemas relacionados con exploradores que ofrezcan recursos estáticos antiguos.

Puede encontrar la configuración para esta función en [**[!UICONTROL Stores]**> Configuración > Configuración >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://docs.magento.com/user-guide/system/static-file-signature.html).

![Configuración de archivos estáticos](../../assets/configuration/static-files-settings.png)

Determine el estado:

```bash
bin/magento config:show dev/static/sign
```

Habilite o deshabilite la firma de contenido estático:

```bash
bin/magento config:set dev/static/sign <value>
```

Donde `<value>` es 1 (habilitado) o 0 (deshabilitado).

## Firmas de versión

Commerce anexa la firma de la versión como un componente de ruta directamente después de la URL base de los archivos de vista estática para preservar la integridad de las direcciones URL relativas en los recursos estáticos.
Esto también obliga al explorador a resolver una dirección URL relativa al origen firmado correcto, mientras que mantiene su contenido independiente de la presencia o ausencia del valor de firma.

Cuando un explorador solicita un origen firmado desde el servidor, el servidor utiliza las reescrituras de URL para eliminar el componente de firma de la dirección URL.

## Uso durante implementaciones

Después de actualizar o modificar los recursos estáticos, debe ejecutar el `setup:static-content:deploy` para implementar la versión y actualizar el contenido estático, lo que obliga al explorador a cargar los recursos actualizados.

Si implementa código en un servidor independiente y lo mueve a producción utilizando un repositorio de código para reducir el tiempo de inactividad, también debe agregar el archivo `pub/static/deployed_version.txt` al repositorio.
Este archivo contiene la nueva versión para el contenido estático implementado.
