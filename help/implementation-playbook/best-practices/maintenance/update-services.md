---
title: Prácticas recomendadas de actualización de servicios
description: Obtenga información sobre cómo mantener actualizado su Adobe Commerce en la pila de tecnología de infraestructura en la nube.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: cf8626bfab170a1e12cc72f0bc344c9beb9349a7
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---


# Prácticas recomendadas de actualización de servicios

Este artículo proporciona recomendaciones para mantener su Adobe Commerce actualizado en la pila de tecnología de la infraestructura de nube y proporciona vínculos a recursos útiles.

## Productos y versiones afectados

Adobe Commerce en la infraestructura de nube 2.4.x y posteriores

## Actualizar servicios

Actualice los servicios y componentes utilizados por Adobe Commerce antes de que alcancen o estén próximos a la fecha de finalización de la vida útil. Esto ayuda a mantenerse al día con el cumplimiento de PCI y a reducir las vulnerabilidades de seguridad.

Los clientes con planes Starter pueden autoabastecerse en actualizaciones de servicios. Consulte [Cambiar la versión del servicio](https://devdocs.magento.com/cloud/project/services.html#change-service-version) para obtener más información sobre cómo hacerlo.

Los clientes con planes Pro solo pueden autoabastecerse en actualizaciones de servicios en sus [Entorno de integración](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). Para las actualizaciones de servicios en Producción, debe [enviar un ticket de asistencia](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) solicitando la actualización.

>[!WARNING]
>
>Las actualizaciones de servicio no se pueden impulsar al entorno de producción sin previo aviso de 48 horas laborables a nuestro equipo de infraestructura. Esto es necesario, ya que necesitamos asegurarnos de tener un ingeniero de soporte de infraestructura disponible para actualizar su configuración dentro de un periodo de tiempo deseado con un downtime mínimo para su entorno de producción.

Puede ver la lista de versiones de servicio y fechas de finalización de la vida útil en el siguiente archivo: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Este archivo no puede considerarse una única fuente de verdad. Consulte los sitios web oficiales del proveedor para estas tecnologías si hay dudas.

## Información adicional

[Requisitos del sistema](../../../installation/system-requirements.md)
