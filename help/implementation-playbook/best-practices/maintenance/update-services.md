---
title: Actualizar prácticas recomendadas de servicios
description: Obtenga información sobre cómo mantener su Adobe Commerce en la pila de tecnología de infraestructura en la nube actualizada.
role: Developer
feature: Best Practices
exl-id: 62aeffe3-b5a6-49f8-a39b-3219b46cd486
source-git-commit: 5e3289b328b51eb50354efdc1571283791175b9a
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Actualizar prácticas recomendadas de servicios

Este artículo incluye recomendaciones para mantener actualizado el conjunto de tecnología de Adobe Commerce en la infraestructura en la nube y proporciona vínculos a recursos útiles.

## Productos y versiones afectados

Adobe Commerce en la infraestructura en la nube 2.4.x y posterior

## Actualizar servicios

Actualice los servicios y componentes que utiliza Adobe Commerce antes de que lleguen a la fecha de fin de vida útil o estén cerca de ella. Esto ayuda a cumplir con PCI y a disminuir las vulnerabilidades de seguridad.

Los clientes con planes de inicio pueden autoabastecerse con actualizaciones de servicios. Consulte [Cambiar la versión del servicio](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/configure/service/services-yaml#change-service-version) para obtener más información sobre cómo hacerlo.

Los clientes con planes Pro solo pueden autoabastecerse con actualizaciones de servicios en su [entorno de integración](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/integration-environment-enhancement-request-pro-and-starter.html?lang=es). Para las actualizaciones de servicios en Producción, debe [enviar un vale de soporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=es#submit-ticket) solicitando la actualización.

>[!WARNING]
>
>Las actualizaciones de servicios no se pueden insertar en un entorno de producción sin un aviso previo de 48 horas laborables al equipo de infraestructura de Adobe. Esto es necesario para que Adobe pueda garantizar que haya un ingeniero de asistencia técnica de infraestructura disponible para actualizar la configuración dentro de un periodo de tiempo deseado con un tiempo de inactividad mínimo en el entorno de producción. Adobe recomienda poner el sitio en modo de mantenimiento durante la actualización del servicio.

Puede ver la lista de versiones del servicio y las fechas de finalización de la vida útil en el siguiente archivo: [https://github.com/magento/ece-tools/blob/develop/config/eol.yaml](https://github.com/magento/ece-tools/blob/develop/config/eol.yaml).

>[!NOTE]
>
>Este archivo no puede considerarse una única fuente de verdad. Consulte los sitios web oficiales de los proveedores para conocer estas tecnologías si tiene alguna duda.

## Más información

[Requisitos del sistema](../../../installation/system-requirements.md)
