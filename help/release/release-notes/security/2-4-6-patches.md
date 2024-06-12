---
title: Notas de la versión de Adobe Commerce 2.4.6 Security Patch
description: Obtenga información acerca de las correcciones de errores de seguridad, las mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parches de seguridad para Adobe Commerce 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: 59a5306c8329ddc3ca2a2e086f5ebe81b49eab3a
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 0%

---


# Notas de la versión de parches de seguridad de Adobe Commerce 2.4.6

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.6-p6

La versión de seguridad de Adobe Commerce 2.4.6-p6 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.6.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Mejoras de seguridad adicionales

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## Adobe Commerce 2.4.6-p5

La versión de seguridad de Adobe Commerce 2.4.6-p5 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.6.

Para obtener la información más reciente sobre estas correcciones, consulte [Boletín de Seguridad del Adobe APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.6-p4

La versión de seguridad de Adobe Commerce 2.4.6-p4 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Aspectos destacados de seguridad

Esta versión incorpora dos mejoras de seguridad significativas:

* **Cambios en el comportamiento de las claves de caché no generadas**:

   * Las claves de caché no generadas para bloques ahora incluyen prefijos que difieren de los prefijos para las claves generadas automáticamente. (Las claves de caché no generadas son claves que se establecen mediante sintaxis de directiva de plantilla o la variable `setCacheKey` o `setData` métodos.)
   * Las claves de caché no generadas para bloques ahora solo deben contener letras, dígitos, guiones (-) y caracteres de subrayado (_).  <!-- AC-9831 -->

* **Limitaciones en el número de códigos de cupones generados automáticamente**. Commerce ahora limita el número de códigos de cupones que se generan automáticamente. El máximo predeterminado es 250 000. Los comerciantes pueden utilizar el nuevo **[!UICONTROL Code Quantity Limit]** opción de configuración (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) para controlar este nuevo límite. <!-- AC-8753 -->

## Adobe Commerce 2.4.6-p3

La versión de seguridad de Adobe Commerce 2.4.6-p3 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de seguridad, consulte [Boletín de Seguridad del Adobe APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Aspectos destacados de seguridad

Esta versión introduce una nueva configuración de caché de página completa que ayuda a mitigar los riesgos asociados con el `{BASE-URL}/page_cache/block/esi HTTP` punto final. Este extremo admite fragmentos de contenido cargados dinámicamente y sin restricciones desde controladores de diseño y estructuras de bloque de Commerce. El nuevo **[!UICONTROL Handles Param]** La configuración de establece el valor del punto de conexión `handles` , que determina el número máximo permitido de identificadores por API. El valor predeterminado de esta propiedad es 100. Los comerciantes pueden cambiar este valor desde el Administrador (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### Revisiones incluidas en esta versión

Adobe Commerce 2.4.6-p3 incluye la resolución de la degradación del rendimiento corregida por el parche ACSD-51892. Los comerciantes no se ven afectados por el problema que resuelve este parche, que se describe en la sección [ACSD-51892: Problema de rendimiento donde los archivos de configuración se cargan varias veces](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) Artículo de la Base de conocimiento.

### Problema conocido

**Problema**: Adobe Commerce muestra un `wrong checksum` error durante la descarga por Compositor desde `repo.magento.com`y se interrumpe la descarga del paquete. Este problema puede ocurrir durante la descarga de los paquetes de versiones disponibles durante el periodo de prelanzamiento y se debe a un reempaquetado del `magento/module-page-cache` paquete.

**Solución**: Los comerciantes que ven este error durante la descarga pueden seguir estos pasos:

1) Elimine el `/vendor` dentro del proyecto, si existe.
2) Ejecute el `bin/magento composer update magento/module-page-cache` comando. Este comando actualiza solo la variable `page cache` paquete.

Si el problema de la suma de comprobación persiste, elimine la `composer.lock` antes de volver a ejecutar el `bin/magento composer update` para actualizar cada paquete.

## 2.4.6-p2

La versión de seguridad de Adobe Commerce 2.4.6-p2 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Aplicar parche para resolver la vulnerabilidad de seguridad CVE-2022-31160 en la biblioteca jQuery-UI

`jQuery-UI` La versión 1.13.1 de la biblioteca de tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Commerce y Magento Open Source. Esta biblioteca es una dependencia de Adobe Commerce y de los Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecuten implementaciones afectadas deben aplicar el parche especificado en la [Vulnerabilidad de seguridad de la IU de jQuery CVE-2022-31160 corregida para las versiones 2.4.4, 2.4.5 y 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Artículo de la Base de conocimiento.

### Aspecto destacado de seguridad

El valor de `fastcgi_pass` en el `nginx.sample` se ha devuelto a su valor anterior (anterior a 2.4.6-p1) de `fastcgi_backend`. Este valor se ha cambiado por error a `php-fpm:9000` en Adobe Commerce 2.4.6-p1.

### Revisiones incluidas en esta versión

Adobe Commerce 2.4.6-p2 incluye la resolución de la degradación del rendimiento a la que se dirigió el parche ACSD-51892. Los comerciantes no se ven afectados por el problema que resuelve este parche, que se describe en la sección [ACSD-51892: Problema de rendimiento donde los archivos de configuración se cargan varias veces](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html) Artículo de la Base de conocimiento.

## Adobe Commerce 2.4.6-p1

La versión de seguridad de Adobe Commerce 2.4.6-p1 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad y actualizaciones de la plataforma para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB23-35](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Aplicar parche para resolver la vulnerabilidad de seguridad CVE-2022-31160 en la biblioteca jQuery-UI

`jQuery-UI` La versión 1.13.1 de la biblioteca de tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Commerce y Magento Open Source. Esta biblioteca es una dependencia de Adobe Commerce y de los Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecuten implementaciones afectadas deben aplicar el parche especificado en la [Vulnerabilidad de seguridad de la IU de consulta CVE-2022-31160 para las versiones 2.4.4, 2.4.5 y 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Artículo de la Base de conocimiento.

#### Aspecto destacado de seguridad

El comportamiento predeterminado del [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL query y ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) El extremo REST ha cambiado. De forma predeterminada, la API ahora siempre devuelve `true`. Los comerciantes pueden activar el comportamiento original, que es devolver `true` si el correo electrónico no existe en la base de datos y `false` si existe. <!-- AC-6695 -->

### Actualizaciones de plataforma

Las actualizaciones de plataforma para esta versión mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

* **Compatibilidad con caché de barniz 7.3**. Esta versión es compatible con la última versión de Varnish Cache 7.3. La compatibilidad se mantiene con las versiones 6.0.x y 7.2.x, pero el Adobe recomendado con Adobe Commerce 2.4.6-p1 solo con Varnish Cache versión 7.3 o versión 6.0 LTS.

* **Compatibilidad con RabbitMQ 3.11**. Esta versión es compatible con la última versión de RabbitMQ 3.11. La compatibilidad sigue siendo con RabbitMQ 3.9, que es compatible hasta agosto de 2023, pero el Adobe recomendado usar Adobe Commerce 2.4.6-p1 solo con RabbitMQ 3.11.

* **Bibliotecas de JavaScript**. Las bibliotecas de JavaScript obsoletas se han actualizado a las últimas versiones secundarias o de parches, que incluyen `moment.js` biblioteca (v2.29.4), `jQuery UI` biblioteca (v1.13.2) y `jQuery` biblioteca de complementos de validación (versión 1.19.5).

### Problemas conocidos

* El `nginx.sample` se ha actualizado de forma involuntaria con un cambio que modifica el valor de `fastcgi_pass` de `fastcgi_backend` hasta `php-fpm:9000`. Este cambio se puede revertir o ignorar de forma segura. <!-- AC-8992 -->

* La falta de dependencias para el paquete de seguridad B2B provoca el siguiente error de instalación al instalar o actualizar la extensión B2B a 1.4.0.

  ```terminal
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Este problema se puede resolver añadiendo dependencias manuales para el paquete de seguridad B2B con un [etiqueta de estabilidad](https://getcomposer.org/doc/04-schema.md#package-links). Para obtener más información, consulte la [Notas de la versión B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html#known-issue).
