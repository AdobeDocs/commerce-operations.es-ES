---
title: Programación de lanzamiento del parche
description: Descubra cuándo planea Adobe anunciar el lanzamiento de nuevos parches y correcciones de seguridad para Adobe Commerce.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 0f46bdfd0afbca07e0d60e995ee9426f5408671d
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 4%

---


# Programación de lanzamiento del parche

Adobe se esfuerza continuamente por encontrar el equilibrio adecuado entre hacer que las actualizaciones de los productos sean sencillas y predecibles, y al mismo tiempo ofrecer mejoras más rápidas a los usuarios que las adoptaron por primera vez (consulte [directiva de versiones](versioning-policy.md)).

El propósito de esta programación es proporcionar fechas para cuándo Adobe planea anunciar el lanzamiento de [parches](versioning-policy.md#patch-release) para cada línea de lanzamiento compatible de la aplicación principal de Adobe Commerce PHP. Las versiones de parches son oportunidades para actualizar la base de código principal a fin de mantener la seguridad, la fiabilidad y el rendimiento de su plataforma.

>[!NOTE]
>
>Para obtener más información sobre las nuevas características, la infraestructura en la nube y las versiones de extensibilidad, consulte la [documentación de la versión de Adobe Commerce Services](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all).

Además de los parches de calidad, seguridad y beta programados que se enumeran en esta página, Adobe proporciona acceso a [parches individuales](versioning-policy.md#individual-patch) mediante la [Herramienta de parches de calidad](../tools/quality-patches-tool/usage.md). La herramienta le permite aplicar, revertir y ver información general sobre todos los parches individuales que están disponibles para la versión instalada de Adobe Commerce.

Las versiones de parches de Adobe Commerce se publican en función de las siguientes directrices:

- **Archivo de parches de seguridad aislado**: los [archivos de parches de seguridad](versioning-policy.md#isolated-security-patch-file) individuales y no acumulativos se liberan de forma independiente para permitir una corrección más rápida y se incorporan al siguiente parche de seguridad completo. Para aplicar un archivo de parches de seguridad aislado, los clientes deben estar en la última versión de parches de solo seguridad (la última versión -p) para su línea de versiones admitida, ya que las correcciones de seguridad aisladas se prueban exclusivamente en esa versión.

- **Parches de seguridad**: como mínimo, [los parches de seguridad](versioning-policy.md#security-patch-release) se lanzan anualmente para todas las [líneas de versión admitidas](lifecycle-policy.md). Estos parches incluyen todas las revisiones de seguridad, cumplimiento y calidad publicadas anteriormente.  Adobe puede lanzar parches de seguridad adicionales si es necesario, pero no está garantizado.

- **Parche**: anualmente (mayo) se lanza un [parche](versioning-policy.md#patch-release) completo para la línea de versión LTS de Adobe Commerce 2.4.x (período de compatibilidad de 3 años).

- **Parches Alpha**-Se lanza anualmente un [parche alfa](versioning-policy.md#alpha-patch-release) para la línea de versión Adobe Commerce 2.4.x LTS.

- **Parches de Beta**: se lanza anualmente uno de [parches beta](versioning-policy.md#beta-patch-release) para la línea de versión Adobe Commerce 2.4.x LTS.

Consulte la siguiente imagen para obtener más información:

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![Calendario de la versión de Adobe Commerce de 2026](../assets/release/release-calendar.png)


## Canales de notificación de versiones

Adobe notifica a los clientes sobre las nuevas versiones de parches a través de los siguientes canales:

- [Avisos y boletines de seguridad de Adobe](https://helpx.adobe.com/security/security-bulletin.html#magento)
- Correo electrónico
- Alertas en el producto

>[!NOTE]
>
> Para ver las fechas de lanzamiento de cada versión secundaria, revisión y de seguridad, y las fechas de fin de la compatibilidad regular, consulte [Versiones publicadas](https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions).
