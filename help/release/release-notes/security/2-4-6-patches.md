---
title: Notas de la versión del parche de seguridad de Adobe Systems Commerce 2.4.6
description: Learn about security bug fixes, security enhancements, and other security related updates included in the security patch releases for Adobe Commerce version 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: 9bf1c539220d70a8e7fe449e4d91199f23cc23b2
workflow-type: tm+mt
source-wordcount: '1316'
ht-degree: 0%

---


# Release notes for Adobe Commerce 2.4.6 security patches

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.6-p10

La versión de seguridad de Adobe Systems Commerce 2.4.6-p10 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.6.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB25-26](https://helpx.adobe.com/es/security/products/magento/apsb25-26.html).

{{b2b-patches}}

## 2.4.6-p9

The Adobe Commerce 2.4.6-p9 security release provides security bug fixes for vulnerabilities identified in previous releases of 2.4.6.

For the latest information about the security bug fixes, see [Adobe Security Bulletin APSB25-08](https://helpx.adobe.com/es/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Highlights

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.6-p8

The Adobe Commerce 2.4.6-p8 security release provides security bug fixes for vulnerabilities identified in previous releases of 2.4.6.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB24-73](https://helpx.adobe.com/es/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Resúmenes

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Correcciones incluidas en esta versión

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.6-p7

La versión de seguridad de Adobe Systems Commerce 2.4.6-p7 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.6.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB24-61](https://helpx.adobe.com/es/security/products/magento/apsb24-61.html).

### Resúmenes

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Correcciones incluidas en esta versión

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.6-p6

La versión de seguridad de Adobe Systems Commerce 2.4.6-p6 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.6.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB24-40](https://helpx.adobe.com/es/security/products/magento/apsb24-40.html).

Para ser compatibles con la versión 2.4.6-p6 de Commerce, los comerciantes que tengan la extensión Adobe Systems Commerce B2B deben actualizar a [B2B versión 1.4.2-p1](https://experienceleague.adobe.com/es/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Aplicar revisión para CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

Para ser compatibles con la versión 2.4.6-p6 de Commerce, los comerciantes que tengan la extensión Adobe Systems Commerce B2B deben actualizar a [B2B versión 1.4.2-p1](https://experienceleague.adobe.com/es/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Resúmenes

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.6-p5

La versión de seguridad de Adobe Systems Commerce 2.4.6-p5 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.6.

Para obtener la información más reciente acerca de estas correcciones, consulte [Adobe Systems boletín de seguridad APSB24-18](https://helpx.adobe.com/es/security/products/magento/apsb24-18.html).

## 2.4.6-p4

La versión de seguridad Adobe Systems Commerce 2.4.6-p4 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB24-03](https://helpx.adobe.com/es/security/products/magento/apsb24-03.html).

### Resúmenes

Esta versión introduce dos mejoras de seguridad significativas:

* **Cambios en el comportamiento de las claves de caché no generadas**:

   * Las claves de caché no generadas para bloques ahora incluyen prefijos que difieren de los prefijos para claves que se generan automáticamente. (Las claves de caché no generadas son claves que se establecen mediante plantilla sintaxis de directiva o los `setCacheKey` métodos o `setData` ).
   * Las claves de caché no generadas para bloques ahora deben contener solo letras, dígitos, guiones (-) y caracteres de subrayado (_).  <!-- AC-9831 -->

* **Limitaciones en el número de códigos** de cupón generados automáticamente. El comercio ahora limita el número de códigos de cupón que se generan automáticamente. El valor máximo predeterminado es 250.000. Los comerciantes pueden utilizar la nueva **[!UICONTROL Code Quantity Limit]** opción de configuración (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) para controlar este nuevo límite. <!-- AC-8753 -->

## 2.4.6-p3

La versión de seguridad Adobe Systems Commerce 2.4.6-p3 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente acerca de las correcciones de seguridad, consulte [Adobe Systems boletín de seguridad APSB23-50](https://helpx.adobe.com/es/security/products/magento/apsb23-50.html).

### Resúmenes

Esta versión introduce una nueva opción de configuración de caché de Página completa que ayuda a mitigar los riesgos asociados con el `{BASE-URL}/page_cache/block/esi HTTP` extremo. Este extremo admite fragmentos de contenido cargados dinámicamente sin restricciones procedentes de controladores de diseño de comercio y estructuras de bloques. La nueva **[!UICONTROL Handles Param]** configuración establece el valor del `handles` parámetro de este extremo, que determina el número máximo permitido de identificadores por API. El valor predeterminado de este Propiedad es 100. Los comerciantes pueden cambiar este valor desde el Administrador (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > > **[!UICONTROL System]** **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### Correcciones incluidas en esta versión

Adobe Systems Commerce 2.4.6-p3 incluye la resolución de la degradación del rendimiento corregida por parche ACSD-51892. Los comerciantes no se ven afectados por el problema que se aborda en este parche, que se describe en el artículo de Knowledge Base ACSD-51892: Problema de rendimiento donde los [archivos de configuración se cargan varias veces](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html?lang=es) veces.

### Problemas conocidos

**Problema**: Adobe Systems Commerce muestra un `wrong checksum` error durante la descargar por Composer desde `repo.magento.com`y se interrumpe la descargar del paquete. Este problema puede producirse durante descargar de paquetes de lanzamiento disponibles durante el período de prelanzamiento y está causado por un reempaquetado del `magento/module-page-cache` paquete.

**Solución alternativa**: Los comerciantes que vean este error durante descargar pueden seguir estos pasos:

1) Eliminar el `/vendor` directorio dentro del proyecto, si existe.
2) Ejecute el `bin/magento composer update magento/module-page-cache` comando. Este comando actualiza sólo el `page cache` paquete.

Si el problema de suma de comprobación persiste, elimine el `composer.lock` archivo antes de volver a ejecutar el `bin/magento composer update` comando para actualizar todos los paquetes.

## 2.4.6-p2

La versión de seguridad Adobe Systems Commerce 2.4.6-p2 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también proporciona mejoras de seguridad para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB23-42](https://helpx.adobe.com/es/security/products/magento/apsb23-42.html).

### Apply hotfix for CVE-2022-31160

`jQuery-UI` library version 1.13.1 has a known security vulnerability (CVE-2022-31160) that affects multiple versions of Adobe Commerce and Magento Open Source. Este biblioteca es una dependencia de Adobe Systems Commerce y Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecutan implementaciones afectadas deben aplicar el parche especificado en el artículo de la Base de conocimiento sobre la vulnerabilidad de seguridad de IU de jQuery CVE-2022-31160 para las [versiones](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=es) 2.4.4, 2.4.5 y 2.4.6.

### Resúmenes

El valor de `fastcgi_pass` en el `nginx.sample` archivo se ha devuelto a su valor anterior (anterior a 2.4.6-p1) de `fastcgi_backend`. Este valor se cambió inadvertidamente a `php-fpm:9000` en Adobe Systems Commerce 2.4.6-p1.

### Hotfixes included in this release

Adobe Commerce 2.4.6-p2 includes resolution of the performance degradation that was addressed by patch ACSD-51892. Merchants are not affected by the issue addressed by this patch, which is described in the [ACSD-51892: Performance issue where config files load multiple times](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html?lang=es) Knowledge Base article.

## 2.4.6-p1

The Adobe Commerce 2.4.6-p1 security release provides security bug fixes for vulnerabilities that have been identified in previous releases. This release also includes security enhancements and platform upgrades to improve compliance with the latest security best practices.

For the latest information about the security bug fixes, see [Adobe Security Bulletin APSB23-35](https://helpx.adobe.com/es/security/products/magento/apsb23-35.html).

### Aplicar revisión para CVE-2022-31160

`jQuery-UI` biblioteca versión 1.13.1 tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Systems Commerce y Magento Open Source. Este biblioteca es una dependencia de Adobe Systems Commerce y Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecutan implementaciones afectadas deben aplicar el parche especificado en el artículo de Knowledge Base CVE-2022-31160 [sobre la vulnerabilidad de seguridad de Query IU para las versiones](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=es) 2.4.4, 2.4.5 y 2.4.6.

#### Destacar

El comportamiento predeterminado del punto final REST [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) consulta y ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) de GraphQL ha cambiado. De forma predeterminada, la API ahora siempre devuelve `true`. Los comerciantes pueden habilitar el comportamiento original, que es devolver `true` si el correo electrónico no existe en la base de datos y `false` si existe. <!-- AC-6695 -->

### Platform actualizaciones

Platform upgrades for this release improve compliance with the latest security best practices.

* **Varnish cache 7.3 support**. Esta versión es compatible con la última versión de Varnish Cache 7.3. Compatibilidad mantiene con las versiones 6.0.x y 7.2.x, pero Adobe Systems recomienda usar Adobe Systems Commerce 2.4.6-p1 solo con Varnish Cache versión 7.3 o versión 6.0 LTS.

* **Compatibilidad con** RabbitMQ 3.11. Esta versión es compatible con la última versión de RabbitMQ 3.11. Compatibilidad permanece con RabbitMQ 3.9, que es compatible hasta agosto de 2023, pero Adobe Systems recomienda usar Adobe Systems Commerce 2.4.6-p1 solo con RabbitMQ 3.11.

* **JavaScript bibliotecas**. Outdated JavaScript libraries have been upgraded to the latest minor or patch versions, including `moment.js` library (v2.29.4), `jQuery UI` library (v1.13.2), and `jQuery` validation plugin library (v1.19.5).

### Known issues

* The `nginx.sample` file was inadvertently updated with a change that modifies the value of `fastcgi_pass` from `fastcgi_backend` to `php-fpm:9000`. This change can be safely reverted or ignored. <!-- AC-8992 -->

* Missing dependencies for the B2B security package cause the following installation error when installing or upgrading the B2B extension to 1.4.0.

  ```
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  This issue can be resolved by adding manual dependencies for the B2B security package with a [stability tag](https://getcomposer.org/doc/04-schema.md#package-links). Para obtener más información, consulte la Notas de la versión B2B[&#128279;](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html?lang=es#known-issue).
