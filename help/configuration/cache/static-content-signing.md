---
title: Firma de contenido estático e invalidación de caché del explorador
description: Descubra cómo funciona la firma de contenido estático en Adobe Commerce para invalidar la caché del explorador para los recursos estáticos. Descubra cómo habilitar y configurar esta función.
feature: Configuration, Cache, SCD
exl-id: b54ceea2-b3a1-4dbb-ba87-743f2af0d2fb
badgePaas: label="PaaS" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a Adobe Commerce en proyectos en la nube y locales."
autotag-review: '2026-06-22T21:48:08.334Z'
TQID: 'https://experienceleague.adobe.com/vagWBVnjIS7tjnwVE5Dk56VDmPtbPgjsNVLBHSlOc-s'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 372
ht-degree: 0%

---

# Firma de contenido estático e invalidación de la caché del explorador

Para mejorar el rendimiento, Commerce establece los encabezados `Expires` de los recursos estáticos, como imágenes, JavaScript y archivos CSS.
Al establecer el encabezado `Expires` en un recurso estático, se indica al explorador que almacene en caché el recurso en esa dirección URL y proporcione la versión en caché hasta que caduque.
Esta es una [práctica recomendada](https://developer.yahoo.com/performance/rules.html#expires=) común para almacenar en caché recursos estáticos.

Cuando el explorador almacena en caché un recurso estático y ese recurso cambia en el servidor, debe borrar la caché del explorador para que pueda descargar la nueva versión.
La eliminación manual de la caché del explorador funciona si es administrador de un sitio web, pero no es una solicitud adecuada para realizar a los usuarios cuando desea que descarguen nuevas versiones de un recurso estático.

## Firma de contenido estático

La firma de contenido estático es una función de Commerce que le permite invalidar la memoria caché del explorador para los recursos estáticos.
Commerce lo consigue añadiendo una versión de implementación a la dirección URL de los archivos estáticos.

El siguiente es un ejemplo de una dirección URL firmada con una versión:

```text
http://magento2.com/pub/static/version1475604434/frontend/Magento/luma/en_US/images/logo.svg
```

Cuando ejecuta el comando [`setup:static-content:deploy`](../cli/static-view-file-deployment.md) para implementar contenido estático, Commerce cambia automáticamente la versión de implementación.
Esto cambia la dirección URL de los archivos estáticos y fuerza al explorador a cargar la nueva versión de los archivos.

Commerce habilita esta función de forma predeterminada y Adobe recomienda mantenerla habilitada para evitar problemas relacionados con los exploradores que usan recursos estáticos antiguos.

La configuración para la firma de contenido estático se encuentra en [**[!UICONTROL Stores]**> Configuración > Configuración >**[!UICONTROL Advanced]**>**[!UICONTROL Developer]**>**[!UICONTROL Static Files Settings]**](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/developer-tools#static-file-signatures).

- **Solo local**: esta configuración está disponible si el sitio es **no** en [modo de producción](../bootstrap/application-modes.md#production-mode).
- **Cloud**: esta configuración está oculta porque el modo de producción se aplica estrictamente; por lo tanto, debe utilizar la línea de comandos como se muestra a continuación.

![Configuración de archivos estáticos](../../assets/configuration/static-files-settings.png)

Determine el estado:

```shell
bin/magento config:show dev/static/sign
```

Habilitar o deshabilitar la firma de contenido estático:

```shell
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
