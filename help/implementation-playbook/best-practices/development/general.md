---
title: Prácticas recomendadas generales de desarrollo
description: Obtenga información sobre las prácticas recomendadas generales para el desarrollo de proyectos de Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: 35de9849-2d19-4bb6-b920-9ce3838bc8bc
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# Prácticas recomendadas generales de desarrollo para Adobe Commerce

En este tema se describe la línea de base para un proceso de desarrollo de Adobe Commerce en buen estado. Describe procesos fundamentales, principios de codificación y principios de diseño de aplicaciones para guiar a los desarrolladores.

>[!NOTE]
>
>Los arquitectos técnicos de Adobe utilizan estas prácticas recomendadas como referencia durante las contrataciones que implican desarrollo.

Estas prácticas recomendadas se han desarrollado sobre la base de años de experiencia en el desarrollo y la entrega de proyectos de Commerce. El Adobe recomienda que las iniciativas técnicas sigan estas prácticas recomendadas y que mejore los procesos y el código existentes para alinearse con ellos.

## Convenciones de texto

Las palabras clave &quot;MUST&quot;, &quot;MUST NOT&quot;, &quot;REQUIRED&quot;, &quot;SHALL&quot;, &quot;SHALL NOT&quot;, &quot;SHOULD&quot;, &quot;SHOULD NOT&quot;, &quot;RECOMMENDED&quot;, &quot;MAY&quot; y &quot;OPTIONAL&quot; en este tema se deben interpretar como se describe en [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119).

## Proceso

1. Se debe acordar una metodología de proyecto definida antes de comenzar las actividades del proyecto. PUEDE ser Scrum, Waterfall o cualquier otra metodología o combinación de metodologías, siempre y cuando se defina.
1. El desarrollo NO DEBE comenzar hasta que el equipo de desarrollo disponga de una estrategia de ramificación para el sistema de control de versiones.
1. El desarrollo NO DEBE comenzar hasta después de la firma de especificaciones técnicas, la firma de historias de usuarios y casos de uso y la firma de casos de prueba están disponibles para el equipo de desarrollo.
1. El desarrollo NO DEBE comenzar hasta que haya al menos un entorno de desarrollo y control de calidad disponible.
1. Los requisitos específicos del proyecto que son obligatorios para que se inicie el desarrollo PUEDEN documentarse en una _definición de Listo_.
1. La firma DEBE realizarla un representante del cliente autorizado para firmar los entregables del proyecto.
1. En las metodologías de proyecto Agile, PUEDEN seguir requisitos adicionales a la firma. Estos requisitos DEBEN tratarse como nuevos requisitos y DEBEN recopilarse, diseñarse y planificarse en consecuencia.
1. El desarrollador DEBE probar funcionalmente todo el desarrollo antes del envío.
1. Todo el desarrollo DEBE pasar pruebas automatizadas antes de enviarse para la revisión del código. Esto PUEDE configurarse como un proceso automatizado después de la creación de la solicitud de extracción.
1. Todo desarrollo DEBE pasar la revisión manual del código por parte de un arquitecto técnico o desarrollador principal antes de enviarlo para garantizar la calidad.
1. Todo desarrollo DEBE pasar la garantía de calidad antes de la entrega al cliente.
1. Los requisitos específicos del proyecto que son obligatorios para la entrega PUEDEN documentarse en una &quot;Definición de Listo&quot;.

## Entorno

1. Todos los desarrolladores DEBEN utilizar el mismo IDE. PhpStorm es el IDE recomendado para el desarrollo de Adobe Commerce.
1. Todos los desarrolladores DEBEN desarrollar y probar utilizando la misma pila tecnológica que se utiliza en los (futuros) servidores de producción. Las versiones del software de esta pila tecnológica DEBEN coincidir con la versión principal y secundaria del software instalado en los servidores de producción. Consulte [requisitos del sistema](../../../installation/system-requirements.md) para obtener detalles sobre la pila de tecnología típica para Adobe Commerce.
1. El administrador del sistema o el arquitecto técnico PUEDEN proporcionar al equipo un entorno de desarrollo local mantenido de forma centralizada para garantizar y promover entornos locales iguales y actualizados.
1. Los desarrolladores y los ingenieros de control de calidad DEBEN tener acceso a la línea de comandos, la base de datos y los archivos de registro del entorno de control de calidad. Esto PUEDE requerir una conexión VPN.

## Estándares de codificación

1. Todo el código DEBE seguir las convenciones en arquitectura, metodología y estándares de codificación. La creatividad se desea en la función, no en la forma.
1. Todo el código DEBE estar en línea con [Adobe Commerce Architecture Guide](https://developer.adobe.com/commerce/php/architecture/){target="_blank}.
1. Todo el código DEBE cumplir con los [Estándares de codificación de Adobe Commerce](https://developer.adobe.com/commerce/php/coding-standards/).
1. Todo el código DEBE adherirse a las [Directrices técnicas de Adobe Commerce](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).
1. Todo el código DEBE implementar las [Prácticas recomendadas de Adobe Commerce](../phases.md), si corresponde.
1. Todo el código DEBE cumplir con los estándares [FIG (PHP-Framework Interoperability Group)](https://www.php-fig.org/).
1. Siempre que sea posible, se RECOMIENDA tener en cuenta [Adobe Commerce Technical Visions](https://developer.adobe.com/commerce/php/architecture/technical-vision/).
1. Todas las integraciones con sistemas externos DEBEN tener pruebas de integración que validen el proceso empresarial.
1. Todos los módulos DEBEN tener cobertura de prueba. El equipo de desarrollo, en colaboración con el arquitecto técnico o el desarrollador principal, DEBE determinar qué pruebas deben realizarse exactamente. Esta determinación DEBE basarse en medidas cualitativas y no en medidas cuantitativas; un porcentaje elevado de cobertura de código no es un indicador de éxito, ni implica una calidad de código elevada. En su lugar, determine el riesgo de no cubrir una parte del código mediante la evaluación de la probabilidad y la gravedad de las regresiones en esa parte del programa.

## Versiones

Las versiones de módulo DEBEN cumplir con el estándar [Semantic Versioning 2.0.0](https://semver.org/).
Las dependencias en el código base de Adobe Commerce DEBEN seguir las [directrices de dependencias de versión de módulo](https://developer.adobe.com/commerce/php/development/versioning/dependencies/).

## CONTROL DE REVISIÓN

Las confirmaciones DEBEN ir acompañadas de mensajes de confirmación significativos.

## Seguridad

1. [NO se DEBEN usar funciones no seguras](https://developer.adobe.com/commerce/php/development/security/non-secure-functions/).
1. [DEBEN aplicarse estrategias de prevención de XSS](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/).
1. [DEBEN aplicarse políticas de seguridad de contenido](https://developer.adobe.com/commerce/php/development/security/content-security-policies/).
1. Las nuevas instancias de Adobe Commerce DEBEN entregarse en la última versión de seguridad de una versión que aún no haya alcanzado la fecha de &quot;Fin de las correcciones de seguridad&quot;. Consulte [Política de ciclo de vida del software de Adobe Commerce](../../../release/lifecycle-policy.md).
