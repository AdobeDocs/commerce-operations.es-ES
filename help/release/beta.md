---
title: Versiones beta
description: Obtenga información sobre las versiones beta de Adobe Commerce y cómo participar.
source-git-commit: 1ce0ff87291c5c3f0fd130aa351bc975f42501e3
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---


# Versiones beta de Adobe Commerce

A partir de junio de 2023 y en adelante, Adobe lanzará versiones beta públicas para las versiones de parches (&quot;versiones beta&quot;). Las versiones beta están disponibles para todos los clientes y socios de Adobe Commerce antes de la disponibilidad general (GA) e incluyen correcciones de seguridad, conformidad normativa, rendimiento y calidad de alta prioridad.

>[!IMPORTANT]
>
>Las versiones beta pueden contener defectos y se proporcionan &quot;TAL CUAL&quot; sin garantía de ningún tipo. Adobe no tiene obligación de mantener, corregir, actualizar, cambiar, modificar o admitir de otro modo (a través de los Servicios de soporte de Adobe o de otro modo) las versiones beta. Se recomienda a los clientes que tengan cuidado y no dependan en modo alguno del correcto funcionamiento o rendimiento de las versiones beta y/o de la documentación o los materiales adjuntos. Por lo tanto, cualquier uso de las versiones beta es totalmente bajo el propio riesgo del cliente.

## Liberar contenido

Cada versión beta de Adobe Commerce incluye todos los cambios entregados al código principal de Adobe Commerce en la fecha programada de lanzamiento, incluidas, entre otras, las siguientes áreas funcionales:

- Últimas correcciones de seguridad
- Mejoras de rendimiento
- Mejoras de GraphQL
- Correcciones de errores de calidad generales
- Contribuciones comunitarias
- Cambios necesarios para admitir la compatibilidad con [Servicios de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html)

## Convenciones y programación de nombres

Adobe lanzará parches beta dos veces al año. El primer parche beta se suele lanzar tres meses después de la publicación general de un nuevo parche de la aplicación principal.

Los paquetes de la versión beta tienen un `-betaX` sufijo. Por ejemplo, los paquetes de la versión beta de Adobe Commerce 2.4.7 utilizan la siguiente convención de nombres:

- `2.4.7-beta1`
- `2.4.7-beta2`

Consulte la [programación de versiones](schedule.md) para obtener la lista de fechas públicas de lanzamiento de la beta.

## Ventajas de participar

Cuanto antes vea el código que estamos desarrollando, antes podrá preparar su tecnología y a los comerciantes para la próxima actualización.

Aunque las cosas pueden cambiar, la participación en las versiones beta le permitirá empezar a comprender en qué parte de la base de código se producen cambios y comenzar a prepararse con antelación a la fecha de lanzamiento de GA.

## Acceso a la versión beta

Las versiones beta de Adobe Commerce se distribuyen de la misma manera que cualquier otra versión de parches de Adobe Commerce: como metapaquetes de Composer en `https://repo.magento.com`. El código fuente está disponible en [GitHub](https://github.com/magento/magento2).

Consulte [Inicio rápido de la instalación del Compositor](../installation/composer.md) para obtener más información.

## Informe de problemas

Adobe no proporciona el servicio de soporte de Adobe estándar para las versiones beta.

Para enviar comentarios relacionados con las versiones beta, siga nuestros [flujo regular de informes de problemas](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) el [GitHub](https://github.com/magento/magento2).

Nuestros equipos internos monitorizarán todos los problemas críticos notificados en relación con la última versión beta y les darán prioridad para que se resuelvan antes de la fecha de lanzamiento de GA.
