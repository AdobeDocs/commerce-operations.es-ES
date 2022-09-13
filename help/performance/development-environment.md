---
title: Entorno de desarrollo Recommendations
description: Obtenga información sobre las recomendaciones de rendimiento para configurar el entorno de desarrollo de Adobe Commerce o Magento Open Source local.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Recomendaciones sobre el entorno de desarrollo

Esta página proporciona recomendaciones para entornos de desarrollo de comercio.

## Limpie las cachés en lugar de desactivarlas

Muchos desarrolladores tienden a deshabilitar todas las cachés en sus instancias de desarrollador. Solo se recomienda limpiar las cachés, sin deshabilitar todas las cachés. [!DNL Commerce] se ejecuta de forma más eficaz cuando [limpiar las cachés] en lugar de desactivarlos por completo. La mayoría de los tipos de cachés rara vez se invalidan durante el desarrollo.

Si [desactivar las cachés], solo se recomienda desactivar las cachés de página y bloque en las instancias de desarrollo. Recuerde habilitar todas las cachés durante la prueba.

## Comandos que se deben evitar en el modo de desarrollo

En el modo de desarrollo, no ejecute comandos para la compilación, generación de código e implementación de contenido estático. Estos comandos se crearon para su uso únicamente en modo de producción.

**No ejecutar** comandos de producción en modo de desarrollo:

* `setup:di:compile` genera clases generadas automáticamente y cachés de configuración optimizadas.

   ```bash
   bin/magento setup:di:compile
   ```

   En el modo de desarrollo, el Magento realiza la generación a petición; no es necesario que lo ejecute. Si ha modificado una firma de una clase y necesita volver a generar su `factories/proxies/interceptors`, elimine esas clases o _generado_ carpeta.

* `setup:static-content:deploy` implementa contenido estático para una tienda.

   ```bash
   bin/magento setup:static-content:deploy
   ```

   En el modo de desarrollo, el Magento lo realiza bajo demanda; no es necesario que lo ejecute.

## Tiempo normal de carga de página en una máquina virtual

Si se desarrolla en una VM y la carga de una página de Magento tarda más de 2 segundos, revise la configuración de su entorno.

<!-- Link definitions -->

[limpiar las cachés]: ../configuration/cli/manage-cache.md#clean-and-flush-cache-types
[desactivar las cachés]: ../configuration/cli/manage-cache.md#enable-or-disable-cache-types
