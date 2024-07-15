---
title: Pasos previos al lanzamiento
description: Utilice nuestras listas de comprobación previas al lanzamiento para garantizar una implementación sin problemas del sitio de Adobe Commerce.
exl-id: bd10881f-0336-4aa4-82ad-4d635010e2e4
feature: Deploy
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Pasos previos al lanzamiento

Cuando haya completado la implementación y las pruebas en los entornos de ensayo, puede comenzar la preparación del lanzamiento del sitio. El ensayo es un entorno casi de producción que se ejecuta en hardware, configuraciones, arquitectura y servicios similares. Puede reducir el tiempo de inactividad y hacer que la extensión, el servicio, las configuraciones personalizadas y las pruebas de aceptación de usuarios comerciales sean componentes vitales para el lanzamiento de sus sitios y tiendas.

La lista de comprobación previa al lanzamiento es necesaria para verificar el estado antes del lanzamiento, que incluye las siguientes verificaciones importantes:

- Congelación de código para despliegue
- Asegúrese de que el tiempo de inactividad se haya comunicado con antelación al menos un día para la versión de mantenimiento y una semana para el primer lanzamiento
- Los scripts de implementación se configuran completamente para los entornos de producción, ensayo e integración
- Todas las bases de datos están configuradas e idénticas entre los entornos de ensayo y producción
- Los certificados SSL (TLS) se validan para los entornos de ensayo y producción
- Los servicios de correo están bien configurados y funcionan para los correos electrónicos transaccionales
- CDN está configurado para entornos de ensayo/producción
- Configuración del análisis de seguridad para entornos de ensayo/producción
   - Análisis de seguridad de Adobe Commerce
- Realizar evaluación de rendimiento por
   - JMeter
   - Asedio
   - Prueba de página web
   - Velocidad de página de Google
- Valide todas las integraciones de terceros que funcionarán en la aplicación (OMS, CRM).
- Habilitar la herramienta de monitorización del rendimiento (New Relics)
- Actividades de migración de datos en ensayo (si las hay)

![Diagrama que muestra la fase 1 del proceso de lanzamiento](../../assets/playbooks/launch-steps-1.svg)

Las principales diferencias entre las implementaciones locales y en la nube de Adobe Commerce son las herramientas y los scripts de implementación, así como la configuración de SSL, el servicio de correo y CDN. Sin embargo, el proceso sigue siendo el mismo.

Para el certificado SSL (TLS), Adobe Commerce en la infraestructura de la nube proporciona un certificado comodín de Fastly. Para empezar a usarlo, debe pasar la validación: agregue el registro TXT de Fastly al nombre de dominio Apex dentro de la configuración DNS. El registro TXT de Fastly se puede encontrar en la hoja de cálculo de incorporación, de lo contrario, debe enviar al servicio de asistencia un ticket para obtenerlo. Reemplace este texto con sus preguntas/comentarios aquí. Si utiliza su propio certificado SSL (TLS) en lugar de un certificado comodín de Fastly, envíe un ticket de asistencia con el certificado adjunto a la configuración.

Adobe Commerce en la infraestructura en la nube proporciona la funcionalidad SendGrid Mail para sus correos electrónicos transaccionales. Para los planes Pro, debe agregar los registros de SendGrid a la configuración de DNS. Los registros de SendGrid se pueden encontrar en la hoja de cálculo de incorporación, de lo contrario, SI o el comerciante deben enviar tickets de asistencia para obtenerlos. Para empezar, no es necesario realizar ningún cambio en el DNS; SendGrid está preconfigurado para usted.

## Lista de comprobación completa antes del lanzamiento

La lista de comprobación completa previa al lanzamiento muestra todas las actividades principales cuya integridad es necesaria para pasar al estado de lanzamiento.

- Actualización de los planes de mitigación de riesgos del lanzamiento
- Se proporcionaron los nombres de dominio correctos
- Se han probado los correos electrónicos salientes
- El certificado SSL está aprovisionado y configurado
- La configuración más importante de la aplicación de Adobe Commerce se actualiza correctamente
- Las direcciones URL base y URL de administrador base se establecen correctamente en el nombre de host final
- Se cambian las contraseñas de administrador
- Se eliminan todos los usuarios con acceso a la aplicación que ya no requieran acceso
- Configuración de pago para el entorno de producción (para algunos, el pago se realiza mediante el modo de zona protegida para realizar pruebas)
- Se borran los datos de prueba (cliente, lista de deseos, revisiones, pedidos y datos relacionados) de la base de datos de producción

![Diagrama que muestra la fase 2 del proceso de lanzamiento](../../assets/playbooks/launch-steps-2.svg)
