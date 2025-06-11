---
title: Notas de la versión de Adobe Commerce 2.4.4 Security Patch
description: Obtenga información acerca de las correcciones de errores de seguridad, las mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parches de seguridad para Adobe Commerce 2.4.4.
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: 33debd1c742698e8242faaef1ff83bb2a9e5ee58
workflow-type: tm+mt
source-wordcount: '1715'
ht-degree: 0%

---


# Notas de la versión de parches de seguridad de Adobe Commerce 2.4.4

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.4-p14

La versión de seguridad de Adobe Commerce 2.4.4-p14 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.4.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB25-50](https://helpx.adobe.com/es/security/products/magento/apsb25-50.html).

{{b2b-patches}}

### Características destacadas

Esta versión incluye los siguientes aspectos destacados:

* **Mejora del rendimiento de la API**: resuelve la degradación del rendimiento en los extremos de API web asincrónicos masivos que se introdujeron después de la revisión de seguridad anterior.<!-- AC-14078 -->

* **Corrección de acceso de bloques de CMS**: resuelve un problema en el cual los usuarios administradores con permisos restringidos (como acceso de solo comercialización) no podían ver la página de listado [!UICONTROL CMS Blocks].

  Anteriormente, estos usuarios encontraban un error debido a la falta de parámetros de configuración después de instalar las revisiones de seguridad anteriores.<!-- AC-14087 -->

* **Compatibilidad con límites de cookies**: resuelve un cambio incompatible con versiones anteriores que implica la constante `MAX_NUM_COOKIES` en el marco de trabajo. Esta actualización restaura el comportamiento esperado y garantiza la compatibilidad de las extensiones o personalizaciones que interactúan con los límites de las cookies.<!-- AC-14475 -->

* **Operaciones asincrónicas**: operaciones asincrónicas restringidas para anular pedidos de clientes anteriores.<!-- AC-13917 -->

## 2.4.4-p13

La versión de seguridad de Adobe Commerce 2.4.4-p13 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.4.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB25-26](https://helpx.adobe.com/es/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.4-p12

La versión de seguridad de Adobe Commerce 2.4.4-p12 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.4.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB25-08](https://helpx.adobe.com/es/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.4-p11

La versión de seguridad de Adobe Commerce 2.4.4-p11 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.4.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB24-73](https://helpx.adobe.com/es/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

## 2.4.4-p10

La versión de seguridad de Adobe Commerce 2.4.4-p10 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.4.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB24-61](https://helpx.adobe.com/es/security/products/magento/apsb24-61.html).

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Revisiones incluidas en esta versión

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.4-p9

La versión de seguridad de Adobe Commerce 2.4.4-p9 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.4.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB24-40](https://helpx.adobe.com/es/security/products/magento/apsb24-40.html).

### Aplicar revisión para CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Actualizaciones de plataforma

* **Compatibilidad con MariaDB 10.5**. Esta versión del parche presenta compatibilidad con MariaDB versión 10.5. Adobe Commerce sigue siendo compatible con MariaDB versión 10.4, pero Adobe recomienda usar Adobe Commerce 2.4.4-p9 y todas las próximas versiones de parches solo de seguridad 2.4.4 solo con MariaDB versión 10.5 porque el mantenimiento de MariaDB 10.4 finaliza el 18 de junio de 2024. <!--AC-11530-->

### Características destacadas

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.4-p8

La versión de seguridad de Adobe Commerce 2.4.4-p8 proporciona correcciones de errores de seguridad para la implementación de Adobe Commerce 2.4.4. Estas actualizaciones corrigen las vulnerabilidades que se han identificado en versiones anteriores.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB24-18](https://helpx.adobe.com/es/security/products/magento/apsb24-18.html).

## 2.4.4-p7

La versión de seguridad de Adobe Commerce 2.4.4-p7 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB24-03](https://helpx.adobe.com/es/security/products/magento/apsb24-03.html).

### Características destacadas

Esta versión incorpora dos mejoras de seguridad significativas:

* **Cambios en el comportamiento de las claves de caché no generadas**:

   * Las claves de caché no generadas para bloques ahora incluyen prefijos que difieren de los prefijos para las claves generadas automáticamente. (Las claves de caché no generadas son claves que se establecen mediante sintaxis de directiva de plantilla para los métodos `setCacheKey` o `setData`).
   * Las claves de caché no generadas para bloques ahora deben contener solo letras, dígitos, guiones (-) y caracteres de subrayado (_). <!-- AC-9831 -->

* **Limitaciones en el número de códigos de cupones generados automáticamente**. Commerce ahora limita el número de códigos de cupones que se generan automáticamente. El máximo predeterminado es 250 000. Los comerciantes pueden usar la nueva opción de configuración **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) para controlar este nuevo límite. <!-- AC-8753 -->

## 2.4.4-p6

La versión de seguridad de Adobe Commerce 2.4.4-p6 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB23-50](https://helpx.adobe.com/es/security/products/magento/apsb23-50.html).

Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

### Características destacadas

Esta versión introduce una nueva configuración de caché de página completa que ayuda a mitigar los riesgos asociados con el extremo `{BASE-URL}/page_cache/block/esi HTTP`. Este extremo admite fragmentos de contenido cargados dinámicamente y sin restricciones desde controladores de diseño y estructuras de bloque de Commerce. La nueva configuración **[!UICONTROL Handles Param]** establece el valor del parámetro `handles` de este extremo, que determina el número máximo permitido de identificadores por API. El valor predeterminado de esta propiedad es 100. Los comerciantes pueden cambiar este valor desde el administrador (**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Problemas conocidos

**Problema**: Adobe Commerce muestra un error de **suma de comprobación incorrecta** durante la descarga por Compositor desde `repo.magento.com` y la descarga del paquete se interrumpe. Este problema puede ocurrir durante la descarga de paquetes de versiones que estaban disponibles durante la versión preliminar y que se debe a un reempaquetado del paquete `magento/module-page-cache`.

**Solución alternativa**: Los comerciantes que ven este error durante la descarga pueden seguir estos pasos:

1) Elimine el directorio `/vendor` dentro del proyecto, si existe.
2) Ejecute el comando `bin/magento composer update magento/module-page-cache`. Este comando actualiza solamente el paquete `page cache`.

Si el problema de la suma de comprobación persiste, quite el archivo `composer.lock` antes de volver a ejecutar el comando `bin/magento composer update` para actualizar todos los paquetes.

## 2.4.4-p5

La versión de seguridad de Adobe Commerce 2.4.4-p5 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB23-42](https://helpx.adobe.com/es/security/products/magento/apsb23-42.html).

### Aplicar revisión para CVE-2022-31160

La versión 1.13.1 de la biblioteca `jQuery-UI` tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Commerce y Magento Open Source. Esta biblioteca es una dependencia de Adobe Commerce y Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecuten implementaciones afectadas deben aplicar el parche especificado en la corrección de la vulnerabilidad de seguridad de la interfaz de usuario de [jQuery CVE-2022-31160 para las versiones 2.4.4, 2.4.5 y 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=es) del artículo de la Base de conocimiento.

## 2.4.4-p4

La versión de seguridad de Adobe Commerce 2.4.4-p4 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad y actualizaciones de la plataforma para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB23-35](https://helpx.adobe.com/es/security/products/magento/apsb23-35.html).

### Aplicar revisión para CVE-2022-31160

La versión 1.13.1 de la biblioteca `jQuery-UI` tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Commerce y Magento Open Source. Esta biblioteca es una dependencia de Adobe Commerce y Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecuten implementaciones afectadas deben aplicar el parche especificado en la corrección de la vulnerabilidad de seguridad de la interfaz de usuario de [jQuery CVE-2022-31160 para las versiones 2.4.4, 2.4.5 y 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=es) del artículo de la Base de conocimiento.

### Características destacadas

El comportamiento predeterminado de la consulta GraphQL [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) y el extremo REST ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) ha cambiado. De manera predeterminada, la API ahora siempre devuelve `true`. Los comerciantes pueden habilitar el comportamiento original, que consiste en devolver `true` si el correo electrónico no existe en la base de datos y `false` si existe. <!-- AC-6695 -->

### Actualizaciones de plataforma

Las actualizaciones de plataforma para esta versión mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

* **Compatibilidad con Varnish cache 7.3**. Esta versión es compatible con la última versión de Varnish Cache 7.3. La compatibilidad sigue siendo con las versiones 6.0.x y 7u.2.x, pero Adobe recomienda utilizar Adobe Commerce 2.4.4-p4 solo con Varnish Cache versión 7.3 o versión 6.0 LTS.

* **Compatibilidad con RabbitMQ 3.11**. Esta versión es compatible con la última versión de RabbitMQ 3.11. La compatibilidad sigue siendo con RabbitMQ 3.9, que es compatible hasta agosto de 2023, pero Adobe recomienda utilizar Adobe Commerce 2.4.4-p4 solo con RabbitMQ 3.11.

* **Bibliotecas de JavaScript**. Las bibliotecas JavaScript obsoletas se han actualizado a las últimas versiones secundarias o de parches, incluidas la biblioteca `moment.js` (v2.29.4), la biblioteca `jQuery UI` (v1.13.2) y la biblioteca de complementos de validación `jQuery` (v1.19.5).

## 2.4.4-p3

La versión de seguridad de Adobe Commerce 2.4.4-p3 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB23-17](https://helpx.adobe.com/es/security/products/magento/apsb23-17.html).

## 2.4.4-p2

La versión de seguridad de Adobe Commerce 2.4.4-p2 proporciona correcciones para vulnerabilidades que se han identificado en versiones anteriores. Una corrección incluye la creación de una nueva configuración. La opción de configuración [!UICONTROL **Requerir confirmación por correo electrónico si se ha cambiado el correo electrónico**] permite a los administradores solicitar confirmación por correo electrónico cuando un usuario administrador cambia su dirección de correo electrónico. <!-- AC-6292-->

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB22-48](https://helpx.adobe.com/es/security/products/magento/apsb22-48.html).

### Aplique AC-3022.patch para seguir ofreciendo DHL como transportista

DHL ha introducido la versión de esquema 6.2 y dejará de utilizar la versión de esquema 6.0 en un futuro próximo. Adobe Commerce 2.4.4 y las versiones anteriores compatibles con la integración de DHL solo admiten la versión 6.0. Los comerciantes que implementen estas versiones deben aplicar `AC-3022.patch` lo antes posible para seguir ofreciendo DHL como transportista. Consulte el artículo de la base de conocimiento [Aplicar un parche para seguir ofreciendo DHL como transportista](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) para obtener información sobre cómo descargar e instalar el parche.

## 2.4.4-p1

La versión de seguridad de Adobe Commerce 2.4.4-p1 proporciona correcciones para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe](https://helpx.adobe.com/es/security/products/magento/apsb22-38.html).t

### Aplicar `AC-3022.patch` para seguir ofreciendo DHL como transportista

DHL ha introducido la versión de esquema 6.2 y dejará de utilizar la versión de esquema 6.0 en un futuro próximo. Adobe Commerce 2.4.4 y las versiones anteriores compatibles con la integración de DHL solo admiten la versión 6.0. Los comerciantes que implementen estas versiones deben aplicar `AC-3022.patch` lo antes posible para seguir ofreciendo DHL como transportista. Consulte el artículo de la base de conocimiento [Aplicar un parche para seguir ofreciendo DHL como transportista](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) para obtener información sobre cómo descargar e instalar el parche.

### Características destacadas

Las mejoras de seguridad para esta versión mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes, que incluyen:

* Los recursos ACL se han agregado al inventario.
* Se ha mejorado la seguridad de la plantilla de inventario.

### Problemas conocidos

**Problema**: la API web y las pruebas de integración muestran este error cuando se ejecutan en el paquete 2.4.4-p1: `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **Solución alternativa**: instale la versión anterior de Monólogo ejecutando el comando `require monolog/monolog:2.6.0`. <!-- AC-3651-->

**Problema**: Los comerciantes pueden observar avisos de reducción de versión del paquete durante una actualización de Adobe Commerce 2.4.4 a Adobe Commerce 2.4.4-p1. Estos mensajes se pueden ignorar. La discrepancia en las versiones del paquete se debe a anomalías durante la generación del paquete. No se ha visto afectada ninguna funcionalidad del producto. Consulte el artículo de la base de conocimiento [Paquetes degradados después de actualizar de 2.4.4 a 2.4.4-p1](https://support.magento.com/hc/en-us/articles/8214752983949) para ver una discusión de los escenarios afectados y las soluciones alternativas.
