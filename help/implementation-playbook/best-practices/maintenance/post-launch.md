---
title: Asistencia y mantenimiento posteriores al lanzamiento
description: Garantice el rendimiento y la seguridad óptimos de su tienda Adobe Commerce con nuestras completas prácticas recomendadas de mantenimiento y asistencia tras el lanzamiento.
role: Admin, User, Developer
feature: Best Practices
source-git-commit: bcb45d53aba4a73a5730989e9bf29ccba6e9bf35
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 0%

---


# Soporte y mantenimiento posteriores al lanzamiento para Adobe Commerce

La asistencia y el mantenimiento posteriores al lanzamiento son esenciales para garantizar que su tienda Adobe Commerce funcione sin problemas, funcione bien, siga siendo segura y siga cumpliendo con sus objetivos comerciales. Esta fase incluye monitorización continua, optimización, corrección de errores, actualizaciones y asistencia al usuario. Las siguientes secciones desglosan **compatibilidad posterior al inicio** en categorías clave:

## Monitorización regular del sitio y optimización del rendimiento

### Monitorización del rendimiento

- **Pruebas de carga y velocidad del sitio**: Adobe Commerce puede consumir muchos recursos, por lo que la supervisión regular del rendimiento es crucial.

   - **Herramientas para usar**: Todos los proyectos de infraestructura en la nube de Adobe Commerce incluyen acceso a New Relic, que ayuda a supervisar el rendimiento e investigar eventos dentro de la aplicación y la infraestructura en la nube de Commerce. Las herramientas adicionales incluyen Google PageSpeed Insights y GTMetrix.

   - **Qué monitorizar**: estos son los elementos principales que se deben monitorizar para Adobe Commerce en la infraestructura en la nube:

      - **Notificaciones de estado**: Alertas para el espacio en disco y el estado del entorno.

      - **Observación**: Supervisión completa que combina datos de registro de múltiples fuentes para una administración eficaz del sitio.

      - **Servicio de New Relic**: supervisa el rendimiento en ensayo y producción, centrándose en las métricas clave.

      - **Directiva de alertas administradas**: Rastrea métricas con umbrales predefinidos para notificaciones de déclencheur por problemas de infraestructura o aplicación que afectan el rendimiento.

  >[!TIP]
  >
  >Consulte [supervisión del rendimiento](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) en la _Guía de Cloud_.


- **Optimizando el rendimiento de la base de datos**: Para optimizar el rendimiento de la base de datos en Adobe Commerce Cloud, implemente lo siguiente:

   - **Supervisar y optimizar consultas MySQL**: identifique y resuelva consultas de ejecución lenta, lo que se puede hacer con los comandos SHOW FULL PROCESSLIST y EXPLAIN de MySQL. Para configuraciones más complejas, los usuarios de arquitectura Pro pueden utilizar Percona Toolkit para analizar los registros de consultas en busca de problemas de rendimiento.

   - **Administración de índices**: Asegúrese de que cada tabla tiene una clave principal y quite los índices duplicados, ya que pueden reducir la eficacia y provocar conflictos durante las escrituras simultáneas.

   - **Optimización del trabajo Cron**: los trabajos Cron deben programarse durante las horas de menor actividad para minimizar el impacto en el rendimiento, especialmente si las tareas en segundo plano como la indexación son frecuentes.

  >[!TIP]
  >
  >Consulte las [prácticas recomendadas para resolver los problemas de rendimiento de la base de datos](resolve-database-performance-issues.md).

- **Supervisar CDN**: Para supervisar el rendimiento de Fastly CDN en Adobe Commerce Cloud, puede realizar las siguientes acciones:

   - **Aproveche New Relic para supervisar**: Adobe Commerce ofrece New Relic para supervisar rápidamente el rendimiento y otras métricas en los entornos de ensayo y producción. Esta herramienta proporciona perspectivas sobre el estado del servidor, el almacenamiento en caché de CDN y las solicitudes de red a lo largo del tiempo, lo que ayuda a identificar patrones y optimizar la configuración de CDN.

   - **Análisis de registros de Fastly**: En los proyectos de Adobe Commerce Cloud Pro, puede usar Registros de New Relic para revisar y analizar los datos de registro de Fastly en CDN y WAF para rastrear tendencias de rendimiento, eventos de seguridad y diagnosticar errores o problemas de latencia.

   - **Usar comandos cURL**: ejecute comandos cURL con encabezados específicos de Fastly para inspeccionar el estado de caché del sitio. Los encabezados de respuesta clave incluyen `X-Cache` (HIT/MISS), `Fastly-Module-Enabled`, `Fastly-Magento-VCL-Uploaded` y `Cache-Control` para verificar el almacenamiento en caché y el estado del módulo. Adobe proporciona comandos cURL de ejemplo para los entornos de ensayo y producción.

   - **Compruebe la información del encabezado**: Encabezados de Inspect como `Cache-Control`, `Pragma` y `X-Magento-Tags` para confirmar el comportamiento de almacenamiento en caché y la administración de etiquetas adecuados en el contenido almacenado en caché. Los valores de encabezado adecuados indican si las configuraciones de almacenamiento en caché se aplican de forma eficaz en toda la CDN.

   - **Depuración y prueba rápidas**: Use la característica de depuración de Fastly para identificar y solucionar problemas con las tasas de aciertos y errores de caché, la lógica de almacenamiento en caché o las respuestas de encabezado incorrectas, que pueden señalar a problemas de configuración o desalineación con las reglas de almacenamiento en caché esperadas.

Estos pasos de monitorización ayudan a mantener un rendimiento de CDN óptimo y a abordar los problemas que afectan a la velocidad y fiabilidad del sitio.

>[!TIP]
>
>Consulte [Información general sobre los servicios de Fastly](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) en la _Guía de Cloud_.

#### Supervisión regular de la seguridad

Para mantener una monitorización de seguridad regular en Adobe Commerce Cloud, Adobe recomienda un enfoque multifacético que implique un análisis continuo, un registro y prácticas de seguridad proactivas. Estas son algunas acciones principales para garantizar una seguridad continua:

- **Análisis de seguridad**: Use la herramienta de análisis de seguridad de Adobe para detectar vulnerabilidades y malware conocidos en los sitios de Commerce. Esta herramienta proporciona alertas para posibles riesgos de seguridad y problemas de cumplimiento.

- **Mantenimiento regular de parches y actualizaciones**: aplique los parches y las actualizaciones de seguridad de Adobe a medida que estén disponibles. La actualización a la última versión de Adobe Commerce garantiza las últimas defensas contra las amenazas.

- **Supervisión de auditoría y registro**: aproveche herramientas como New Relic Logs (disponibles para proyectos Pro) para centralizar y analizar los registros de seguridad de los entornos de ensayo y producción, lo que aumenta la visibilidad de posibles problemas e infracciones de seguridad.

- **Administración de cuentas y acceso**: audite con regularidad las cuentas de usuario y administrador para eliminar cualquier cuenta no autorizada u obsoleta. Reforzar los controles de acceso con autenticación multifactor (MFA) para los usuarios administradores.

- **Firewall de aplicaciones web (WAF)**: utilice el Fastly WAF integrado para detectar y mitigar las amenazas de patrones de tráfico malintencionados, como intentos de extracción de datos no autorizados.

- **Seguridad de código y extensión personalizados**: Proteja cualquier código personalizado o extensión de terceros realizando auditorías de código regulares y limitando las extensiones a las que el Adobe ha vetado.

>[!TIP]
>
>Consulte [Seguridad](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security) en la _Guía de sistemas de administración_.

#### Registro y monitorización de errores

Para supervisar el registro de errores en Adobe Commerce Cloud, Adobe proporciona varias herramientas y prácticas para una solución de problemas y una administración del rendimiento eficaces:

- **Agregación de registros con New Relic**: New Relic recopila y centraliza registros de aplicaciones de Adobe Commerce, incluidos registros relacionados con la infraestructura, CDN y WAF. Esta configuración permite realizar un seguimiento de errores simplificado, crear paneles y registros de consultas para obtener información más detallada sobre el rendimiento de la aplicación y los problemas. El acceso a los registros de New Relic permite buscar y filtrar registros por varios atributos para diagnosticar problemas rápidamente.

- **Tipos de registro de errores**: Los registros de errores clave en Adobe Commerce Cloud incluyen `cloud.log`, que contiene comentarios sobre la implementación, y `cloud.error.log`, que registra errores y advertencias sobre la implementación. Otros registros específicos para la depuración incluyen `debug.log`, `system.log` y `exception.log`, cada uno de los cuales cumple diferentes funciones en el seguimiento de errores y eventos en la plataforma Commerce.

- **Registro personalizado con Monolog**: Adobe Commerce admite el registro personalizado mediante Monolog, que permite a los desarrolladores dirigir los mensajes de registro a varios destinos, como archivos, bases de datos e incluso alertas. Esta flexibilidad resulta útil para crear estrategias de registro avanzadas que satisfagan las diferentes necesidades de monitorización en entornos de desarrollo y producción.

- **Supervisión de excepciones con la herramienta de análisis de todo el sitio**: la herramienta de análisis de todo el sitio ayuda a supervisar y administrar los registros de excepciones e identifica los problemas recurrentes en los eventos de implementación y aplicación. Esta herramienta destaca problemas frecuentes, lo que facilita la priorización y la resolución de problemas críticos que afectan al rendimiento.

>[!TIP]
>
>Para obtener más información sobre las prácticas de registro y seguimiento de errores en Adobe Commerce Cloud, consulte [administración de registros de New Relic](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management) y [supervisión de excepciones](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/exceptions).

### Seguridad y actualizaciones

#### Revisiones y actualizaciones de seguridad

Para mantenerse actualizado y garantizar la seguridad de su sistema Adobe Commerce Cloud, estas son algunas prácticas clave para monitorizar los parches y las actualizaciones de seguridad:

- **Suscribirse a las alertas de seguridad de Adobe Commerce**: manténgase informado sobre las vulnerabilidades de seguridad al [registrarse para recibir notificaciones del Adobe](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security).

- **Comprobar notas de la versión**: revise con regularidad las [notas de la versión de los parches de seguridad](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/security-patches/overview), que están etiquetadas con &quot;-pN&quot; para las versiones (por ejemplo, 2.3.5-p1) y contienen correcciones y mejoras esenciales.

- **Aplicar los parches de seguridad inmediatamente**: Aplique los parches de seguridad tan pronto como estén disponibles. Esto incluye actualizar a las versiones más recientes o aplicar archivos de parche específicos.

- **Usar parches de nube**: Para Adobe Commerce Cloud, los parches de seguridad se pueden agrupar dentro de Cloud Tools Suite. Asegúrese de actualizar el grupo de informes o la versión de Commerce para recibir estas correcciones.

- **Administración automatizada de parches**: Considere la posibilidad de utilizar herramientas como el parche centralizado para [administrar y aplicar parches en varias tiendas automáticamente](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale).

>[!TIP]
>
>Para obtener más información e instrucciones paso a paso sobre cómo aplicar parches y mantener la seguridad, consulte [notas de la versión de parches de seguridad](../../../release/release-notes/security/overview.md) y [Cómo aplicar parches de seguridad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches). También debería revisar [los informes de la Herramienta de análisis en todo el sitio](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access).

#### Conformidad con PCI

Para garantizar la conformidad con PCI en Adobe Commerce Cloud, siga estas prácticas clave:

- **Datos del titular de la tarjeta de Protect**: No almacene nunca los datos del titular de la tarjeta en Adobe Commerce. Si se requiere almacenamiento, utilice métodos cifrados y tokenizados para protegerlo.

- **Use protocolos de transmisión segura**: Transmita siempre los datos de pago a través de protocolos seguros como TLS, con cifrado y administración de claves adecuada.

- **Usar firewall de aplicaciones web (WAF)**: El servicio WAF con tecnología Fastly ayuda a cumplir los requisitos de PCI DSS 6.6 y protege contra vulnerabilidades comunes bloqueando el tráfico malintencionado antes de que llegue a su sitio. Ver más información [aquí](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage) y [aquí](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly-waf-service).

- **Limitar el acceso**: Asegúrate de que solo el personal autorizado tenga acceso a los datos de pago confidenciales y [aplica el control de acceso para reducir el riesgo de exposición](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/planning/payment-processing-storage).

- **Análisis regular de la seguridad**: realice análisis regulares de ASV de PCI y [supervise su entorno](https://experienceleague.adobe.com/en/docs/commerce-operations/security-and-compliance/shared-responsibility) para abordar posibles vulnerabilidades.

>[!TIP]
>
>Para obtener instrucciones más detalladas sobre cómo mantener el cumplimiento de PCI con Adobe Commerce, consulte [prácticas recomendadas para el procesamiento y almacenamiento de pagos](../planning/payment-processing-storage.md).

### Asistencia al usuario y al cliente

#### Configurar

- **Canales de soporte**: Implemente canales de soporte al cliente como:

   - **Chat en vivo**: ofrece soporte de Chat en vivo para recibir ayuda de inmediato. Las soluciones más populares son Zendesk, Intercom y Tidio.

   - **Soporte por correo electrónico**: Use un sistema de tickets de soporte como Freshdesk o Zoho Desk para administrar las consultas de los clientes de manera efectiva.

   - **Soporte telefónico**: Si cuenta con una gran base de clientes, considere la posibilidad de ofrecer soporte telefónico durante el horario laboral.

#### Formación del usuario administrador

- **Formación interna**: Capacite a su personal sobre cómo usar el administrador de Adobe Commerce, procesar pedidos, administrar productos y manejar problemas de servicio al cliente.

- **Documentación**: mantenga una base de conocimientos interna o un manual de usuario para las preguntas más frecuentes (FAQ), la solución de problemas y las tareas más comunes.

#### Optimización de la experiencia del cliente

- **Encuestas y comentarios**: Use las encuestas para recopilar los comentarios de los clientes y optimizar su experiencia. Adobe Commerce admite integraciones con herramientas como SurveyMonkey o Google Forms.

- **Administración de críticas**: administra las críticas de los clientes y las clasificaciones de sus productos. Anime a los clientes felices a dejar reseñas mientras responden adecuadamente a las críticas negativas.

- **Personalization**: Implemente características de personalización como recomendaciones de productos personalizadas o promociones segmentadas.

### Mantenimiento y optimización continuos de la tienda

#### Optimización del motor de búsqueda (SEO)

- **Optimización de contenido**: actualice con regularidad las descripciones de los productos, las publicaciones de blog y las páginas de categorías para que el contenido sea actualizado y relevante para los motores de búsqueda.

- **auditorías de SEO**: realice auditorías de SEO regulares con herramientas como Google Search Console o Screaming Frog para identificar problemas de SEO (por ejemplo, vínculos rotos, falta metadatos, contenido duplicado).

- **Estructura de la dirección URL**: Mantenga una estructura de dirección URL lógica y limpia y asegúrese de que no haya vínculos rotos ni redirecciones.

#### Optimización de la tasa de conversión (CRO)

- **Pruebas A/B**: Ejecute pruebas A/B en diferentes elementos de página, como páginas de productos o procesos de cierre de compra, para mejorar las tasas de conversión.

- **Abandono del carro de compras**: Implemente campañas de correo electrónico de abandono del carro de compras o ventanas emergentes de intención de salida para recuperar las ventas perdidas.

- **Optimización de cierre de compra**: simplifica el proceso de cierre de compra al reducir el número de pasos y ofrecer el cierre de compra de invitado para mejorar las conversiones.

#### Integración de marketing

- **Campañas de correo electrónico**: configure flujos de marketing por correo electrónico automatizados para correos electrónicos de bienvenida, correos electrónicos del carro de compras abandonados y seguimientos posteriores a la compra. Plataformas como Adobe Marketo, Mailchimp o Klaviyo se integran bien con Adobe Commerce.

- **Integración de medios sociales y anuncios**: integra con plataformas como Facebook, Instagram y Google Ads para ejecutar campañas dirigidas y rastrear el rendimiento.

#### Optimización móvil

- **Capacidad de respuesta móvil**: Pruebe con regularidad la capacidad de uso y la capacidad de respuesta móvil del sitio. Dado que el comercio móvil está creciendo, un enfoque que priorice la movilidad es esencial para un éxito continuo.

- **Rendimiento móvil**: Use las herramientas de rendimiento y pruebas de Google compatibles con dispositivos móviles para optimizar la experiencia de su tienda móvil.

### Escala y desarrollo de nuevas funciones

- **Escalado automático para la administración del tráfico**:

   - Adobe Commerce Cloud admite el escalado automático para ajustar dinámicamente los recursos del servidor (por ejemplo, los nodos web) en función de las demandas de tráfico en tiempo real, lo que garantiza que su tienda pueda gestionar altos volúmenes de visitantes sin intervención manual. Consulte [escalado automático](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/autoscaling) en la _Guía de Cloud_.

   - Los niveles web y de servicio se pueden escalar de forma independiente, agregando más nodos web para aumentar el tráfico y escalando los nodos de base de datos o de servicio para el rendimiento back-end durante los períodos de mayor actividad. Consulte [arquitectura escalada](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) en la _Guía de Cloud_.

- **Supervisión del rendimiento**:

   - Use **New Relic** para monitorizar las métricas de rendimiento en tiempo real (por ejemplo, uso de CPU, niveles de tráfico) y hacer los ajustes necesarios.

   - Pruebe el rendimiento en entornos de ensayo antes de escalar para evitar problemas en la producción.

- **Desarrollo de nuevas características**:

   - Integre características avanzadas como **personalización basada en IA**, **administración de suscripciones** y soluciones personalizadas.

   - Pruebe y perfeccione continuamente las funciones en los entornos de ensayo antes de la implementación en producción para minimizar el tiempo de inactividad.

- **Mantenimiento continuo del sitio**:

   - Revise regularmente los registros del sistema y las métricas de rendimiento para identificar áreas que se deben mejorar.

   - Garantice que la infraestructura siga siendo escalable y adaptable a los nuevos requisitos y al crecimiento del negocio.

>[!TIP]
>
>Para obtener instrucciones detalladas, consulte [prácticas recomendadas de mantenimiento](overview.md), [personalización](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization) y [desarrollo de características](https://business.adobe.com/blog/the-latest/adobe-commerce-continues-investment-in-composable-development-tools-and-ai-powered-personalization).

### Informes y análisis

- **Adobe Commerce Intelligence:** Commerce Intelligence, una función básica de Adobe Commerce, proporciona información sobre prácticas recomendadas en múltiples fuentes de datos, lo que permite a los comerciantes tomar decisiones basadas en datos científicos y tomar acciones claras e informadas. Consulte la [_Guía del usuario de Commerce Intelligence_](https://experienceleague.adobe.com/en/docs/commerce-business-intelligence/mbi/getting-started).

- **Adobe Analytics:** Adobe Analytics ofrece una potente solución para rastrear, analizar y optimizar el rendimiento de tu tienda en línea. Adobe Analytics ayuda a las empresas de comercio electrónico a obtener una información más detallada sobre el comportamiento de los clientes, el rendimiento de los productos, las tasas de conversión y otras métricas clave, lo que permite la toma de decisiones basada en datos.

- **Google Analytics:** Use Google Analytics para rastrear el comportamiento de los clientes, las fuentes de tráfico y las tasas de conversión.

- **Herramientas adicionales de Commerce Intelligence:** Adobe Commerce incluye Informes avanzados. Esta función le brinda acceso a un conjunto de informes dinámicos basados en sus datos de productos, pedidos y clientes, con un tablero personalizado que se adapta a sus necesidades comerciales. Para obtener más información, consulte [informes avanzados](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/business-intelligence#advanced-reporting) en la _Guía del usuario de administración_.

### Conclusión

La asistencia y el mantenimiento posteriores al lanzamiento son esfuerzos continuos que requieren una atención regular para garantizar que su tienda Adobe Commerce siga funcionando correctamente, siga siendo segura y se adapte a las necesidades de su negocio. La implementación de un enfoque estructurado para la monitorización del sitio, la asistencia al cliente, la optimización y las actualizaciones es crucial para el éxito a largo plazo.
