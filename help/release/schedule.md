---
title: Programación de lanzamiento del parche
description: Descubra cuándo planea Adobe anunciar el lanzamiento de nuevos parches y correcciones de seguridad para Adobe Commerce.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: f4601034e3e988b3058946b263ec5e8da41fce16
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Programación de lanzamiento del parche

Adobe se esfuerza continuamente por encontrar el equilibrio adecuado entre hacer que las actualizaciones de los productos sean sencillas y predecibles, y al mismo tiempo ofrecer mejoras más rápidas a los usuarios que las adoptaron por primera vez (consulte [directiva de versiones](versioning-policy.md)).

El propósito de esta programación es proporcionar fechas para cuándo Adobe planea anunciar el lanzamiento de [parches](versioning-policy.md#patch-release) para cada línea de lanzamiento compatible de la aplicación principal de Adobe Commerce PHP. Las versiones de parches son oportunidades para actualizar la base de código principal a fin de mantener la seguridad, la fiabilidad y el rendimiento de su plataforma.

>[!NOTE]
>
>Para obtener más información sobre las nuevas características, la infraestructura en la nube y las versiones de extensibilidad, consulte la [documentación de la versión de Adobe Commerce Services](https://experienceleague.adobe.com/es/docs/commerce/user-guides/release-information/release-notes-all).

Además de los parches de calidad, seguridad y beta programados que se enumeran en esta página, Adobe proporciona acceso a [parches individuales](versioning-policy.md#individual-patch) mediante la [Herramienta de parches de calidad](../tools/quality-patches-tool/usage.md). La herramienta le permite aplicar, revertir y ver información general sobre todos los parches individuales que están disponibles para la versión instalada de Adobe Commerce.

A partir de enero de 2026, Adobe Commerce pasará a una programación mensual de versiones de parches con la siguiente estrategia:

- **Correcciones de seguridad aisladas**: [correcciones de seguridad](versioning-policy.md#isolated-patch) individuales y no acumulativas se pueden publicar mensualmente e incluir correcciones de seguridad para todas las [líneas de versión admitidas](lifecycle-policy.md) (incluye soporte regular y extendido).

- **Parches de seguridad**: como mínimo, [los parches de seguridad](versioning-policy.md#security-patch-release) se lanzan anualmente (mayo) para todas las [líneas de versión admitidas](lifecycle-policy.md). Estos parches incluyen todas las correcciones de seguridad aisladas publicadas anteriormente. Adobe puede lanzar parches de seguridad adicionales en noviembre si es necesario, pero no está garantizado.

- **Parche**: anualmente (mayo) se lanza un [parche](versioning-policy.md#patch-release) completo para la línea de versión LTS de Adobe Commerce 2.4.x (período de compatibilidad de 3 años).

- **Parches de Beta**: dos veces al año (marzo y noviembre) se lanzan dos [parches beta](versioning-policy.md#beta-patch-release) para la línea de versión Adobe Commerce 2.4.x LTS.

Consulte la siguiente imagen para obtener más información:

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![Calendario de la versión de Adobe Commerce de 2026](../assets/release/release-calendar.drawio.png)
