---
title: Responder a un incidente de seguridad
description: Gestione los incidentes de seguridad siguiendo las prácticas recomendadas para responder y solucionar los problemas de seguridad que afectan a la disponibilidad y el rendimiento del sitio.
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: e63f68dd469564e70269154810cbfbd95d2b2e57
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 0%

---

# Prácticas recomendadas para responder a un incidente de seguridad

El siguiente artículo resume las prácticas recomendadas para responder a un incidente de seguridad y solucionar problemas que afectan a la disponibilidad, fiabilidad y rendimiento del sitio de Adobe Commerce.

Las siguientes prácticas recomendadas pueden ayudar a evitar el acceso no autorizado y los ataques de malware. Si se produce un incidente de seguridad, estas prácticas recomendadas le ayudan a prepararse para una respuesta inmediata, realizar un análisis de las causas principales y administrar el proceso de corrección para restaurar las operaciones normales.

>[!TIP]
>
>El Adobe ha descubierto que la mayoría de los incidentes de seguridad ocurren cuando los actores se aprovechan de las vulnerabilidades existentes, sin parches, contraseñas deficientes y configuraciones débiles de propiedad y permisos en la aplicación de Commerce y la configuración de la infraestructura. Minimice la ocurrencia de incidentes de seguridad revisando y siguiendo las prácticas recomendadas de seguridad de Adobe al configurar, configurar y actualizar instalaciones de Adobe Commerce. Ver [Proteja su sitio e infraestructura de Commerce](../launch/security-best-practices.md).


## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Responder a un incidente

Si cree que el proyecto de infraestructura de Adobe Commerce en la nube se ve afectado por un incidente de seguridad, los primeros pasos esenciales son:

- Auditar el acceso de todos los administradores a cuentas de usuario
- Habilitar controles avanzados de autenticación multifactor (MFA)
- Conservar registros críticos
- Revise las actualizaciones de seguridad de su versión de Adobe Commerce.

A continuación se detallan más recomendaciones.

## Tomar medidas inmediatas en caso de un ataque

En el desafortunado caso de un compromiso con el sitio, estas son algunas recomendaciones clave a seguir:

- Póngase en contacto con el integrador de sistemas y el personal de seguridad adecuado para llevar a cabo tareas de investigación y corrección.

- Determine el alcance del ataque:
   - ¿Se accedió a la información de tarjeta de crédito?
   - ¿Qué información fue robada?
   - ¿Cuánto tiempo ha pasado desde el compromiso?
   - ¿La información estaba encriptada?

- Intente encontrar el vector de ataque para determinar cuándo y cómo se comprometió el sitio, revisando los archivos de registro del servidor y los cambios de archivo.

   - En determinadas circunstancias, puede ser aconsejable borrar y volver a instalar todo o, en el caso del alojamiento virtual, crear una nueva instancia. El malware podría estar oculto en una ubicación insospechada a la espera de restaurarse.

   - Elimine todos los archivos innecesarios. A continuación, vuelva a instalar los archivos necesarios desde un origen limpio y conocido. Por ejemplo, puede volver a instalar con archivos del sistema de control de versiones o desde los archivos de distribución originales desde el Adobe.

   - Restablezca todas las credenciales, incluida la base de datos, el acceso a archivos, las integraciones de pago y envío, los servicios web y el inicio de sesión del administrador. Restablezca también todas las claves y cuentas de integración y API que puedan utilizarse para atacar el sistema.

## Análisis de un incidente

El primer paso del análisis de incidentes es recopilar tantos hechos como sea posible y con la mayor rapidez posible. La recopilación de información sobre el incidente puede ayudar a determinar la causa potencial del mismo. Adobe Commerce proporciona las herramientas siguientes para ayudarle con el análisis de incidentes.

- [Registros De Acciones De Administración De Auditoría](https://experienceleague.adobe.com/docs/commerce-admin/systems/action-logs/action-log-report.html).

  El informe Registros de acciones muestra un registro detallado de todas las acciones de administración habilitadas para el registro. Cada registro tiene una marca de hora y registra la dirección IP y el nombre del usuario. El detalle del registro incluye los datos de usuario de administración y los cambios relacionados que se realizaron durante la acción.

- Analice eventos con la [herramienta Observación para Adobe Commerce](../../../tools/observation-for-adobe-commerce/intro.md).

  La herramienta Observación para Adobe Commerce le permite analizar problemas complejos para ayudar a identificar causas básicas. En lugar de rastrear datos dispares, puede dedicar su tiempo a correlacionar eventos y errores para obtener información más detallada sobre las causas de los cuellos de botella del rendimiento.

  Use la ficha **Seguridad** de la herramienta para tener una visión clara de los posibles problemas de seguridad y ayudar a identificar las causas principales y mantener el rendimiento óptimo de los sitios.

- Analizar registros con [Registros de New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html)

  Los proyectos Pro de Adobe Commerce en infraestructura en la nube incluyen el servicio [Registros de New Relic](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management.html). El servicio está preconfigurado para agregar todos los datos de registro de los entornos de ensayo y producción y mostrarlos en un panel de administración de registros centralizado, donde puede buscar y visualizar los datos agregados.

  Para otros proyectos de Commerce, puede configurar y utilizar el servicio [Registros de New Relic](https://docs.newrelic.com/docs/logs/get-started/get-started-log-management/) para completar las tareas siguientes:
   - Use [consultas de New Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) para buscar datos de registro agregados.
   - Visualice los datos de registro mediante la aplicación New Relic Logs.

## Cuentas de auditoría, código y base de datos

Revise la configuración y los registros de las cuentas de administrador y de usuario de Commerce, el código de aplicación y la base de datos para identificar y limpiar el código sospechoso y garantizar la seguridad del acceso a la cuenta, el sitio y la base de datos. A continuación, vuelva a implementar según sea necesario.

Continúe monitorizando de cerca el sitio después del incidente, ya que muchos sitios se comprometen de nuevo en cuestión de horas. Garantice la revisión continua del registro y la monitorización de la integridad de los archivos para detectar rápidamente cualquier señal de nuevo compromiso.

### Auditar cuentas de usuario de administración

- [Revisar el acceso de los usuarios administradores](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html): elimine las cuentas antiguas, no utilizadas o sospechosas y gire las contraseñas de todos los usuarios administradores.

- [Revisar la configuración de seguridad de administración](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html): compruebe que la configuración de seguridad de administración sigue las prácticas recomendadas de seguridad.

- [Revise las cuentas de usuario de Adobe Commerce en los proyectos de infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html): elimine las cuentas antiguas, no utilizadas o sospechosas y gire las contraseñas de todos los usuarios administradores de proyectos en la nube. Asegúrese de que la configuración de seguridad de la cuenta es correcta.

- [Auditar claves SSH](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) para Adobe Commerce en la infraestructura en la nube: revise, elimine y gire las claves SSH.

### Código de auditoría

- Desde el administrador, revise la [configuración del encabezado y pie de página del HTML](https://experienceleague.adobe.com/docs/commerce-admin/content-design/design/page-setup.html) en todos los niveles de ámbito, incluidos `website` y `store view`. Elimine cualquier código JavaScript desconocido de los scripts y las hojas de estilos, así como la configuración de varios HTML. Conservar solo código reconocido, como fragmentos de seguimiento.

- Compare el código base de producción actual con el código base almacenado en el Sistema de control de versiones (VCS).

- Ponga en cuarentena cualquier código sospechoso.

- Asegúrese de que no queden restos de código sospechoso mediante la reimplementación de la base de código en el entorno de producción.

### Auditoría de configuración y registros de base de datos

- Revise los procedimientos almacenados para ver si hay modificaciones.

- Compruebe que solo la instancia de Commerce puede acceder a la base de datos.

- Verificar que el malware ya no está presente analizando el sitio con herramientas de análisis de malware disponibles públicamente.

- Proteja el panel de administración cambiando su nombre y comprobando que las direcciones URL del sitio `app/etc/local.xml` y `var` no son de acceso público.

- Continúe monitorizando de cerca el sitio después del incidente, ya que muchos sitios se comprometen de nuevo en cuestión de horas. Garantice la revisión continua del registro y la monitorización de la integridad de los archivos para detectar rápidamente cualquier señal de nuevo compromiso.

## Eliminar advertencias de Google

Si Google ha marcado el sitio como que contiene código malicioso, solicite una revisión una vez que se haya limpiado el sitio. Las revisiones de los sitios infectados con malware tardan unos días. Una vez que Google determina que el sitio está limpio, las advertencias de los resultados de búsqueda y los exploradores deben desaparecer en un plazo de 72 horas. Ver [Solicitar revisión](https://web.dev/articles/request-a-review).

## Revisar lista de comprobación de resultados de malware

Si las herramientas de análisis de malware disponibles públicamente confirman un ataque de malware, investigue el incidente. Trabaje con el integrador de soluciones para limpiar el sitio y seguir el proceso de corrección recomendado.

## Realizar revisiones adicionales

Cuando se trata de ataques sofisticados, el mejor curso de acción es trabajar con un desarrollador experimentado, un experto de terceros o un integrador de soluciones para reparar completamente el sitio y revisar las prácticas de seguridad. Trabajar con profesionales de seguridad experimentados garantiza que se tomen medidas completas y avanzadas para garantizar la seguridad de su negocio y de sus clientes.

## Más información

- [Marco de análisis de causa raíz](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
