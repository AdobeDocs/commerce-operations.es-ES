---
title: Recomendaciones del entorno de desarrollo
description: Obtenga información acerca de las recomendaciones de entornos de desarrollo en Adobe Commerce. Descubra estrategias de optimización y directrices de implementación.
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Recomendaciones del entorno de desarrollo

Esta página proporciona recomendaciones para entornos de desarrollo de Commerce.

## Limpie las cachés en lugar de deshabilitar

Muchos desarrolladores tienden a deshabilitar todas las cachés en sus instancias de desarrollador. Solo recomendamos limpiar las cachés, sin deshabilitar todas las cachés. [!DNL Commerce] se ejecuta de manera más eficiente cuando [limpia las cachés](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) en lugar de deshabilitarlas por completo. La mayoría de los tipos de cachés rara vez se invalidan durante el desarrollo.

Si [deshabilita las cachés](../configuration/cli/manage-cache.md#enable-or-disable-cache-types), recomendamos que solo deshabilite las cachés de página y bloque en las instancias de desarrollo. Recuerde habilitar todas las cachés durante la prueba.

## Comandos que se deben evitar en el modo de desarrollo

En el modo de desarrollo, no ejecute comandos para compilación, generación de código e implementación de contenido estático. Estos comandos se crearon únicamente para utilizarlos en el modo de producción.

**No ejecutar** comandos de producción en modo de desarrollo:

* `setup:di:compile` genera clases generadas automáticamente y cachés de configuración optimizadas.

  ```shell
  bin/magento setup:di:compile
  ```

  En el modo de desarrollo, Magento realiza la generación bajo demanda; no es necesario ejecutarla. Si ha modificado una firma de una clase y necesita volver a generar su `factories/proxies/interceptors` generado automáticamente, quite esas clases o la carpeta _generated_.

* `setup:static-content:deploy` implementa contenido estático para un almacén.

  ```shell
  bin/magento setup:static-content:deploy
  ```

  En el modo de desarrollo, Magento lo realiza bajo demanda; no es necesario ejecutarlo.

## Tiempo normal de carga de la página en una máquina virtual

Si desarrolla en una VM y tarda más de 2 segundos en cargar una página de Magento, revise la configuración de su entorno.
