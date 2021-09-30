---
title: Pasos previos al lanzamiento
description: Utilice nuestras listas de comprobación previas al lanzamiento para garantizar una implementación sin problemas del sitio de comercio de Adobe.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%

---


# Pasos previos al lanzamiento

Cuando haya completado la implementación y las pruebas en los entornos de ensayo, puede comenzar la preparación del lanzamiento del sitio. El ensayo es un entorno de casi producción que se ejecuta en hardware, configuraciones, arquitectura y servicios similares. Puede reducir el tiempo de inactividad y hacer que la extensión, el servicio, las configuraciones personalizadas y la aceptación de los usuarios comerciantes prueben componentes vitales para lanzar sus sitios y tiendas.

La lista de comprobación previa al lanzamiento es necesaria para verificarla antes del estado de inicio, que incluye las siguientes verificaciones importantes:

- Congelación de código para la implementación
- Asegúrese de que el tiempo de inactividad se haya comunicado con antelación al menos un día para la versión de mantenimiento y una semana para el primer lanzamiento
- Los scripts de implementación se configuran/configuran completamente para los entornos de producción/ensayo/integración
- Todas las bases de datos están configuradas y son idénticas entre los entornos de ensayo y producción
- Los certificados SSL (TLS) se validan para entornos de ensayo/producción
- Los servicios de correo están bien configurados y funcionan para los correos electrónicos transaccionales
- CDN está configurado para entornos de ensayo/producción
- Configuración del análisis de seguridad para entornos de ensayo/producción
   - Análisis de seguridad de Adobe Commerce
- Realice una evaluación del rendimiento de
   - JMeter
   - Siege
   - Prueba de página web
   - Velocidad de página de Google
- Validar todas las integraciones de terceros que funcionen en la aplicación (OMS, CRM)
- Habilitar la herramienta de monitorado de rendimiento (nuevas reliquias)
- Actividades de migración de datos en ensayo (si las hay)

![Diagrama de la fase 1 del proceso de lanzamiento](../../assets/playbooks/launch-steps-1.svg)

Las principales diferencias entre las implementaciones locales y en la nube de Adobe Commerce son los scripts y las herramientas de implementación, así como la configuración para SSL, el servicio de correo y CDN. Sin embargo, el proceso sigue siendo el mismo.

Para el certificado SSL (TLS), Adobe Commerce en la infraestructura de la nube proporciona un certificado comodín Finfinito. Para empezar a utilizarla, debe pasar la validación: agregue el registro TXT de inicio rápido al nombre de dominio de ápex dentro de la configuración DNS. El registro TXT FAdministración se encuentra en la hoja de cálculo de incorporación; de lo contrario, deberá enviar un ticket de soporte para obtenerlo. Reemplace este texto por sus preguntas/comentarios aquí. Si utiliza su propio certificado SSL (TLS) en lugar de un certificado comodín FIENE, envíe un vale de asistencia con el certificado adjunto a la configuración.

Adobe Commerce en la infraestructura de la nube proporciona la funcionalidad SendGrid Mail para sus correos electrónicos transaccionales. Para planes Pro, debe agregar registros SendGrid a la configuración DNS. Los registros de SendGrid se pueden encontrar en la hoja de cálculo de incorporación, de lo contrario, SI o el comerciante deben enviar tickets de soporte para obtenerlos. Para empezar, no es necesario realizar ningún cambio en el DNS; SendGrid está preconfigurado para usted.

## Lista de comprobación completa previa al lanzamiento

La lista de comprobación completa previa al lanzamiento muestra todas las actividades principales cuya integridad es necesaria para pasar al estado de lanzamiento.

- Se actualizaron los planes de mitigación de riesgos de Go-live
- Se han proporcionado los nombres de dominio correctos
- Se han probado los correos electrónicos salientes
- El certificado SSL está aprovisionado y configurado
- La configuración importante de la aplicación de comercio de Adobe se actualiza correctamente
- Las direcciones URL base y la URL de administración base se establecen correctamente en el nombre de host final
- Se han cambiado las contraseñas de los administradores
- Se eliminan todos los usuarios con acceso a la aplicación que ya no requieran acceso
- Configuración de pago para el entorno de producción (para algunos, el pago está usando el modo de simulación de pruebas)
- Los datos de prueba (cliente, lista de deseos, revisiones, pedidos y datos relacionados) de la base de datos de producción se borran

![Diagrama de la fase 2 del proceso de lanzamiento](../../assets/playbooks/launch-steps-2.svg)
