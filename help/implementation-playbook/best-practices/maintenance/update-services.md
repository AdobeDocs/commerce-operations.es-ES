---
title: Actualizar prácticas recomendadas de servicios
description: Obtenga información sobre cómo mantener su Adobe Commerce en la pila de tecnología de infraestructura en la nube actualizada.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Actualizar prácticas recomendadas de servicios

Este artículo incluye recomendaciones para mantener actualizado el conjunto de tecnología de Adobe Commerce en la infraestructura en la nube y proporciona vínculos a recursos útiles.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube 2.4.x y posterior

## Actualizar servicios

Actualice los servicios y componentes que utiliza Adobe Commerce antes de que lleguen a la fecha de fin de vida útil o estén cerca de ella. Esto ayuda a cumplir con PCI y a disminuir las vulnerabilidades de seguridad.

Los clientes con planes de inicio pueden autoabastecerse con actualizaciones de servicios. Consulte [Cambiar la versión del servicio](https://devdocs.magento.com/cloud/project/services.html#change-service-version) para obtener más información sobre cómo hacerlo.

Los clientes con planes Pro solo pueden autoabastecerse con actualizaciones de servicios en sus [Entorno de integración](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html). Para actualizar los servicios en Producción, debe [enviar un ticket de asistencia](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) solicitando la actualización.

>[!WARNING]
>
>Las actualizaciones de servicios no se pueden insertar en el entorno de producción sin un aviso de 48 horas laborables a nuestro equipo de infraestructura. Esto es necesario, ya que tenemos que asegurarnos de tener un ingeniero de asistencia técnica de infraestructura disponible para actualizar la configuración dentro de un periodo de tiempo deseado con un tiempo de inactividad mínimo en el entorno de producción.

Puede ver la lista de versiones del servicio y las fechas de finalización de la vida útil en el siguiente archivo: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Este archivo no puede considerarse una única fuente de verdad. Consulte los sitios web oficiales de los proveedores para conocer estas tecnologías si tiene alguna duda.

## Información adicional

[Requisitos del sistema](../../../installation/system-requirements.md)
