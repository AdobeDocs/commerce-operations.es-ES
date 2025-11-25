---
title: Guía de solución de problemas de [!DNL Cloud Automation Patching Service (CAPS)]
description: Solucionar problemas comunes y mensajes de error en  [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 0%

---

# [!DNL Cloud Automation Patching Service (CAPS)] guía de solución de problemas

Al usar [!DNL CAPS] para operaciones de revisión, puede encontrar mensajes de error y problemas que pueden impedir la aplicación o reversión de revisión correcta. Esta guía proporciona soluciones para los problemas más comunes.

## Pasos rápidos de solución de problemas

### Si falla la operación de parche

* Compruebe el estado de la operación para comprender qué fase falló
* Revisar mensajes de error por motivos de error específicos
* Examinar los registros de errores para obtener detalles técnicos
* Siga las soluciones proporcionadas en esta guía

### Duración de operaciones de parche

En la mayoría de los entornos, la siguiente cronología describe cuánto tiempo deben tardar las operaciones de parche, pero podría tardar más según el tamaño y la complejidad del entorno:

* **Procesamiento previo:** de 2 a 5 minutos
* **Parches:** de 5 a 15 minutos
* **Procesamiento posterior:** de 10 a 40 minutos
* **Total:** 15-60 minutos

### Cancelación de un parche en curso

>[!WARNING]
>
>Una vez que se inicia una operación de parche, debe permitirse que se complete. El sistema incluye procedimientos de limpieza que se ejecutan incluso si las operaciones fallan. Si se interrumpe el proceso, su entorno puede quedar en un estado incoherente.

## Mensajes de éxito comunes

* **&quot;Trabajo completado correctamente&quot;** - El parche se aplicó/revirtió correctamente sin ningún problema.

* **&quot;Se ha aplicado el parche&quot;** - Está intentando aplicar un parche que ya se ha aplicado. El sistema detectó que el parche ya está presente en su entorno. No es necesario realizar ninguna acción.

* **&quot;El parche se ha revertido&quot;** - Está intentando revertir un parche que ya se ha revertido. El sistema detectó que el parche no se está aplicando actualmente. No es necesario realizar ninguna acción.

## Mensajes de error comunes y soluciones

### Errores de aplicación de parche

#### &quot;No se puede aplicar el parche porque [!DNL CAPS] ha detectado estos problemas con el código base o el archivo de parche&quot;

**Cuando se produce:** Durante la comprobación preliminar

**Causa:** El parche entra en conflicto con la base de código actual O hay un problema con el propio parche

**Soluciones:**

* Revise los registros de errores detallados proporcionados para identificar si se trata de un problema de código base o de parche
* Compruebe si hay personalizaciones en conflicto en el código
* Verifique que el parche sea compatible con su versión de Adobe Commerce
* Considere la posibilidad de resolver conflictos manualmente o póngase en contacto con el soporte técnico

#### &quot;Este parche no fue administrado por [!DNL CAPS]. No se puede revertir&quot;

**Cuando se produce:** Durante las operaciones de reversión

**Causa:** Está intentando revertir un parche que no se aplicó mediante [!DNL CAPS]

**Solución:** Use el mismo método que se usó para aplicar el parche originalmente o póngase en contacto con el soporte técnico para obtener ayuda manual

### Errores de entorno y validación

#### &quot;El entorno no está sincronizado con el elemento principal&quot;

**Cuando se produce:** Durante la validación

**Causa:** El entorno de integración difiere del entorno principal

**Soluciones:**

* Sincronizar el entorno con la rama principal
* Vuelva a intentar la operación de parche
* Póngase en contacto con el servicio de asistencia si persisten problemas de sincronización

#### &quot;No se cumplen las salvaguardias del entorno de producción&quot;

**Cuando esto sucede:** Durante la comprobación preliminar de entornos de producción

**Causa:** El entorno de producción no cumple las condiciones de seguridad requeridas

**Soluciones:**

* Habilite el modo de mantenimiento para su tienda de producción
* Deshabilitar los trabajos cron en el entorno de producción
* Compruebe que se cumplen ambas condiciones antes de volver a intentarlo

>[!IMPORTANT]
>
> [!DNL CAPS] no habilita automáticamente el modo de mantenimiento ni deshabilita los trabajos cron; usted debe realizar estos trabajos de forma externa

#### &quot;Se ha aplicado el parche, pero la comprobación de estado no ha funcionado. Considere la posibilidad de revertir&quot;

**Cuando ocurre:** Después de aplicar el parche durante la validación

**Causa:** El parche se aplicó correctamente, pero no se pudo comprobar el estado

**Soluciones:**

* Revisar los registros de aplicaciones para detectar errores específicos
* Prueba manual de la funcionalidad esencial
* Considere la posibilidad de revertir el parche si los problemas persisten
* Póngase en contacto con el soporte si necesita ayuda

### Errores de autenticación y acceso

#### &quot;Error de autenticación para el repositorio de Adobe Commerce&quot;

**Cuando ocurre:** Durante cualquier etapa

**Causa:** credenciales de repositorio de Adobe Commerce no válidas o caducadas

**Soluciones:**

Existen dos opciones recomendadas para resolver este problema:

**Opción 1: corregir `env:COMPOSER_AUTH` variable de nivel de entorno (recomendado)**

* Asegúrese de haber configurado las credenciales correctas para `env:COMPOSER_AUTH`.
* Para acceder a la configuración global, haga clic en el icono de engranaje en la parte superior izquierda de la interfaz de usuario del proyecto en la nube y, a continuación, seleccione la pestaña **Variables**.
* Asegúrese de seleccionar _Disponible durante la compilación_ y deseleccione _Disponible durante la ejecución_.

Si la Opción 1 no resuelve su problema, continúe con la Opción 2.

**Opción 2: crear e implementar el archivo `auth.json` manualmente**

* SSH en el servidor.
* Recupere el contenido de la variable `env:COMPOSER_AUTH` actual mediante:\
  `echo $COMPOSER_AUTH`
* Copie todo el contenido del paso anterior (en formato JSON).
* Cree un nuevo archivo de nombre `auth.json` con este contenido.
* Confirme este archivo `auth.json` recién creado en el directorio raíz del repositorio.
* Déclencheur una nueva implementación.

#### &quot;Permisos insuficientes para el acceso al entorno&quot;

**Cuando ocurre:** Durante la creación del entorno o el acceso

**Causa:** Su cuenta de usuario carece de los permisos necesarios

**Soluciones:**

* Compruebe la función de usuario y los permisos
* Póngase en contacto con el administrador del sistema
* Compruebe que tiene permisos de administración del entorno
* Asegúrese de que tiene permisos de implementación

### Errores de recursos y cuotas

#### &quot;Se ha superado la cuota de entorno&quot;

**Cuando se produce:** Durante la creación del entorno

**Causa:** Ha alcanzado el límite de entorno

**Soluciones:**

* Desactivar entornos no utilizados
* Limpieza de ramas e implementaciones antiguas
* Póngase en contacto con el servicio de asistencia para solicitar aumento de cuota
* Considere actualizar su plan

#### &quot;Recursos insuficientes para la operación&quot;

**Cuando ocurre:** Durante cualquier etapa

**Causa:** Su entorno carece de CPU, memoria o almacenamiento suficientes

**Soluciones:**

* Compruebe el uso de los recursos del entorno
* Libere recursos limpiando archivos
* Esperar a que los recursos estén disponibles
* Póngase en contacto con el servicio de asistencia si persisten problemas de recursos

## Obtención de ayuda

**Cuándo ponerse en contacto con el soporte técnico:**

Póngase en contacto con el servicio de asistencia de Adobe Commerce Cloud cuando:

* Los mensajes de error no son claros o no tienen detalles suficientes
* Las operaciones de parche fallan constantemente
* Necesita ayuda con la resolución manual de conflictos
* Las comprobaciones de estado fallan, pero la causa no es evidente
* Necesita ayuda con los problemas de sincronización del entorno

**Información que proporcionar:**

Al ponerse en contacto con el servicio de asistencia, proporcione:

* **ID de proyecto** - Su identificador de proyecto de Adobe Commerce Cloud
* **Id. de entorno** - El entorno específico donde ocurrió el problema
* **Id. de operación** - Identificador de operación [!DNL CAPS]
* **Detalles del error** - Completar mensajes de error y registros
* **Pasos para reproducir**: lo que estaba haciendo cuando se produjo el error
* **Intentos anteriores** - Lo que ya ha intentado resolver el problema

### Recursos adicionales

Para obtener información técnica más detallada:

* Revise los registros de errores completos proporcionados con las operaciones fallidas
* Consulte la documentación de Adobe Commerce para obtener instrucciones específicas sobre los parches
* Póngase en contacto con el servicio de asistencia técnica de Adobe Commerce Cloud para problemas específicos del entorno

### Temas relacionados

* [Documentación de Adobe Commerce Cloud](https://experienceleague.adobe.com/es/docs/commerce-cloud-service/user-guide/overview)
* [Guía de instalación de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/overview)
* [Introducción a CAPS](intro.md)
* [Cómo acceder a](access.md)
* [Flujo de trabajo](workflow.md)
* [Prácticas recomendadas](best-practices.md)
