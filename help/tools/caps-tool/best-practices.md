---
title: Guía de prácticas recomendadas de [!DNL Adobe Commerce Patching Automation]
description: Aprenda a usar [!DNL Adobe Commerce Patching Automation] para planear, validar y aplicar parches de forma segura, minimizando el riesgo de implementación y las interrupciones del servicio.
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# Guía de prácticas recomendadas de [!DNL Adobe Commerce Patching Automation]

Las siguientes prácticas recomendadas son esenciales para realizar correctamente y de forma segura las operaciones de revisión con [!DNL Adobe Commerce Patching Automation]. Esta guía proporciona prácticas recomendadas completas para realizar operaciones de parches eficaces, administrar el entorno y lograr la excelencia operativa.

## Prácticas recomendadas de revisión previa

### Preparación del entorno

**Práctica recomendada:** Prepare siempre el entorno a fondo antes de aplicar los parches para garantizar que las operaciones se realicen correctamente y minimizar los riesgos.

Antes de aplicar los parches, asegúrese de que su entorno está preparado correctamente:

* **Cuenta de Adobe Commerce Cloud**
  * Suscripción activa a Adobe Commerce Cloud
  * Licencia válida de Adobe Commerce
  * [Claves de autenticación del compositor](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/authentication-keys) configuradas para acceder al repositorio de Adobe Commerce
  * Permisos de proyectos y entornos

* **Recursos de entorno**
  * El proyecto tiene capacidad para crear un entorno de integración activo adicional para la operación de revisión. Consulte [Administrar ramas con la consola de Cloud](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/project/console-branches) para obtener información sobre los límites de entorno activos
  * Suficientes recursos de almacenamiento, CPU y memoria
  * Acceso de red a repositorios de Adobe
  * Entorno principal estable para la sincronización

* **Preparación del entorno de producción** (para aplicar parches de producción)
  * Habilitar modo de mantenimiento
  * Deshabilitar trabajos de Cron
  * Establecer procedimientos de ventana de mantenimiento
  * Procedimientos de reversión de documentos
  * Preparar plan de comunicación con las partes interesadas

## Prácticas recomendadas de aplicación de parches

### Horario y programación

**Práctica recomendada:** Programe operaciones de revisión durante períodos de poco tráfico y coordine con las partes interesadas para minimizar el impacto en la empresa.

**Elija el momento adecuado para la aplicación de revisión:**

* **Períodos de poco tráfico**
  * Programar parches durante las horas de menor actividad
  * Evite aplicar parches durante eventos de alto tráfico
  * Planificar el posible tiempo de inactividad durante la validación

* **Consideraciones sobre el entorno de producción**
  * **Ventanas de mantenimiento** - Programar parches de producción durante las ventanas de mantenimiento planificadas
  * **Comunicación con el cliente**: Notifique a los clientes sobre el modo de mantenimiento y el tiempo de inactividad esperado
  * **Coordinación del equipo** - Asegúrese de que todos los miembros del equipo estén al tanto de la programación de mantenimiento
  * **Preparación para la reversión** - Tenga miembros del equipo disponibles para la reversión inmediata si es necesario

### Monitorización y validación

**Durante las operaciones de revisión:**

* **Supervisar progreso**
  * Observar el estado de funcionamiento en tiempo real
  * Preste atención a cualquier advertencia o error
  * No interrumpa el proceso una vez iniciado

* **Validar resultados**
  * Prueba de la funcionalidad esencial después de una aplicación correcta
  * Comprobar las métricas de rendimiento para detectar cualquier degradación
  * Verificar que las medidas de seguridad permanezcan intactas

## Prácticas recomendadas posteriores al parche

### Verificación y pruebas

**Práctica recomendada:** Compruebe siempre el éxito de la aplicación de parches mediante pruebas y supervisión exhaustivas para garantizar la estabilidad y la funcionalidad del sistema.

**Después de aplicar correctamente el parche:**

* **Pruebas funcionales**
  * Probar todos los procesos empresariales críticos
  * Verificar los flujos de pago y pago
  * Comprobar funcionalidad del panel de administración

* **Supervisión del rendimiento**
  * Monitorización de tiempos de carga de página
  * Comprobar rendimiento de base de datos
  * Observe si hay picos de uso de recursos

* **Validación de seguridad**
  * Verificar que las funciones de seguridad funcionen
  * Compruebe si hay nuevas vulnerabilidades de seguridad
  * Autenticación y autorización de pruebas

## Prácticas recomendadas del entorno de producción

### Pruebas previas a la producción

**Práctica recomendada:** Nunca aplique parches directamente en la producción sin realizar pruebas exhaustivas en entornos de preproducción que reflejen la configuración de producción.

**Probar siempre parches antes de la implementación de producción:**

* **Configuración del entorno de prueba**
  * Uso de entornos de ensayo o integración para realizar pruebas
  * Asegúrese de que el entorno de prueba refleje la configuración de producción
  * Realizar pruebas con datos de producción siempre que sea posible

* **Pruebas exhaustivas**
  * Probar todos los procesos empresariales críticos
  * Verificar los flujos de pago y pago
  * Comprobar funcionalidad del panel de administración
  * Prueba de integraciones personalizadas

* **Pruebas de rendimiento**
  * Monitorización del impacto de los parches sobre el rendimiento
  * Compruebe si hay alguna degradación del rendimiento
  * Verificar que el uso de recursos sea aceptable

### Mitigación de riesgos

**Minimizar riesgos durante la aplicación de parches de producción:**

* **Plan de comunicación**
  * Notificar a los clientes sobre ventanas de mantenimiento
  * Mantener informadas a las partes interesadas del progreso
  * Tenga preparados los procedimientos de escalación

* **Estrategia de reversión**
  * Saber cómo revertir rápidamente los parches si es necesario
  * Tener miembros del equipo disponibles para una respuesta inmediata
  * Procedimientos de reversión de documentos

* **Supervisión y alertas**
  * Configurar la monitorización de problemas posteriores al parche
  * Tener alertas para errores críticos
  * Supervise atentamente las métricas de rendimiento

## Resumen de las prácticas recomendadas clave

### Prácticas recomendadas críticas para el éxito de [!DNL Patching Automation]

* Realice pruebas siempre en la preproducción antes de aplicar parches a los entornos de producción
* Habilitar el modo de mantenimiento y deshabilitar los trabajos cron para las operaciones de parches de producción
* Supervise las operaciones y prepare los procedimientos de reversión
* Documente todas las operaciones de parche y mantenga registros completos
* Siga los procedimientos adecuados de administración de cambios y obtenga las aprobaciones adecuadas
* Mantener los entornos sincronizados y mantener una asignación de recursos adecuada
* Establezca procedimientos de soporte claros y mantenga la formación del equipo
* Revisión y mejora periódicas de los procesos de administración de parches

## Temas relacionados

* [Introducción a la automatización de parches](intro.md)
* [Cómo acceder a](access.md)
* [Resumen de flujo de trabajo](workflow.md)
* [Integración de GitHub](github-integration.md)
* [Resolución de problemas](troubleshooting.md)
