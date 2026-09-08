---
title: Guía de solución de problemas de [!DNL Adobe Commerce Patching Automation]
description: Solucionar problemas comunes y mensajes de error en  [!DNL Adobe Commerce Patching Automation]
source-git-commit: f2b9ba118bfe4982a67ec5041141e5ee7548fc4d
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---

# [!DNL Adobe Commerce Patching Automation] guía de solución de problemas

Al usar [!DNL Patching Automation] para operaciones de revisión, puede encontrar mensajes de error y problemas que pueden impedir la aplicación o reversión de revisión correcta. Esta guía proporciona soluciones para los problemas más comunes.

## Pasos rápidos de solución de problemas

### Si falla la operación de parche

* Compruebe el estado de la operación para comprender qué fase falló
* Revisar mensajes de error por motivos de error específicos
* Examinar los registros de errores para obtener detalles técnicos
* Siga las soluciones proporcionadas en esta guía

>[!TIP]
>
>En Cloud Console, los registros de implementación están disponibles en la fuente de actividades del proyecto, incluso después de eliminar un entorno de integración temporal.

### Duración de operaciones de parche

En la mayoría de los entornos, la siguiente cronología describe la duración de las operaciones de parche, pero puede tardar más según el tamaño y la complejidad del entorno:

* **Procesamiento previo:** de 2 a 5 minutos
* **Parches:** de 5 a 15 minutos
* **Procesamiento posterior:** de 10 a 40 minutos
* **Total:** 15-60 minutos

>[!NOTE]
>
>El tiempo posterior al procesamiento se calcula a partir del historial de implementación del entorno, por lo que puede quedar fuera del intervalo anterior en el caso de entornos de implementación inusualmente rápida o lenta.

### Cancelación de un parche en curso

>[!WARNING]
>
>Una vez que se inicia una operación de parche, debe permitirse que se complete. El sistema incluye procedimientos de limpieza que se ejecutan incluso si las operaciones fallan. Interrumpir el proceso puede dejar el entorno en un estado incoherente.

## Mensajes de éxito comunes

* **&quot;Trabajo completado correctamente&quot;** - El parche se aplicó/revirtió correctamente sin ningún problema.

* **&quot;Se ha aplicado el parche&quot;** - Está intentando aplicar un parche que ya se ha aplicado. El sistema detectó que el parche ya está presente en su entorno. No es necesario realizar ninguna acción.

* **&quot;El parche se ha revertido&quot;** - Está intentando revertir un parche que ya se ha revertido. El sistema detectó que el parche no se está aplicando actualmente. No es necesario realizar ninguna acción.

## Mensajes de error comunes y soluciones

>[!NOTE]
>
>No todos los errores posibles se enumeran a continuación. Los errores no enumerados durante la comprobación o validación preliminares aparecen como errores genéricos. Póngase en contacto con el soporte técnico con el texto de error exacto. Durante la aplicación de parches, un error no anticipado muestra directamente el mensaje de error subyacente sin procesar en lugar de la reserva genérica.

### Errores de preparación del entorno

#### &quot;La última implementación no se realizó correctamente. Asegúrese de que el entorno sea estable antes de aplicar o revertir parches&quot;.

**Cuando esto sucede:** Al comienzo de la comprobación preliminar, antes de cualquier validación específica del parche

**Causa:** La implementación más reciente del entorno de destino no se completó correctamente

**Solución:** Vuelva a implementar el entorno de destino y confirme que la implementación se completa correctamente (compruebe su registro de implementación en la consola de Cloud) antes de volver a intentar la operación de revisión.

### Errores de aplicación de parche

#### &quot;No se puede aplicar el parche porque [!DNL Patching Automation] ha detectado estos problemas con el código base o el archivo de parche&quot;

**Cuando se produce:** Durante la comprobación preliminar

**Causa:** El parche entra en conflicto con la base de código actual O hay un problema con el propio parche

**Soluciones:**

* Revise los registros de errores detallados proporcionados para identificar si se trata de un problema de código base o de parche
* Compruebe si hay personalizaciones en conflicto en el código
* Verifique que el parche sea compatible con su versión de Adobe Commerce
* Considere la posibilidad de resolver conflictos manualmente o póngase en contacto con el soporte técnico

#### &quot;Está intentando revertir un parche que no se aplicó a través de [!DNL Patching Automation]. Es probable que el parche se haya aplicado manualmente&quot;.

**Cuando se produce:** Durante las operaciones de reversión

**Causa:** Está intentando revertir un parche que no se aplicó mediante [!DNL Patching Automation]

**Solución:** Use el mismo método que se usó para aplicar el parche originalmente o póngase en contacto con el soporte técnico para obtener ayuda manual

### Errores de entorno y validación

#### &quot;El entorno no está sincronizado con el elemento principal&quot;

**Cuando esto sucede:** Durante la validación, en la comprobación de sincronización previa a la combinación, antes de que el entorno de integración se combine en el entorno de destino

**Causa:** El entorno de integración difiere del entorno principal, normalmente porque el entorno de destino cambió mientras se estaba probando el parche

**Soluciones:**

* Vuelva a intentar la operación de parche una vez que el entorno de destino esté estable
* Evite realizar cambios en el entorno de destino mientras se lleva a cabo una operación de parche
* Póngase en contacto con el servicio de asistencia si persisten problemas de sincronización

#### &quot;Error de verificación posterior a la combinación: los entornos no están sincronizados después de la combinación&quot;.

**Cuando esto sucede:** Durante la validación, después de que el entorno de integración ya se haya combinado en el entorno de destino

**Causa:** El código del código de los dos entornos no coincide después de la combinación, normalmente un retraso temporal de propagación de la API Platform.sh en lugar de un conflicto real

**Soluciones:**

* Espere unos minutos y vuelva a comprobar el estado del entorno. Este problema suele resolverse automáticamente
* Si los entornos siguen sin coincidir después de unos minutos, póngase en contacto con el Soporte técnico de Adobe.

#### &quot;No se puede crear el trabajo de parche en el entorno de producción cuando cron está habilitado y el modo de mantenimiento está deshabilitado. Habilite el modo de mantenimiento y deshabilite los trabajos cron antes de aplicar los parches&quot;.

**Cuando esto sucede:** Durante la comprobación preliminar de entornos de producción

**Causa:** El entorno de producción no cumple las condiciones de seguridad requeridas

**Soluciones:**

* Habilite el modo de mantenimiento para su tienda de producción
* Deshabilitar los trabajos cron en el entorno de producción
* Compruebe que se cumplen ambas condiciones antes de volver a intentarlo
* También puede seleccionar la casilla de verificación de anulación en la interfaz de usuario para omitir estas comprobaciones y continuar de todos modos. Utilice únicamente la opción de anulación si comprende el riesgo de aplicar parches a la producción sin esas garantías

>[!IMPORTANT]
>
> [!DNL Patching Automation] no habilita automáticamente el modo de mantenimiento ni deshabilita los trabajos cron. Complete estos procedimientos manualmente.

#### &quot;La operación de revisión se completó, pero la comprobación de estado del entorno falló. Esto indica posibles problemas con la implementación. Revise el estado del entorno y considere la posibilidad de revertir el cambio&quot;.

**Cuando esto sucede:** Después de aplicar el parche o de la reversión, durante la validación

**Causa:** El parche se aplicó o se revirtió correctamente, pero la comprobación de estado posterior no se realizó correctamente

**Soluciones:**

* Pruebe los flujos de trabajo de tienda y de cierre de compra y administración críticos para confirmar si los clientes se ven afectados
* En Cloud Console, revise el estado del entorno e inspeccione los registros de aplicación e implementación en la fuente de proyectos **Activity**. Busque errores asociados con la operación o implementación de parches.
* Déclencheur una reimplementación manual para determinar si un problema de implementación o infraestructura transitorio causó el error de comprobación de estado.
* Si el problema persiste, revierta el parche. Si [!DNL Patching Automation] administra el parche y la operación está disponible, seleccione [!UICONTROL Revert]. Si la revisión es una revisión personalizada en el directorio `m2-hotfixes`, elimine el archivo de revisión del repositorio del proyecto. Confirme e inserte el cambio y, a continuación, vuelva a implementar el entorno.
* Si el problema persiste, póngase en contacto con el Soporte técnico de Adobe. Incluya la siguiente información en la solicitud de soporte: ID de proyecto de soporte, ID de entorno y este mensaje exacto: la última operación no se completó correctamente, por lo que el soporte debe confirmar el estado del entorno.

### Errores de autenticación y acceso

#### &quot;Acceso denegado&quot;

**Cuando ocurre:** Cuando su cuenta carece de los permisos necesarios durante la creación o el acceso al entorno

**Causa:** Su cuenta de usuario carece de los permisos necesarios

**Soluciones:**

* Compruebe la función de usuario y los permisos
* Póngase en contacto con el administrador del sistema
* Compruebe que tiene permisos de administración del entorno
* Asegúrese de que tiene permisos de implementación

### Errores de integración de GitHub

#### &quot;No hay credenciales de Git disponibles para el proveedor &quot;github&quot;. Instale la aplicación GitHub de automatización de parches para este repositorio&quot;

**Cuando esto sucede:** Durante las operaciones de revisión de los proyectos conectados a GitHub

**Causa:** La aplicación GitHub [!DNL Patching Automation] no está instalada en el repositorio

**Solución:** Siga los pasos de [Configurar la integración de GitHub para [!DNL Patching Automation]](github-integration.md)

#### &quot;Error de solicitud de API de GitHub&quot;

**Cuando esto sucede:** Durante las operaciones de revisión para proyectos conectados a GitHub

**Causa:** Un problema temporal impidió que el servicio se conectara a GitHub

**Solución:** Espere unos minutos y vuelva a intentar la operación. Si el error persiste, ponte en contacto con el [servicio de asistencia en Adobe Commerce Cloud](https://experienceleague.adobe.com/home?lang=es#support)

#### &quot;Entorno no creado dentro del tiempo de espera&quot; (proyecto conectado a GitHub)

**Cuando ocurre:** Durante la creación del entorno de integración

**Causa:** La integración de GitHub del proyecto tiene deshabilitada la opción `fetch-branches`. Como resultado, las ramas temporales insertadas por el servicio no se sincronizan y el entorno de integración nunca se crea.

**Solución:** Habilite la opción [`fetch-branches` de la integración](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration) y vuelva a intentar la operación. Consulte [Configurar la integración de GitHub para [!DNL Patching Automation]](github-integration.md).

### Errores de activación del entorno

#### &quot;No se puede activar el entorno de integración&quot;.

**Cuando esto sucede:** Cuando [!DNL Patching Automation] no puede activar el entorno de integración temporal necesario para probar el parche de forma segura.

**Causa:** depende de los detalles adicionales que se muestran junto con el error:

**Si los detalles mencionan paquetes de Compositor o Adobe Commerce:**

* Inicie sesión en [https://account.magento.com/customer/account/login](https://account.magento.com/customer/account/login) (o pida al propietario de la cuenta que lo haga) y confirme que su cuenta tiene acceso a la base de código empresarial de Commerce.
* Compruebe que las claves de autenticación pública y privada del Compositor del proyecto son correctas. Consulte [Claves de autenticación](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/authentication-keys).
* Confirme que el paquete llamado en el mensaje de error está disponible para su versión de Commerce. Ver [paquetes de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-operations/release/packages/adobe-commerce).

**Si los detalles mencionan espacios o recursos del entorno:**

* En Cloud Console, abra la descripción general del proyecto y revise los entornos y sus estados. Desactivar o eliminar cualquier entorno de integración que no se utilice: seleccione el entorno. Ir a **[!UICONTROL Settings]>[!UICONTROL General]**. Para desactivar el entorno, establezca el estado en inactivo.

  También puede usar la CLI: `magento-cloud environment:list` / `magento-cloud environment:deactivate <environment-name>`
* Compruebe que el proyecto tiene recursos suficientes, por ejemplo espacio en disco.
* Asegúrese de que el entorno principal sea estable (sin implementación activa) en el momento de la operación.
* Póngase en contacto con el Soporte técnico de Adobe si necesita aumentar el límite de entornos.

**Por cualquier otra causa:** revise los registros de error detallados en la interfaz de usuario de automatización de parches o póngase en contacto con el servicio de soporte técnico con el texto exacto del error.

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
* **Id. de operación** - Identificador de operación [!DNL Patching Automation]
* **Detalles del error** - Completar mensajes de error y registros
* **Pasos para reproducir**: lo que estaba haciendo cuando se produjo el error
* **Intentos anteriores** - Lo que ya ha intentado resolver el problema

### Recursos adicionales

Para obtener información técnica más detallada:

* Revise los registros de errores completos proporcionados con las operaciones fallidas
* Consulte la documentación de Adobe Commerce para obtener instrucciones específicas sobre los parches
* Póngase en contacto con el servicio de asistencia técnica de Adobe Commerce Cloud para problemas específicos del entorno

### Temas relacionados

* [Documentación de Adobe Commerce Cloud](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/overview)
* [Guía de instalación de Adobe Commerce](/help/installation/overview.md)
* [Introducción a la automatización de parches](intro.md)
* [Cómo acceder a](access.md)
* [Resumen de flujo de trabajo](workflow.md)
* [Integración de GitHub](github-integration.md)
* [Prácticas recomendadas](best-practices.md)
