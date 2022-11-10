---
title: Prevención y respuesta de un incidente de seguridad
description: Obtenga información sobre las prácticas recomendadas para evitar y responder a incidentes de seguridad en su proyecto de infraestructura en la nube de Adobe Commerce.
role: Admin, Developer, Leader, User
feature-set: Commerce
feature: Best Practices
source-git-commit: bb9b8cc9993a70ea50667f08c8260759ab0f91dc
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Prácticas recomendadas para ayudar a prevenir y responder a un incidente de seguridad

La seguridad de Adobe Commerce opera en un [Responsabilidad compartida](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) modelo. Es clave para comprender de qué son responsables el Adobe y sus equipos técnicos. A continuación, resumimos [Prácticas recomendadas de seguridad](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf) para garantizar que su proyecto tenga los mejores controles de seguridad y cómo responder mejor a un incidente de seguridad.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube

## Responder a un incidente

Hay muchas consideraciones a la hora de responder a un incidente de seguridad. Si cree que ha encontrado un incidente de seguridad reciente para su proyecto de infraestructura en la nube de Adobe Commerce, es importante auditar todos los controles de cuentas de usuario de administrador, habilitar controles avanzados de autenticación multifactor (MFA), conservar los registros críticos y revisar las actualizaciones de seguridad para su versión de Adobe Commerce.

A continuación se describen más recomendaciones. Pueden ayudar a evitar el acceso no autorizado e iniciar el proceso para un análisis de incidentes más amplio.

## Cómo evitar incidentes de seguridad

Siga estas prácticas recomendadas de seguridad para evitar de forma proactiva incidentes de seguridad que afecten a sus sitios y tiendas de Adobe Commerce:

- [Habilitar 2FA para acceso de administrador](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
La autenticación de dos factores se utiliza ampliamente, y es común generar códigos de acceso para diferentes sitios web en la misma aplicación. Esto garantiza que solo usted pueda iniciar sesión en su cuenta de usuario. Si pierde la contraseña o un bot la adivina, la autenticación de dos factores añade una capa de protección.
- [Habilitar MFA para acceso SSH](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
Cuando MFA está habilitado en un proyecto, todos los Adobe Commerce de cuentas de infraestructura en la nube con acceso SSH deben seguir un flujo de trabajo de autenticación que requiera un código de autenticación de dos factores (2FA), o un token de API y un certificado SSH para acceder al entorno.
- Actualice a la última versión de Adobe Commerce.
Adobe publica parches funcionales y de seguridad para cada versión compatible de Adobe Commerce.
- Configure y utilice un [URL de administración no predeterminada](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
Adobe recomienda usar una URL de administración personalizada y única en lugar de la predeterminada `admin` o un término común como *backend*. Aunque este cambio de configuración no protege directamente su sitio de un actor incorrecto determinado, puede reducir la exposición a scripts que intentan obtener acceso no autorizado.
- Impida que los valores de configuración se editen o actualicen en el administrador mediante la función  [`bin/magento config:set` CLI con el comando `lock env` opción de configuración](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). Esta opción bloquea el valor de configuración para que no se pueda editar en Admin o evita cambios en una configuración que ya está bloqueada. Al utilizar esta opción, los cambios de configuración se escriben en la variable `<Commerce base dir>/app/etc/env.php` archivo.
- Configure y ejecute el [Herramienta de análisis de seguridad de Adobe Commerce](https://docs.magento.com/user-guide/magento/security-scan.html).
El análisis de seguridad mejorado le permite supervisar cada uno de sus sitios de Adobe Commerce, incluido el PWA, para detectar riesgos de seguridad conocidos y malware, y recibir actualizaciones de parches y notificaciones de seguridad.
- [Revisar y actualizar el acceso de los usuarios administradores](https://docs.magento.com/user-guide/system/permissions-users-all.html) y [configuración de seguridad](https://docs.magento.com/user-guide/stores/security-admin.html).
   - Recomendamos quitar las cuentas antiguas, no utilizadas o sospechosas y girar las contraseñas de todos los usuarios administradores.
   - Revise y actualice la Configuración de seguridad avanzada&lt; de su proyecto. La configuración de seguridad del administrador le permite agregar una clave secreta a las direcciones URL, requerir que las contraseñas distingan entre mayúsculas y minúsculas y limitar la duración de las sesiones del administrador, incluida la duración de las contraseñas, y el número de intentos de inicio de sesión que se pueden realizar antes de que la cuenta de usuario del administrador esté bloqueada. Para aumentar la seguridad, puede configurar la duración de la inactividad del teclado antes de que caduque la sesión actual y requerir que el nombre de usuario y la contraseña distingan entre mayúsculas y minúsculas.
- Auditar Adobe Commerce en [usuarios del proyecto en la nube](https://devdocs.magento.com/cloud/project/user-admin.html).
Se recomienda eliminar las cuentas antiguas, no utilizadas o sospechosas y solicitar a los usuarios que cambien sus contraseñas.
- Auditoría [Claves SSH](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) para Adobe Commerce en infraestructura de nube.
Recomendamos revisar, eliminar y rotar claves SSH.
- Implemente la Lista de control de acceso (ACL) para administradores.
Puede utilizar una lista de ACL de borde flexible en combinación con una [Fragmento de código VCL](https://devdocs.magento.com/cloud/cdn/fastly-vcl-allowlist.html#vcl) para filtrar las solicitudes entrantes y permitir el acceso por dirección IP a Admin.

## Analizar un incidente

El primer paso del análisis de incidentes es reunir tantos hechos como sea posible, tan rápido como sea posible. Recopilar información sobre el incidente puede ayudarle a determinar la causa potencial del incidente. Adobe Commerce proporciona las herramientas siguientes para ayudarle con el análisis de incidentes.

- [Registros de acciones del administrador de auditoría](https://docs.magento.com/user-guide/system/action-log-report.html).
El informe Registros de acción muestra un registro detallado de todas las acciones de administración que están habilitadas para el registro. Cada registro lleva una marca de hora y registra la dirección IP y el nombre del usuario. El detalle del registro incluye los datos de usuario administradores y los cambios relacionados que se realizaron durante la acción.
- Analizar eventos con la variable [Herramienta Observación para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
La herramienta Observación para Adobe Commerce le permite analizar problemas complejos para ayudar a identificar causas profundas. En lugar de rastrear datos dispares, puede dedicar su tiempo a correlacionar eventos y errores para obtener una perspectiva más profunda de las causas de los cuellos de botella en el rendimiento.
La herramienta pretende ofrecer una vista clara de algunos de los problemas potenciales del sitio para ayudarle a identificar la causa principal y mantener el rendimiento de los sitios de forma óptima. Haga clic en el vínculo a la documentación de la herramienta Observación para Adobe Commerce que aparece más arriba para acceder a la documentación de la herramienta. Hay una sección en la documentación que detalla toda la información que se puede encontrar en la **Seguridad** pestaña .
- Analizar registros con [Nuevos registros de reliquia](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). Adobe Commerce en infraestructura en la nube Los proyectos Pro incluyen el [Nuevos registros de reliquia](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) servicio. El servicio está preconfigurado para acumular todos los datos de registro de los entornos de ensayo y producción para mostrarlos en un panel de administración de registros centralizado.
Puede utilizar el servicio New Relic Logs para completar las siguientes tareas:
   - Uso [Nuevas consultas de reliquia](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) para buscar datos de registro agregados.
   - Visualice los datos de registro a través de la aplicación New Relic Logs .

## Información adicional

- [Marco de análisis de causa raíz](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
