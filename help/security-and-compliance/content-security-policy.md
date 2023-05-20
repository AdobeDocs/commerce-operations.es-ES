---
title: Información general sobre política de seguridad de contenido
description: Aprenda a mejorar la postura de seguridad de su tienda de Adobe Commerce o Magento Open Source mediante una política de seguridad de contenido.
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# Información general sobre política de seguridad de contenido

Una política de seguridad de contenido (CSP) puede proporcionar capas adicionales de defensa para las instalaciones de Adobe Commerce y Magento Open Source al ayudar a detectar y mitigar los ataques de inyección de datos relacionados y los scripts entre sitios (XSS). Este vector de ataque común funciona mediante la inyección de contenido malicioso que afirma falsamente originarse desde el sitio web. Una vez cargado y ejecutado el contenido malicioso, puede iniciar la transferencia no autorizada de datos.

CSP proporciona un conjunto estandarizado de directivas que indican al explorador en qué recursos de contenido se puede confiar y cuáles se deben bloquear. Mediante directivas cuidadosamente definidas, el CSP puede restringir el contenido del explorador para permitir que solo aparezcan los recursos en la lista blanca.

## Configuración

Para evitar interferir con las operaciones del sitio, el CSP se puede implementar por fases. CSP tiene dos modos básicos de funcionamiento: `report-only mode` y `restrict mode`. La versión 2.3.5 de Adobe Commerce marca la primera fase de nuestra implementación y hace que el CSP esté disponible en `report-only mode` de forma predeterminada. En una versión futura, `restrict mode` está habilitado de forma predeterminada para obtener una protección adicional lista para usar.

**Modo de solo informe**: Se indica al explorador que informe de las violaciones de directivas, pero no que las aplique. Cada vez que un recurso solicitado infringe el CSP, el explorador registra los errores resultantes en la consola. El registro de la consola se puede utilizar para investigar la causa de cada infracción.

Es importante revisar todos los errores de CSP a medida que se producen y refinar las políticas hasta que se incluyan todos los recursos necesarios en la lista blanca. Es seguro cambiar a `restrict mode` cuando no se producen más errores. De lo contrario, un CSP mal configurado podría hacer que el explorador muestre una página en blanco con numerosos errores de consola. Un CSP configurado correctamente permite entregar el contenido de la lista blanca sin ningún impacto aparente en el rendimiento.

**Restringir modo**: Se indica al explorador que aplique todas las políticas de contenido y limite la publicación a los recursos de la lista blanca. Dado que el CSP se configura desde el servidor, en lugar de desde el administrador, la mayoría de los comerciantes necesitan la asistencia de un integrador de sistemas o desarrollador para configurarlo correctamente. Consulte [Políticas de seguridad de contenido](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) en el _Extensiones PHP de Commerce_ guía para desarrolladores.

## Informes

De forma predeterminada, el CSP envía errores a la consola del explorador, pero se puede configurar para que recopile registros de errores mediante una solicitud HTTP. Además, hay varios servicios de terceros que puede utilizar para monitorizar, recopilar e informar de violaciones de CSP.

[URI de informe](https://report-uri.io/) es un servicio que supervisa las infracciones de CSP y muestra los resultados en un panel. Tanto los comerciantes como los desarrolladores pueden utilizar el servicio para recibir informes cada vez que se produzcan infracciones de CSP.
