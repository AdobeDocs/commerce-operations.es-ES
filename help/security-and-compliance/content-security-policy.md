---
title: Información general sobre la política de seguridad de contenido
description: Obtenga información sobre cómo mejorar la postura de seguridad de la tienda de Adobe Commerce o Magento Open Source mediante una política de seguridad de contenido.
source-git-commit: 1a608e8a5986026d5a187dc8cbd358fed2db5d9e
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# Información general sobre la política de seguridad de contenido

Una Política de seguridad de contenido (CSP) puede proporcionar capas adicionales de defensa para las instalaciones de Adobe Commerce y Magento Open Source, ya que ayuda a detectar y mitigar los scripts en sitios múltiples (XSS) y los ataques de inyección de datos relacionados. Este vector de ataque común funciona inyectando contenido malicioso que afirma falsamente originarse en el sitio web. Una vez cargado y ejecutado el contenido malicioso, puede iniciar la transferencia no autorizada de datos.

CSP proporciona un conjunto estandarizado de directivas que indica al explorador en qué recursos de contenido se puede confiar y cuáles se deben bloquear. Mediante políticas cuidadosamente definidas, CSP puede restringir el contenido del explorador para permitir que solo aparezcan los recursos de la lista blanca.

## Configuración

Para evitar interferir con las operaciones del sitio, el CSP se puede implementar por fases. CSP tiene dos modos básicos de funcionamiento: `report-only mode` y `restrict mode`. La versión de Adobe Commerce 2.3.5 marca la primera fase de nuestra implementación y hace que CSP esté disponible en `report-only mode` de forma predeterminada. En una versión futura, `restrict mode` está habilitado de forma predeterminada para protección adicional predeterminada.

**Modo de solo informe**: Se indica al explorador que informe de infracciones de directivas, pero no que las aplique. Cada vez que un recurso solicitado infringe la CSP, el explorador registra los errores resultantes en la consola. El registro de la consola se puede utilizar para investigar la causa de cada infracción.

Es importante revisar todos los errores de CSP a medida que ocurran y refinar las políticas hasta que todos los recursos necesarios estén en la lista blanca. Es seguro cambiar a `restrict mode` cuando no se produzcan más errores. De lo contrario, un CSP mal configurado puede hacer que el explorador muestre una página en blanco con numerosos errores de consola. Un CSP configurado correctamente permite entregar contenido en la lista blanca sin que se perciba ningún impacto en el rendimiento.

**Restringir modo**: Se indica al explorador que aplique todas las políticas de contenido y limite la publicación a los recursos de la lista blanca. Dado que la CSP está configurada desde el servidor, no desde el administrador, la mayoría de los comerciantes necesitan la asistencia de un integrador de sistemas o desarrollador para configurarla correctamente. Consulte [Políticas de seguridad del contenido](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) en el _Extensiones de Commerce PHP_ guía para desarrolladores.

## Informes

De forma predeterminada, CSP envía errores a la consola del explorador, pero se puede configurar para recopilar registros de error mediante solicitud HTTP. Además, existen varios servicios de terceros que puede utilizar para supervisar, recopilar y notificar infracciones de CSP.

[URI de informe](https://report-uri.io/) es un servicio que supervisa las violaciones de CSP y muestra los resultados en un panel. Tanto los comerciantes como los desarrolladores pueden utilizar el servicio para recibir informes cada vez que se produzcan violaciones de CSP.
