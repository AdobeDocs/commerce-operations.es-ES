---
title: Acciones y plazos necesarios para proteger los entornos de Commerce
description: Obtenga información acerca de la aplicación de la seguridad para Adobe Commerce no compatible en versiones en la nube y dependencias de software, incluidos plazos, acciones requeridas y riesgos.
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: c32adafa-ed01-4b31-997e-2413013911b0
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
subfeature_v2:
  - id: f2261633-201d-46c5-8a66-999e70527a83
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
badgePaas: label="Solo Adobe Commerce en la nube 2.4.4&#58; 2.4.9" type="Informative" url="https://experienceleague.adobe.com/es/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a Adobe Commerce en la versión de nube 2.4.4 a 2.4.9"
nudge: true
source-git-commit: e2b86c349bdd085717f732532f68e3fae8455d13
workflow-type: tm+mt
source-wordcount: 2200
ht-degree: 0%

---


# Acciones y plazos necesarios para proteger los entornos de Commerce

>[!NOTE]
>
> **Se aplica a:** entornos de Adobe Commerce en la nube (PaaS) que ejecutan las versiones de Adobe Commerce 2.4.4 a 2.4.9.

El panorama de la ciberseguridad está cambiando de manera fundamental, y los mecanismos defensivos que tienen las empresas necesitan evolucionar rápidamente. La seguridad es crítica para las empresas de comercio electrónico, ya que las transacciones en línea les obligan a gestionar datos personales y empresariales confidenciales, lo que las expone a riesgos financieros y de identidad en caso de infracción. Los entornos de comercio electrónico de PaaS tienen un modelo de responsabilidad compartida en el que el cliente es responsable de la seguridad y el mantenimiento de las dependencias de la capa de aplicación, las integraciones con software de terceros y las canalizaciones de implementación.

En Adobe, seguimos comprometidos a abordar los riesgos en evolución y a garantizar que configuramos nuestros clientes de Adobe Commerce en la nube con los más altos estándares de seguridad. Esto incluye:

1. Correcciones de seguridad aisladas mensualmente para una protección más rápida y predecible contra vulnerabilidades críticas

2. Parches de nube para el paquete de Commerce para garantizar la entrega de parches y correcciones rápidas de Adobe que mejoren la integración con entornos de nube y permitan la resolución rápida de problemas críticos

3. Políticas de cumplimiento del ciclo vital

4. Revisiones fuera del ciclo, si es necesario

5. Versiones de parches anuales compatibles a largo plazo


Mientras que Adobe realiza los pasos necesarios para ayudar a mantener a nuestros clientes seguros, el modelo de responsabilidad compartida para Adobe Commerce en la nube requiere que nuestros clientes siempre estén en una versión compatible de Adobe Commerce en la nube y software de terceros, apliquen parches de aplicaciones, auditen extensiones de terceros y protejan el código personalizado. El software que ha pasado el fin de la asistencia del proveedor ya no recibe parches de seguridad, por lo que los problemas de seguridad del software no se solucionan. Si continúa ejecutando su tienda de comercio electrónico con software no compatible, se crea un riesgo de seguridad real y creciente.

Esta página describe las acciones que todos los clientes de Adobe Commerce en la nube (versión 2.4.4 a 2.4.9) deben realizar para garantizar que su entorno de comercio electrónico siga siendo seguro, junto con las fechas de aplicación y qué esperar cuando no se cumplen los requisitos de seguridad.

## Acciones necesarias para mantener un entorno seguro y compatible

Para mantener el entorno de comercio electrónico seguro y mitigar los riesgos, todos los clientes de Adobe Commerce en la nube (versión 2.4.4 a 2.4.9) deben utilizar:

1. Versiones compatibles con todas las dependencias de software de terceros (PHP, MariaDB, Elasticsearch, OpenSearch, Redis, RabbitMQ)

1. Una versión segura y compatible de Adobe Commerce en la nube. Las versiones totalmente compatibles incluyen 2.4.8, 2.4.9 o la última versión disponible. Consulte la documentación de [política de ciclo de vida](https://experienceleague.adobe.com/es/docs/commerce-operations/release/planning/lifecycle-policy).

Siga las directrices que se indican a continuación para comprobar si debe realizar alguna acción para proteger su Adobe Commerce en el entorno de la nube. Los entornos que no cumplan los requisitos de seguridad según los plazos descritos en la tabla 1 a continuación suspenderán el tráfico entrante y desconectarán la tienda. Si tienes dudas sobre cumplir la fecha límite, ponte en contacto con el equipo de tu cuenta o con el [Soporte técnico de Adobe](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket) lo antes posible.

>[!NOTE]
>
> Esta guía no se aplica a los entornos de [!DNL Adobe Commerce as a Cloud Service] (SaaS) ni a las implementaciones locales de Adobe Commerce.

**Tabla 1: Requisitos de seguridad y plazos**

| Su versión de Adobe Commerce en la nube | Actualización a dependencias de software de terceros compatibles | Actualice a la última versión de Adobe Commerce en la nube o migre a [!DNL Adobe Commerce as a Cloud Service] |
| --- | --- | --- |
| 2.4.4 o 2.4.5 | Requerido para el 30 de octubre de 2026. | Requerido para el 1 de junio de 2027 |
| 2.4.6 o 2.4.7 | Requerido para el 30 de octubre de 2026 o el 31 de mayo de 2027, según el software. | Requerido para el 1 de junio de 2028 |
| 2.4.8 o 2.4.9 | Requerido para el 30 de octubre de 2026 o el 31 de mayo de 2027, según el software. | No se requiere en este momento |

## Pasos detallados para proteger su entorno

Solicite a su administrador de Commerce que siga los siguientes pasos.

### Acción 1: Verificar y actualizar las dependencias de software de terceros

Compruebe que su entorno ejecute versiones compatibles con el proveedor de las siguientes dependencias de software de terceros: PHP, MariaDB, Elasticsearch, OpenSearch, Redis, RabbitMQ. Si no es así, actualice la dependencia del software a una versión compatible.

#### Paso 1: Compruebe las versiones de dependencia del software de terceros

1. Inicie sesión en [Cloud Console](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/start/cloud-console), donde podrá ver todos sus proyectos en la nube.
2. Abra el proyecto correspondiente y, a continuación, seleccione el entorno que desee revisar.
3. Abra la pestaña &quot;Contenedores&quot;, donde puede ver una lista de todos los servicios que se utilizan actualmente en el entorno seleccionado.
4. Haga clic en cada vínculo de servicio para comprobar la versión exacta que se está ejecutando en el entorno.
Consulte las instrucciones de [Configurar servicios](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/service/services-yaml) para obtener más información.

Todas las dependencias de software no admitidas deben actualizarse a las versiones descritas en los cronogramas compartidos en la Tabla 2 a continuación.

**Tabla 2: Actualizaciones de dependencias requeridas**

| Dependencia | Versión | Debe actualizar a | Plazo |
| --- | --- | --- | --- |
| PHP | 8.1 e inferior | 8.2 o superior | 31 de mayo de 2027 |
| MariaDB/Galera | 10.5 e inferior | 10.6 o superior | 30 de octubre de 2026 |
| MariaDB/Galera | Mayor que 10,5 pero menor que 10,11 | 10.11 o superior | 31 de mayo de 2027 |
| Elasticsearch | cualquier versión | OpenSearch: versión 2.19 para clientes de 2.4.4 y 2.4.5. Clientes de la versión 3 para 2.4.6 y posteriores. | 30 de octubre de 2026 |
| OpenSearch | 1.x | Clientes de la versión 2.19 para 2.4.4 y 2.4.5. Clientes de la versión 3 para 2.4.6 y posteriores. | 31 de mayo de 2027 |
| Redis | 5 e inferior | Valkey versión 8 o superior | 31 de mayo de 2027 |
| RabbitMQ | 3.9 e inferior | Versión 3.13 o superior | 30 de octubre de 2026 |
| RabbitMQ | Mayor que 3,9 pero menor que 3,13 | 4.3 o superior | 31 de mayo de 2027 |

#### Paso 2: Preparación para una actualización de dependencia de software de terceros

Adobe le ayudará a actualizar estas dependencias de software directamente.

* **Introducción:** Abra un [ticket de asistencia](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case) que enumere los entornos que necesita actualizar y las dependencias involucradas. Abra el ticket al menos 30 días antes de la fecha de aplicación para que Adobe pueda programar el trabajo.

* **Tiempo de inactividad:** Adobe confirmará la ventana esperada cuando se programe.

* **Pruebas:** Actualice y valide un entorno que no sea de producción antes de la producción. Como mínimo, valide el cierre de compra, la búsqueda, el carro de compras y cualquier integración personalizada. Los requisitos se aplican a todos sus entornos, por lo que debe planificar la actualización de cada entorno en lugar de hacerlo solo en producción.

* **Compatibilidad:** La mayoría de estos cambios son actualizaciones de versiones dentro del mismo software y conllevan un riesgo bajo. Los siguientes cambios merecen una atención más detenida:

  * **Elasticsearch a OpenSearch** y **Redis a Valkey** son migraciones a otro software en lugar de actualizaciones de versiones. Es posible que se necesite una actualización del código personalizado, las extensiones o la configuración que hacen referencia al servicio original.
  * La actualización de **PHP 8.1 a 8.2** puede dejar de usarse en código personalizado y extensiones de terceros.

Si utiliza extensiones de terceros, confirme con sus proveedores que sus versiones actuales admiten las versiones de Target. Si trabaja con un integrador de soluciones, inclúyalos en la planificación y validación.

### Acción 2: comprobar la versión de Adobe Commerce en la nube y actualizar a una versión compatible

#### Paso 1: Compruebe la versión de Adobe Commerce en la nube y las acciones necesarias

1. Inicie sesión en el panel de administración de Adobe Commerce.

   La versión actual se muestra en la esquina inferior derecha de cualquier página de Administración.

1. Si la versión está oculta en el panel de administración, use la [herramienta de línea de comandos](../configuration/cli/config-cli.md) de Adobe Commerce para ver la versión ejecutando el siguiente comando:

   ```shell
   bin/magento --version
   ```

Consulte las acciones necesarias para su versión de Adobe Commerce en la siguiente tabla.

**Tabla 3: Requisitos para actualizar la versión de Adobe Commerce en la nube**

| Versión actual de Adobe Commerce en la nube | Acción requerida | Plazo |
| --- |--- |--- |
| Versión 2.4.4 o 2.4.5 | Actualice a Adobe Commerce en la nube versión 2.4.9 (o la versión más reciente) o migre a [!DNL Adobe Commerce as a Cloud Service].<br>Motivo: las versiones 2.4.4 y 2.4.5 solo recibirán correcciones de seguridad limitadas y aisladas para la aplicación principal hasta el 31 de mayo de 2027. Esto no incluye correcciones de calidad, compatibilidad con dependencias de aplicaciones (por ejemplo, PHP) ni actualizaciones de dependencias de la plataforma. Consulte la [Política de ciclo de vida](https://experienceleague.adobe.com/es/docs/commerce-operations/release/planning/lifecycle-policy) de Adobe. | 1 de junio de 2027 |
| Versión 2.4.6 o 2.4.7 | Actualice a Adobe Commerce en la nube versión 2.4.9 (o la versión más reciente) o migre a [!DNL Adobe Commerce as a Cloud Service].<br>Motivo: la versión 2.4.6 recibirá soporte ampliado hasta el 30 de agosto de 2027 y solo recibirá correcciones de seguridad aisladas y limitadas para la aplicación principal hasta el 31 de mayo de 2028. La versión 2.4.7 recibirá soporte estándar hasta el 31 de mayo de 2027 y soporte ampliado hasta el 31 de mayo de 2028. Consulte la [Política de ciclo de vida](https://experienceleague.adobe.com/es/docs/commerce-operations/release/planning/lifecycle-policy) de Adobe. | 1 de junio de 2028 |
| Versión 2.4.8 o 2.4.9 | No es necesaria ninguna acción de actualización de la versión de Adobe Commerce en la nube. Los plazos de dependencia de software de terceros de la Acción 1 aún se aplican.<br>Motivo: no se estableció un plazo. | No aplicable |

#### Paso 2: Determinar la ruta de actualización o migración

Si necesita actualizar la versión de Adobe Commerce en la nube, tiene dos opciones:

1. Actualización a una versión compatible de Adobe Commerce en la nube
1. Migrar a [!DNL Adobe Commerce as a Cloud Service] (SaaS)

La siguiente tabla le ayuda a comparar sus opciones y determinar la mejor ruta para usted.

**Tabla 4: Adobe Commerce en la nube comparado con[!DNL Adobe Commerce as a Cloud Service]**

| | Adobe Commerce en la nube versión 2.4.9 | [!DNL Adobe Commerce as a Cloud Service] |
|---|---|---|
| **Qué es** | La versión más reciente de Adobe Commerce con cobertura de seguridad completa, correcciones de calidad y actualizaciones de dependencia de la plataforma. | Plataforma de comercio completamente gestionada de Adobe, diseñada para la innovación continua sin la sobrecarga de actualización. [Más información](https://experienceleague.adobe.com/es/docs/commerce/cloud-service/overview). |
| **Mejor para ti si** | Desea seguir administrando su propia infraestructura, actualizaciones y parches. | Desea dejar atrás los ciclos de actualización para siempre, reducir el coste total de propiedad y obtener las funciones más recientes de Adobe automáticamente, sin ningún esfuerzo adicional. |
| **Beneficio clave** | Cumple los requisitos de seguridad y, al mismo tiempo, conserva la configuración existente. | Una tienda de Edge, con gran velocidad, un catálogo altamente escalable, administración nativa de recursos digitales e IA generativa integrada, todo en una infraestructura administrada por Adobe. |

## ¿Qué sucede si no se realiza ninguna acción antes de la fecha límite?

Adobe mantiene su compromiso de ayudarle a ejecutar los pasos que debe seguir para adoptar una versión compatible del software de terceros, actualizar a la última versión de Adobe Commerce en la nube o migrar a Adobe Commerce as a Cloud Service.  Si tienes dudas sobre cumplir la fecha límite y necesitas una breve extensión, ponte en contacto con el equipo de tu cuenta o con [Soporte técnico de Adobe](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket) lo antes posible.

Si un entorno no ha cumplido los requisitos de seguridad en las fechas de aplicación compartidas anteriormente, Adobe se verá obligado a tomar las medidas adecuadas para mantener la seguridad de la plataforma de Adobe Commerce y de sus clientes. Esto incluye la suspensión del tráfico a la infraestructura afectada y, como resultado, la tienda de Commerce se desconectará.

Si un entorno sigue sin cumplir los requisitos después de la suspensión del tráfico, Adobe puede finalizar los servicios en la nube e iniciar el proceso de retirada del servicio. Como resultado de la retirada del mercado, todos los datos y activos del entorno de comercio alojado, incluidas todas las instancias, entornos y ramas, se eliminarán de forma permanente y no se podrán restaurar.

## Recursos para ayudarle con las actualizaciones o la migración

**Si decide actualizar a Adobe Commerce en la versión 2.4.9 de la nube:**

* **Informe de compatibilidad de actualización:** Adobe proporciona un informe detallado que identifica exactamente lo que requiere su actualización a Adobe Commerce versión 2.4.9, incluyendo la identificación de qué módulos y archivos requieren actualizaciones, el número de problemas críticos, etc. Consulte la documentación de [Site-Wide Analysis Tool](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/site-wide-analysis-tool/access) para obtener más información sobre cómo generar el informe de compatibilidad de actualización.

* **Actualización de dependencia de software:** Dado que no puede actualizar las dependencias de software directamente, abra un [ticket de soporte](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#support-case) para que Adobe se ocupe de la actualización. Para obtener más información, consulte [Configurar servicios](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/configure/service/services-yaml).

**Si decide migrar a [!DNL Adobe Commerce as a Cloud Service]:**

Adobe proporciona herramientas que reducen el costo y el tiempo de la migración a [!DNL Adobe Commerce as a Cloud Service]. Están disponibles sin costo para usted. Estas herramientas solo se aplican a la migración. No se utilizan para las actualizaciones de versiones de Adobe Commerce en la nube. Consulte la [descripción general de la migración](https://experienceleague.adobe.com/es/docs/commerce/cloud-service/migration/overview) para obtener una guía completa de la migración, que incluye las rutas y fases de la migración.

* **Evaluación de la migración:** Clasifica la complejidad de la migración de las personalizaciones. Consulte la [descripción general de la herramienta de evaluación de migración](https://experienceleague.adobe.com/es/docs/commerce/cloud-service/migration/migration-tools/assessment).

* **Migración de datos:** La [herramienta de migración de datos masiva e incremental](https://experienceleague.adobe.com/es/docs/commerce/cloud-service/migration/migration-tools/bulk-data/migration-tool) mueve sus datos a su nuevo entorno de [!DNL Adobe Commerce as a Cloud Service]. Para obtener acceso, póngase en contacto con el [Soporte técnico de Adobe](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket).

* **Herramientas para desarrolladores y migración asistida por IA:** Adobe Developer App Builder y Commerce Storefront con tecnología Edge Delivery Services ayudan a acelerar la modernización de tiendas y la reorganización de plataformas de extensión.

Si tiene alguna pregunta, póngase en contacto con el equipo de su cuenta o comuníquese con [Servicios de soporte](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket).

>[!MORELIKETHIS]
>
>* [Política de ciclo de vida](lifecycle-policy.md)
>* [Directiva de aplicación de actualización de versiones para Adobe Commerce en la nube](version-upgrade-enforcement-policy.md)
>* [Modelo operativo y de seguridad de responsabilidad compartida](../security-and-compliance/shared-responsibility.md)
