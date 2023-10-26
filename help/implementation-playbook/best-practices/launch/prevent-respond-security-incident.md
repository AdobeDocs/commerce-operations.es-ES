---
title: Prevención y respuesta a un incidente de seguridad
description: Conozca las prácticas recomendadas para evitar y responder a los incidentes de seguridad en su proyecto de infraestructura en la nube de Adobe Commerce.
role: Admin, Developer, Leader, User
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: 19ff1fee74e3c5ece13da49648252b32e549eafd
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 0%

---

# Prácticas recomendadas para ayudar a prevenir un incidente de seguridad y responder a él

La seguridad de Adobe Commerce funciona con un [Responsabilidad compartida](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) modelo. Es fundamental comprender de qué son responsables el Adobe y los equipos técnicos. El siguiente artículo resume las prácticas recomendadas de seguridad para garantizar que el proyecto cuenta con los mejores controles de seguridad y que puede planificar la mejor respuesta a los incidentes de seguridad.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube

## Responder a un incidente

Hay muchas consideraciones a la hora de responder a un incidente de seguridad. Si cree que ha encontrado un incidente de seguridad reciente en su proyecto de Adobe Commerce en la nube, es importante auditar el acceso de todos los administradores a la cuenta de usuario, habilitar los controles avanzados de autenticación multifactor (MFA), conservar los registros críticos y revisar las actualizaciones de seguridad de su versión de Adobe Commerce.

A continuación se detallan más recomendaciones. Pueden ayudar a evitar el acceso no autorizado e iniciar el proceso para un análisis posterior de los incidentes.

## Cómo evitar incidentes de seguridad

Siga estas prácticas recomendadas de seguridad para evitar de forma proactiva incidentes de seguridad que afecten a los sitios y tiendas de Adobe Commerce:

- [Habilitar 2FA para acceso de administrador](https://docs.magento.com/user-guide/stores/security-two-factor-authentication.html).
La autenticación de doble factor se utiliza ampliamente y es común generar códigos de acceso para diferentes sitios web en la misma aplicación. Esto garantiza que solo usted pueda iniciar sesión en su cuenta de usuario. Si pierde la contraseña o un bot la adivina, la autenticación de doble factor agrega una capa de protección.
- [Habilitar MFA para acceso SSH](https://devdocs.magento.com/cloud/project/project-enable-mfa-enforcement.html).
Cuando MFA está habilitado en un proyecto, todas las cuentas de infraestructura en la nube de Adobe Commerce con acceso SSH deben seguir un flujo de trabajo de autenticación que requiera un código de autenticación de doble factor (2FA) o un token de API y un certificado SSH para acceder al entorno.
- Actualice a la última versión de Adobe Commerce.
El Adobe publica parches funcionales y de seguridad para cada versión compatible de Adobe Commerce.
- Configuración y uso de un [URL de administración no predeterminada](https://docs.magento.com/user-guide/stores/store-urls-custom-admin.html).
El Adobe recomienda utilizar una URL de administrador única y personalizada en lugar de la predeterminada `admin` o un término común como *servidor*. Aunque este cambio de configuración no protege directamente el sitio de un actor incorrecto determinado, puede reducir la exposición a scripts que intentan obtener acceso no autorizado.
- Impida que los valores de configuración se editen o actualicen en el Administrador mediante el  [`bin/magento config:set` Comando de CLI con `lock env` opción de configuración](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configuration-management/set-configuration-values.html#set-configuration-values-that-cannot-be-edited-in-the-admin). Esta opción bloquea el valor de configuración para que no se pueda editar en el Administrador o impide que se realicen cambios en una configuración que ya está bloqueada. Cuando se utiliza esta opción, los cambios de configuración se escriben en la variable `<Commerce base dir>/app/etc/env.php` archivo.
- Configure y ejecute el [Herramienta de análisis de seguridad de Adobe Commerce](https://docs.magento.com/user-guide/magento/security-scan.html).
El análisis de seguridad mejorado le permite supervisar cada uno de sus sitios de Adobe Commerce, incluido el PWA, para detectar riesgos de seguridad y malware conocidos, así como recibir actualizaciones de parches y notificaciones de seguridad.
- [Revisar y actualizar el acceso de usuario administrador](https://docs.magento.com/user-guide/system/permissions-users-all.html) y [configuración de seguridad](https://docs.magento.com/user-guide/stores/security-admin.html).
   - Elimine las cuentas antiguas, no utilizadas o sospechosas y gire las contraseñas de todos los usuarios administradores.
   - Revise y actualice la Configuración de seguridad avanzada&lt; para su proyecto. La configuración de seguridad de administración le permite agregar una clave secreta a las direcciones URL, requerir que las contraseñas distingan entre mayúsculas y minúsculas y limitar la duración de las sesiones de administración, incluida la duración de las contraseñas, y el número de intentos de inicio de sesión permitidos antes de que se bloquee la cuenta de usuario de administrador. Para aumentar la seguridad, puede configurar la duración de la inactividad del teclado antes de que caduque la sesión actual y requerir que el nombre de usuario y la contraseña distingan entre mayúsculas y minúsculas.
- Auditar Adobe Commerce en [usuarios de proyectos en la nube](https://devdocs.magento.com/cloud/project/user-admin.html).
Elimine las cuentas antiguas, no utilizadas o sospechosas y solicite a los usuarios que cambien sus contraseñas.
- Auditoría [Claves SSH](https://devdocs.magento.com/cloud/before/before-workspace-ssh.html) para Adobe Commerce en la infraestructura en la nube.
Revise, elimine y gire las claves SSH.
- Implemente la Lista de control de acceso (ACL) para los administradores.
Puede filtrar las solicitudes entrantes y configurar el acceso de administrador por dirección IP implementando una lista de ACL de Fastly Edge en combinación con una lista personalizada [Fragmento de código VCL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-allowlist.html).

## Análisis de un incidente

El primer paso del análisis de incidentes es recopilar tantos hechos como sea posible y con la mayor rapidez posible. La recopilación de información relacionada con el incidente puede ayudarle a determinar la causa potencial del mismo. Adobe Commerce proporciona las herramientas siguientes para ayudarle con el análisis de incidentes.

- [Registros de acciones de administración de auditoría](https://docs.magento.com/user-guide/system/action-log-report.html).
El informe Registros de acciones muestra un registro detallado de todas las acciones de administración habilitadas para el registro. Cada registro tiene una marca de hora y registra la dirección IP y el nombre del usuario. El detalle del registro incluye los datos de usuario de administración y los cambios relacionados que se realizaron durante la acción.
- Analizar eventos con [Herramienta Observación para Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/tools/observation-for-adobe-commerce/intro.html?lang=en).
La herramienta Observación para Adobe Commerce le permite analizar problemas complejos para ayudar a identificar causas básicas. En lugar de rastrear datos dispares, puede dedicar su tiempo a correlacionar eventos y errores para obtener información más detallada sobre las causas de los cuellos de botella del rendimiento.
La herramienta pretende ofrecer una visión clara de algunos de los posibles problemas del sitio para ayudarle a identificar la causa raíz y mantener el rendimiento óptimo de los sitios. Haga clic en el vínculo a la documentación de la herramienta Observación para Adobe Commerce anterior para acceder a la documentación de la herramienta. Hay una sección en la documentación de que detalla toda la información que se puede encontrar en la **Seguridad** pestaña.
- Analizar registros con [Registros de New Relic](https://devdocs.magento.com/cloud/project/new-relic.html#new-relic-logs). Los proyectos Pro de Adobe Commerce en infraestructura en la nube incluyen [Registros de New Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/get-started/introduction-new-relic-logs) servicio. El servicio está preconfigurado para agregar todos los datos de registro de los entornos de ensayo y producción y mostrarlos en un panel de administración de registros centralizado.
Puede utilizar el servicio Registros de New Relic para completar las siguientes tareas:
   - Uso [Consultas de New Relic](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) para buscar datos de registro agregados.
   - Visualice los datos de registro mediante la aplicación New Relic Logs.

## Información adicional

- [Marco de análisis de causa raíz](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
