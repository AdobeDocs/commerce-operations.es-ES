---
title: 'Política de seguridad: acciones y plazos requeridos'
description: Obtenga información acerca de la aplicación de la seguridad para Adobe Commerce no compatible en versiones en la nube y dependencias de software, incluidos plazos, acciones requeridas y riesgos.
TQID: 'https://experienceleague.adobe.com/0JX-Z-dRjsiQk5jO-LLRi-J4GWdylTh4pOfXRPOabxs'
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
badgePaas: label="Solo Adobe Commerce en la nube" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a Adobe Commerce en la versión 2.4.4 - 2.4.9 de Cloud"
nudge: true
source-git-commit: 85ff49e8a7dbf4ee8c2eef801bd44f45db0a21a5
workflow-type: tm+mt
source-wordcount: 1983
ht-degree: 0%

---

# Política de seguridad: acciones y plazos requeridos

Adobe aplica los requisitos de seguridad para Adobe Commerce en entornos en la nube, incluidas las versiones de dependencia de software compatibles y las versiones de Adobe Commerce compatibles. Esta página describe qué se necesita, las fechas de aplicación y qué sucede si no se cumplen los requisitos.

## ¿Qué está pasando?

La política de seguridad corporativa de Adobe requiere que todos los entornos alojados por Adobe para Adobe Commerce en la nube se ejecuten en software seguro y compatible, incluidos los siguientes:

1. Versiones compatibles con todas las dependencias de software de terceros (PHP, MariaDB, Elasticsearch/OpenSearch, Redis, RabbitMQ)

1. Una versión segura y compatible de Adobe Commerce en la nube (versión 2.4.8, 2.4.9 o la versión más reciente)

Esto sirve para mitigar los riesgos de seguridad de los entornos de comercio electrónico. A los entornos que no cumplan estos requisitos dentro de los plazos establecidos en [Tabla 1](#determine-your-required-actions) se les suspenderá el tráfico entrante, con lo que la tienda quedará sin conexión. Tenga en cuenta esta notificación como un requisito de seguridad y cumplimiento con fechas de aplicación.

Es posible que se le pida que realice dos acciones.

1. Compruebe si se admiten las dependencias de software de terceros. Si no es así, actualice a una versión compatible.

1. Seleccione si necesita actualizar la versión de Adobe Commerce en la nube a una versión compatible.

Encuentre su versión de Adobe Commerce en la nube a continuación para ver qué se requiere de usted y ver los requisitos para:

1. Dependencias de software de terceros

1. Versión de Adobe Commerce en la nube

| Su versión | Actualizar dependencias de software de terceros<br>(PHP, MariaDB, Elasticsearch/OpenSearch, Redis, RabbitMQ)<br>*Consulte [Acción 1: actualizar dependencias de software de terceros](#action-1-upgrade-third-party-software-dependencies) para obtener detalles y pasos siguientes.* | Actualice o migre su versión de Adobe Commerce <br>*Consulte [Acción 2: si necesita actualizar su versión de Adobe Commerce en la nube](#action-2-if-you-need-to-upgrade-your-adobe-commerce-on-cloud-version) para obtener detalles y los siguientes pasos.* |
| --- | --- | --- |
| 2.4.4 o 2.4.5 | Requerido para el 30 de octubre de 2026. | Requerido para el 1 de junio de 2027 |
| 2.4.6 o 2.4.7 | Requerido para el 30 de octubre de 2026 o el 31 de mayo de 2027, según el software. | Requerido para el 1 de junio de 2028 |
| 2.4.8 o 2.4.9 | Requerido para el 30 de octubre de 2026 o el 31 de mayo de 2027, según el software. | No se requiere en este momento |

**Tabla 1: Acciones requeridas y fechas límites por versión**

## ¿Quién no necesita tomar medidas?

Este aviso no se aplica a:

* Clientes con Adobe Commerce en la versión en la nube 2.4.8 o 2.4.9 y cuyos entornos ejecutan versiones compatibles de software de terceros

* Clientes en [!DNL Adobe Commerce as a Cloud Service]

### Cómo comprobar las versiones que está ejecutando

Necesita ayuda del administrador de comercio electrónico para seguir los siguientes pasos y comprobar qué versión está ejecutando.

**Su versión de Adobe Commerce en la nube**

1. Inicie sesión en el panel de administración de Adobe Commerce.

   La versión actual debe mostrarse en la esquina inferior derecha de cualquier página de Administración.

1. Si la versión no se muestra en el Administrador, use la [herramienta de línea de comandos de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli){target="_blank"} para ejecutar el comando de versión:

   ```shell
   bin/magento --version
   ```

**Sus versiones de dependencia de software**

1. Inicie sesión en [Cloud Console](https://console.adobecommerce.com/).
1. Abra el proyecto correspondiente y, a continuación, seleccione el entorno que desee revisar.
1. Compruebe la configuración del servicio para ese entorno en el archivo `.magento/services.yaml`, que define los nombres de servicio y las versiones compatibles que utiliza Adobe Commerce en la infraestructura en la nube.
Para obtener instrucciones detalladas, consulte la documentación de [Configurar servicios](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/services/config-services){target="_blank"}.

## Por qué este mandato de seguridad es importante

El software que ha pasado el fin de la asistencia del proveedor ya no recibe parches de seguridad, lo que significa que los problemas de seguridad conocidos de ese software no se pueden solucionar. Además, según la [Política del ciclo de vida de Adobe](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/lifecycle-policy):

* **Las versiones de Adobe Commerce 2.4.4 y 2.4.5** ahora solo reciben correcciones de seguridad limitadas y aisladas para la aplicación principal hasta el 31 de mayo de 2027. Esta compatibilidad limitada no incluye correcciones de calidad, compatibilidad con dependencias de aplicaciones (por ejemplo, PHP) ni actualizaciones de dependencias de la plataforma

* **Adobe Commerce 2.4.6** recibirá soporte extendido hasta el 30 de agosto de 2027 y solo recibirá correcciones de seguridad aisladas y limitadas para la aplicación principal hasta el 31 de mayo de 2028

* **Adobe Commerce versión 2.4.7** recibirá soporte estándar hasta el 31 de mayo de 2027 y soporte extendido hasta el 31 de mayo de 2028

* **Adobe Commerce en la nube versión 2.4.8 y 2.4.9** sigue siendo compatible y no requiere ninguna actualización de la versión en este momento.

Seguir ejecutando su tienda de comercio electrónico en software no admitido crea un riesgo de seguridad real y creciente para su empresa, incluida su capacidad para mantener la conformidad con PCI y proteger los datos de sus clientes.

>[!IMPORTANT]
>
>Si su entorno no cumple los requisitos de los plazos detallados en la [Tabla 1](#determine-your-required-actions), Adobe suspenderá el tráfico entrante al entorno afectado. La tienda de comercio electrónico no tendrá conexión y no servirá a los compradores. Ver [Qué sucede si no se realiza ninguna acción](#what-happens-if-no-action-is-taken).

## Detalles sobre las acciones que debe realizar

### Acción 1: actualizar dependencias de software de terceros

Según el software, todas las dependencias de software no admitidas deben actualizarse según las escalas de tiempo compartidas en la tabla siguiente. Puede ver sus entornos en [Cloud Console](https://console.adobecommerce.com/) y comprobar las versiones de dependencia que se ejecutan con estas [instrucciones](#check-software-dependency-versions). Las actualizaciones de dependencias de software se aplican a todas las versiones de Adobe Commerce en la nube de 2.4.4 a 2.4.9.

| Dependencia | Versión | Debe actualizar a | Fecha de aplicación |
| --- | --- | --- | --- |
| PHP | 8.1 e inferior | 8.2 o superior | 31 de mayo de 2027 |
| MariaDB/Galera | 10.5 e inferior | 10.6 o superior | 30 de octubre de 2026 |
| MariaDB/Galera | Mayor que 10,5 pero menor que 10,11 | 10.11 o superior | 31 de mayo de 2027 |
| Elasticsearch | cualquier versión | OpenSearch:<br><br>- versión 2.19 para clientes de las versiones 2.4.4 y 2.4.5<br>- versión 3 para clientes de las versiones 2.4.6 y posteriores. | 30 de octubre de 2026 |
| OpenSearch | 1.x | clientes de la versión 2.19 para 2.4.4 y 2.4.5.<br>versión 3 para 2.4.6 y superiores. | 31 de mayo de 2027 |
| Redis | 5 e inferior | Valkey 8 o superior | 31 de mayo de 2027 |
| RabbitMQ | 3.9 e inferior | 3.13 o superior | 30 de octubre de 2026 |
| RabbitMQ | Mayor que 3,9 pero menor que 3,13 | 4.3 o superior | 31 de mayo de 2027 |

**Tabla 2: Requisitos para la actualización de dependencias de software**

#### Preparación para una actualización de dependencia de software de terceros

Adobe le ayudará a actualizar estas dependencias de software directamente.

* **Introducción:** Abra un [ticket de asistencia](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) que enumere los entornos que necesita actualizar y las dependencias involucradas. Abra su boleto al menos 30 días antes de la fecha de aplicación para que nuestro equipo pueda programar el trabajo.

* **Tiempo de inactividad:** Adobe confirmará la ventana esperada cuando se programe.

* **Pruebas:** Actualice y valide un entorno que no sea de producción antes de la producción. Como mínimo, valide el cierre de compra, la búsqueda, el carro de compras y cualquier integración personalizada. Los requisitos se aplican a todos los entornos, por lo que debe planificar la actualización de cada entorno en lugar de hacerlo solo en producción.

* **Compatibilidad:** La mayoría de estos cambios son actualizaciones de versiones dentro del mismo software y conllevan un riesgo bajo. Lo siguiente merece una atención más estrecha:

  * **Elasticsearch a OpenSearch** y **Redis a Valkey** son migraciones a otro software en lugar de actualizaciones de versiones. Puede que sea necesario actualizar el código personalizado, las extensiones o la configuración que hacen referencia al servicio original.
  * **PHP 8.1 a 8.2** puede dejar de usarse en código personalizado y extensiones de terceros.

Si utiliza extensiones de terceros, confirme con los proveedores de extensiones que sus versiones actuales admiten las versiones de Target. Si trabaja con un integrador de soluciones, inclúyalos en la planificación y validación.

### Acción 2: si necesita actualizar su versión de Adobe Commerce en la nube:

Tiene la opción de (i) actualizar a una versión compatible de Adobe Commerce en la nube o (ii) migrar a Adobe Commerce as a Cloud Service (la plataforma de comercio completamente administrada de Adobe)

La fecha de aplicación de la versión actual se aplica independientemente de la opción que elija.

| Versión actual | Acción | Fecha de aplicación |
| --- | --- | --- |
| Uso de Adobe Commerce en la versión 2.4.4 o 2.4.5 de Cloud | Actualice a Adobe Commerce en la nube versión 2.4.9 (o la versión más reciente) o migre a Adobe Commerce as a Cloud Service | 1 de junio de 2027 |
| Uso de Adobe Commerce en la versión 2.4.6 o 2.4.7 de Cloud | Actualice a Adobe Commerce en la nube versión 2.4.9 (o la versión más reciente) o migre a Adobe Commerce as a Cloud Service | 1 de junio de 2028 |
| Uso de Adobe Commerce en las versiones de nube 2.4.8 o 2.4.9 | En este momento no es necesaria ninguna acción de actualización de la versión de Adobe Commerce en la nube. Los plazos de dependencia del software de la Acción 1 siguen aplicándose. | n/a |

**Tabla 3: Directrices y plazos si debe actualizar su versión actual de Adobe Commerce en la nube**

Consulte la siguiente matriz para obtener más información sobre Adobe Commerce en la nube versión 2.4.9 y Adobe Commerce as a Cloud Service, para poder tomar una decisión informada.

**Tabla 4: Actualizar a Adobe Commerce en la nube frente a Migrar a Adobe Commerce as a Cloud Service**

| | Adobe Commerce en la nube versión 2.4.9 | Adobe Commerce as a Cloud Service |
| --- | --- | --- |
| Qué es | La versión más reciente de Adobe Commerce con cobertura de seguridad completa, correcciones de calidad y actualizaciones de dependencia de la plataforma. | Plataforma de comercio completamente gestionada de Adobe, diseñada para la innovación continua sin la sobrecarga de actualización. [Más información](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview). |
| Lo mejor para usted si | Desea seguir administrando su propia infraestructura, actualizaciones y parches por ahora. Puede migrar a Adobe Commerce as a Cloud Service cuando esté listo. | Desea dejar atrás los ciclos de actualización para siempre, reducir el coste total de propiedad y obtener las funciones más recientes de Adobe automáticamente, sin ningún esfuerzo adicional. |
| Ventaja clave | Cumple los requisitos de seguridad ahora y conserva la configuración existente. | Una tienda de Edge, con gran velocidad, un catálogo altamente escalable, administración nativa de recursos digitales e IA generativa integrada, todo en una infraestructura administrada por Adobe. |

## ¿Qué sucede si no se realiza ninguna acción?

Si un entorno no ha cumplido estos requisitos en las fechas de aplicación compartidas [por encima de](#determine-your-required-actions), Adobe tomará las medidas adecuadas. Esto incluye la suspensión del tráfico a la infraestructura afectada y, como resultado, la tienda de comercio electrónico quedará sin conexión.

Si un entorno sigue sin cumplir los requisitos después de la suspensión del tráfico, Adobe puede finalizar los servicios en la nube e iniciar el proceso de retirada del servicio. Como resultado de la retirada del mercado, todos los datos y activos del entorno de comercio electrónico alojado, incluidas todas las instancias, entornos y ramas, se eliminarán de forma permanente y no se podrán restaurar.

## Resumen de cómo Adobe le ayudará

Adobe ofrece herramientas y asistencia para que su transición sea lo más fluida posible, independientemente de si realiza la actualización o la migración.

**Si decide actualizar a Adobe Commerce en la versión 2.4.9** de la nube

* **Informe de compatibilidad de actualización:** Adobe proporciona un informe detallado que identifica exactamente lo que requiere su actualización a la versión 2.4.9 de Adobe Commerce, incluyendo el tiempo y el ámbito de costo. [Genere su informe de compatibilidad de actualización](https://supportinsights.adobe.com/commerce/tab/main).

* **Actualización de dependencia de software:** Dado que no puede actualizar las dependencias de software directamente, [abra un vale de soporte técnico](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket){target="_blank"} para que Adobe se ocupe de la actualización. Para obtener más información, consulte [Configurar servicios](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/configuration/overview){target="_blank"}.

**Si decide migrar a Adobe Commerce as a Cloud Service**

Adobe proporciona herramientas que reducen el coste y el tiempo de la migración a Adobe Commerce as a Cloud Service. Esto no tiene costo para ti. Estas herramientas solo se aplican a la migración y no se utilizan para una actualización de versión en Adobe Commerce en la nube. Consulte la [descripción general de la migración](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/overview) para obtener una guía completa de la migración, que incluye las rutas y fases de la migración.

* **Evaluación de la migración:** Clasifica la complejidad de la migración de las personalizaciones. Consulte la [descripción general de la herramienta de evaluación de migración](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/assessment).

* **Migración de datos:** La [herramienta de migración de datos masiva e incremental](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/migration/migration-tools/bulk-data) mueve sus datos a su nuevo entorno de as a Cloud Service de Adobe Commerce.

* Las [herramientas para desarrolladores y migración asistida por IA de Adobe](https://developer.adobe.com/commerce/extensibility/developer-agent/), entre ellas **[!DNL Adobe Developer App Builder]** y **[!DNL Commerce Storefront powered by Edge Delivery Services]**, ayudan a acelerar la modernización de tiendas y la reorganización de la plataforma de extensiones.

Si tiene alguna pregunta, póngase en contacto con el equipo de su cuenta, el administrador de cuentas de soluciones, el especialista en renovación o los [servicios de soporte](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide?lang=en#submit-ticket).
