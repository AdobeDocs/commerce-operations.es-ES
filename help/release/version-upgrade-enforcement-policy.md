---
title: Directiva de aplicación de actualización de versión de nube
description: 'Obtenga información acerca de la aplicación de actualización de versiones para Adobe Commerce en la nube: por qué Adobe aplica actualizaciones, fechas de aplicación, clausura y acciones requeridas. Consulte la política de ciclo vital para disposiciones transitorias y rutas de migración.'
nudge: false
source-git-commit: 3e0d993078c73a191809c85c1a0ef03ff29a78a6
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# Directiva de aplicación de actualización de versiones para Adobe Commerce en la nube

Cuando el soporte regular y el soporte extendido terminan para una versión de Adobe Commerce, Adobe se reserva el derecho de eliminar Adobe Commerce de los entornos en la nube que aún ejecuten esa versión no compatible. La aplicación de la actualización de versiones solo se aplica a entornos de Adobe Commerce en la nube. Los clientes locales administran su propia infraestructura. Adobe proporciona avisos por adelantado y recursos de asistencia con bastante antelación a estas fechas para ayudarle a planificar su actualización o migración.

Debe pasar a una versión compatible de Adobe Commerce o migrar a [!DNL Adobe Commerce as a Cloud Service] antes de la fecha de [fin de la compatibilidad ampliada](lifecycle-policy.md#end-of-support-dates) publicada para su línea de lanzamiento.

En las siguientes secciones se explica por qué Adobe aplica las actualizaciones, cómo se calculan las fechas de aplicación y qué sucede en la fecha de aplicación. Para ver las fechas de aplicación específicas de la versión, consulte la tabla [Fechas de fin de la compatibilidad](lifecycle-policy.md#end-of-support-dates) en la directiva de ciclo de vida.

>[!NOTE]
>
>Este tema cubre únicamente la aplicación de actualizaciones en la nube. Consulte la [política de ciclo de vida](lifecycle-policy.md) para obtener definiciones del nivel de soporte, [fechas de fin de soporte](lifecycle-policy.md#end-of-support-dates), [disposiciones transitorias de solo seguridad](lifecycle-policy.md#security-only-transitional-period), [dependencias de software de terceros](lifecycle-policy.md#platform-dependencies), [fin de vida útil de PHP y cumplimiento de PCI](lifecycle-policy.md#php-end-of-life-and-pci-compliance), y [opciones de actualización y migración](lifecycle-policy.md#upgrade-and-migration-options). Además de actualizar a un [!DNL Adobe Commerce version] compatible, Adobe también requiere que mantenga dependencias de software de terceros en versiones compatibles de forma activa. Para ver las acciones y plazos específicos requeridos que se aplican a las versiones 2.4.4 a 2.4.9 de [!DNL Adobe Commerce on Cloud], consulte [Aviso de seguridad y cumplimiento](security-enforcement-policy.md).

## Por qué Adobe presenta esta política

Adobe es responsable de la seguridad y la conformidad de la infraestructura de plataformas alojadas en las que se ejecutan los clientes de Adobe Commerce en la nube. Esto incluye mantener todas las dependencias de software subyacentes actualizadas, aplicar parches de seguridad y cumplir con los estándares de cumplimiento, como PCI, en los que los clientes confían.

Cuando los proveedores finalizan oficialmente la compatibilidad con la seguridad de las dependencias de software subyacentes, Adobe ya no puede proporcionar el nivel necesario de cobertura de seguridad y compatibilidad con la plataforma. El hecho de seguir ejecutando tiendas en infraestructuras no admitidas pone en riesgo inaceptable a los clientes, sus compradores y Adobe. Por lo tanto, Adobe presenta una directiva de aplicación de actualización de versiones formal que define cuándo se retiran del mercado los entornos de Adobe Commerce en la nube que ejecutan versiones de Commerce no compatibles, junto con la compatibilidad que proporciona Adobe para ayudarle a planificar su actualización o migración. Consulte [Aviso de seguridad y cumplimiento] para obtener más información.

## Cálculo de las fechas de aplicación de la actualización

Para cada línea de versión de Adobe Commerce, la fecha de aplicación de la actualización se calcula de la siguiente manera:

**Fecha de aplicación de la actualización** = Fecha de disponibilidad general + 3 años de soporte regular + hasta 1 año de soporte extendido

La compatibilidad ampliada se anuncia más cerca del final de la compatibilidad regular para cada línea de versión.

## Qué sucede en la fecha de aplicación de la actualización de la versión

En la fecha de aplicación de la actualización publicada, Adobe dejará de realizar el mantenimiento de todos los entornos de Adobe Commerce en la nube que aún ejecuten la versión afectada y se reservará el derecho de eliminarlos. Recibirá notificaciones avanzadas en los hitos clave previos a la fecha de aplicación de la actualización de la versión. Adobe proporcionará un período de tiempo para la exportación de datos antes de la desactivación del entorno para que pueda recuperar los datos.

La primera fecha de aplicación de esta directiva es el **1 de junio de 2027** para las líneas de versión que lleguen al final de la compatibilidad extendida antes de esa fecha. Consulte la tabla [Fechas de fin de soporte](lifecycle-policy.md#end-of-support-dates) para ver las fechas de aplicación específicas de la versión.
