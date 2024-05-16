---
title: Notas de la versión de los parches de seguridad de Adobe Commerce 2.4.4
description: Obtenga información acerca de las correcciones de errores de seguridad, las mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parches de seguridad para Adobe Commerce 2.4.4.
exl-id: 136d7090-6bf2-41e3-8445-b07bdc67f12b
source-git-commit: e1c5b5e5c1a8800aa5aa2657060f61c16743cbda
workflow-type: tm+mt
source-wordcount: '1337'
ht-degree: 0%

---

# Notas de la versión de Adobe Commerce 2.4.4 Security Patch

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## 2.4.4-p8

La versión de seguridad de Adobe Commerce 2.4.4-p8 proporciona correcciones de errores de seguridad para la implementación de Adobe Commerce 2.4.4. Estas actualizaciones corrigen las vulnerabilidades que se han identificado en versiones anteriores.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## 2.4.4-p7

La versión de seguridad de Adobe Commerce 2.4.4-p7 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Aspectos destacados de seguridad

Esta versión incorpora dos mejoras de seguridad significativas:

* **Cambios en el comportamiento de las claves de caché no generadas**:

   * Las claves de caché no generadas para bloques ahora incluyen prefijos que difieren de los prefijos para las claves generadas automáticamente. (Las claves de caché no generadas son claves que se establecen mediante sintaxis de directiva de plantilla o la variable `setCacheKey` o `setData` métodos.)
   * Las claves de caché no generadas para bloques ahora solo deben contener letras, dígitos, guiones (-) y caracteres de subrayado (_). <!-- AC-9831 -->

* **Limitaciones en el número de códigos de cupones generados automáticamente**. Commerce ahora limita el número de códigos de cupones que se generan automáticamente. El máximo predeterminado es 250 000. Los comerciantes pueden utilizar el nuevo **[!UICONTROL Code Quantity Limit]** opción de configuración (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) para controlar este nuevo límite. <!-- AC-8753 -->

## 2.4.4-p6

La versión de seguridad de Adobe Commerce 2.4.4-p6 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

### Aspecto destacado de seguridad

Esta versión introduce una nueva configuración de caché de página completa que ayuda a mitigar los riesgos asociados con el `{BASE-URL}/page_cache/block/esi HTTP` punto final. Este extremo admite fragmentos de contenido cargados dinámicamente y sin restricciones desde controladores de diseño y estructuras de bloque de Commerce. El nuevo **[!UICONTROL Handles Param]** La configuración de establece el valor del punto de conexión `handles` , que determina el número máximo permitido de identificadores por API. El valor predeterminado de esta propiedad es 100. Los comerciantes pueden cambiar este valor desde el Administrador (**[!UICONTROL Stores]** > **[!UICONTROL Settings: Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Problema conocido

**Problema**: Adobe Commerce muestra un **suma de comprobación incorrecta** error durante la descarga por Compositor desde `repo.magento.com`y se interrumpe la descarga del paquete. Este problema puede producirse durante la descarga de los paquetes de versiones preliminares que estaban disponibles durante la versión preliminar y que se debe a un reempaquetado del `magento/module-page-cache` paquete.

**Solución**: Los comerciantes que ven este error durante la descarga pueden seguir estos pasos:

1) Elimine el `/vendor` dentro del proyecto, si existe.
2) Ejecute el `bin/magento composer update magento/module-page-cache` comando. Este comando actualiza solo la variable `page cache` paquete.

Si el problema de la suma de comprobación persiste, elimine la `composer.lock` antes de volver a ejecutar el `bin/magento composer update` para actualizar cada paquete.

## 2.4.4-p5

La versión de seguridad de Adobe Commerce 2.4.4-p5 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Aplicar parche para resolver la vulnerabilidad de seguridad CVE-2022-31160 en la biblioteca jQuery-UI

`jQuery-UI` La versión 1.13.1 de la biblioteca de tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Commerce y Magento Open Source. Esta biblioteca es una dependencia de Adobe Commerce y de los Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecuten implementaciones afectadas deben aplicar el parche especificado en la [Vulnerabilidad de seguridad de la IU de jQuery CVE-2022-31160 corregida para las versiones 2.4.4, 2.4.5 y 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Artículo de la Base de conocimiento.

## 2.4.4-p4

La versión de seguridad de Adobe Commerce 2.4.4-p4 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad y actualizaciones de la plataforma para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Aplicar parche para resolver la vulnerabilidad de seguridad CVE-2022-31160 en la biblioteca jQuery-UI

`jQuery-UI` La versión 1.13.1 de la biblioteca de tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Commerce y Magento Open Source. Esta biblioteca es una dependencia de Adobe Commerce y de los Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecuten implementaciones afectadas deben aplicar el parche especificado en la [Vulnerabilidad de seguridad de la IU de jQuery CVE-2022-31160 corregida para las versiones 2.4.4, 2.4.5 y 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Artículo de la Base de conocimiento.

### Aspecto destacado de seguridad

El comportamiento predeterminado del [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL query y ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) El extremo REST ha cambiado. De forma predeterminada, la API ahora siempre devuelve `true`. Los comerciantes pueden activar el comportamiento original, que es devolver `true` si el correo electrónico no existe en la base de datos y `false` si existe. <!-- AC-6695 -->

### Actualizaciones de plataforma

Las actualizaciones de plataforma para esta versión mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

* **Compatibilidad con caché de barniz 7.3**. Esta versión es compatible con la última versión de Varnish Cache 7.3. La compatibilidad se mantiene con las versiones 6.0.x y 7u.2.x, pero el Adobe recomienda usar Adobe Commerce 2.4.4-p4 solo con Varnish Cache versión 7.3 o versión 6.0 LTS.

* **Compatibilidad con RabbitMQ 3.11**. Esta versión es compatible con la última versión de RabbitMQ 3.11. La compatibilidad sigue siendo con RabbitMQ 3.9, que es compatible hasta agosto de 2023, pero Adobe recomienda utilizar Adobe Commerce 2.4.4-p4 solo con RabbitMQ 3.11.

* **Bibliotecas de JavaScript**. Las bibliotecas de JavaScript obsoletas se han actualizado a las últimas versiones secundarias o de parches, que incluyen `moment.js` biblioteca (v2.29.4), `jQuery UI` biblioteca (v1.13.2) y `jQuery` biblioteca de complementos de validación (versión 1.19.5).

## 2.4.4-p3

La versión de seguridad de Adobe Commerce 2.4.4-p3 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## 2.4.4-p2

La versión de seguridad de Adobe Commerce 2.4.4-p2 proporciona correcciones para vulnerabilidades que se han identificado en versiones anteriores. Una corrección incluye la creación de una nueva configuración. El **Requerir confirmación por correo electrónico si el correo electrónico se ha cambiado** La configuración de permite a los administradores solicitar confirmación por correo electrónico cuando un usuario administrador cambia su dirección de correo electrónico. <!-- AC-6292-->

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

### Aplique AC-3022.patch para seguir ofreciendo DHL como transportista

DHL ha introducido la versión de esquema 6.2 y dejará de utilizar la versión de esquema 6.0 en un futuro próximo. Adobe Commerce 2.4.4 y las versiones anteriores compatibles con la integración de DHL solo admiten la versión 6.0. Los comerciantes que implementen estas versiones deben aplicar `AC-3022.patch` lo antes posible para seguir ofreciendo DHL como transportista. Consulte la [Aplicar un parche para seguir ofreciendo DHL como transportista](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier?_ga=2.201689433.994140970.1661546561-1218319047.1534347481) Artículo de Knowledge Base para obtener información sobre cómo descargar e instalar el parche.

## 2.4.4-p1

La versión de seguridad de Adobe Commerce 2.4.4-p1 proporciona correcciones para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de seguridad del Adobe](https://helpx.adobe.com/security/products/magento/apsb22-38.html).t

### Aplicar `AC-3022.patch` para seguir ofreciendo DHL como transportista

DHL ha introducido la versión de esquema 6.2 y dejará de utilizar la versión de esquema 6.0 en un futuro próximo. Adobe Commerce 2.4.4 y las versiones anteriores compatibles con la integración de DHL solo admiten la versión 6.0. Los comerciantes que implementen estas versiones deben aplicar `AC-3022.patch` lo antes posible para seguir ofreciendo DHL como transportista. Consulte la [Aplicar un parche para seguir ofreciendo DHL como transportista](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Artículo de Knowledge Base para obtener información sobre cómo descargar e instalar el parche.

### Aspectos destacados de seguridad

Las mejoras de seguridad para esta versión mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes, que incluyen:

* Los recursos ACL se han agregado al inventario.
* Se ha mejorado la seguridad de la plantilla de inventario.

### Problemas conocidos

**Problema**: la API web y las pruebas de integración muestran este error cuando se ejecutan en el paquete 2.4.4-p1: `[2022-06-14T16:58:23.694Z] PHP Fatal error:  Declaration of Magento\TestFramework\ErrorLog\Logger::addRecord(int $level, string $message, array $context = []): bool must be compatible with Monolog\Logger::addRecord(int $level, string $message, array $context = [], ?Monolog\DateTimeImmutable $datetime = null): bool in /var/www/html/dev/tests/integration/framework/Magento/TestFramework/ErrorLog/Logger.php on line 69`. **Solución**: instale la versión anterior de Monolog ejecutando la variable `require monolog/monolog:2.6.0` comando. <!-- AC-3651-->

**Problema**: Los comerciantes pueden observar avisos de reducción de versión del paquete durante una actualización de Adobe Commerce 2.4.4 a Adobe Commerce 2.4.4-p1. Estos mensajes se pueden ignorar. La discrepancia en las versiones del paquete se debe a anomalías durante la generación del paquete. No se ha visto afectada ninguna funcionalidad del producto. Consulte la [Paquetes degradados después de actualizar de 2.4.4 a 2.4.4-p1](https://support.magento.com/hc/en-us/articles/8214752983949) Artículo de la Base de conocimiento para analizar los escenarios afectados y las soluciones alternativas.

