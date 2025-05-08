---
title: Notas de la versión de Adobe Commerce 2.4.6 Security Patch
description: Obtenga información acerca de las correcciones de errores de seguridad, las mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parches de seguridad para Adobe Commerce 2.4.6.
exl-id: cde096ac-d192-490d-873a-475996c474ff
source-git-commit: 55bba84f05042667d0de3aa053e9a52119bd2599
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 0%

---


# Notas de la versión de parches de seguridad de Adobe Commerce 2.4.6

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2,4,6-p10

La versión de seguridad de Adobe Commerce 2.4.6-p10 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.6.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB25-26](https://helpx.adobe.com/es/security/products/magento/apsb25-26.html).

{{b2b-patches}}

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2025-04.md}}

## 2.4.6-p9

La versión de seguridad de Adobe Commerce 2.4.6-p9 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.6.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB25-08](https://helpx.adobe.com/es/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.6-p8

La versión de seguridad de Adobe Commerce 2.4.6-p8 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.6.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB24-73](https://helpx.adobe.com/es/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Revisiones incluidas en esta versión

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.6-p7

La versión de seguridad de Adobe Commerce 2.4.6-p7 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.6.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB24-61](https://helpx.adobe.com/es/security/products/magento/apsb24-61.html).

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Revisiones incluidas en esta versión

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2.4.6-p6

La versión de seguridad de Adobe Commerce 2.4.6-p6 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.6.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB24-40](https://helpx.adobe.com/es/security/products/magento/apsb24-40.html).

Para ser compatibles con Commerce versión 2.4.6-p6, los comerciantes que tengan la extensión Adobe Commerce B2B deben actualizar a [B2B versión 1.4.2-p1](https://experienceleague.adobe.com/es/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Aplicar revisión para CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

Para ser compatibles con Commerce versión 2.4.6-p6, los comerciantes que tengan la extensión Adobe Commerce B2B deben actualizar a [B2B versión 1.4.2-p1](https://experienceleague.adobe.com/es/docs/commerce-admin/b2b/release-notes#b2b-v142-p1).

### Características destacadas

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.6-p5

La versión de seguridad de Adobe Commerce 2.4.6-p5 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.6.

Para obtener la información más reciente sobre estas correcciones, consulte el [Boletín de seguridad de Adobe APSB24-18](https://helpx.adobe.com/es/security/products/magento/apsb24-18.html).

## 2.4.6-p4

La versión de seguridad de Adobe Commerce 2.4.6-p4 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB24-03](https://helpx.adobe.com/es/security/products/magento/apsb24-03.html).

### Características destacadas

Esta versión incorpora dos mejoras de seguridad significativas:

* **Cambios en el comportamiento de las claves de caché no generadas**:

   * Las claves de caché no generadas para bloques ahora incluyen prefijos que difieren de los prefijos para las claves generadas automáticamente. (Las claves de caché no generadas son claves que se establecen mediante sintaxis de directiva de plantilla para los métodos `setCacheKey` o `setData`).
   * Las claves de caché no generadas para bloques ahora deben contener solo letras, dígitos, guiones (-) y caracteres de subrayado (_). <!-- AC-9831 -->

* **Limitaciones en el número de códigos de cupones generados automáticamente**. Commerce ahora limita el número de códigos de cupones que se generan automáticamente. El máximo predeterminado es 250 000. Los comerciantes pueden usar la nueva opción de configuración **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) para controlar este nuevo límite. <!-- AC-8753 -->

## 2.4.6-p3

La versión de seguridad de Adobe Commerce 2.4.6-p3 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de seguridad, consulte [Boletín de seguridad de Adobe APSB23-50](https://helpx.adobe.com/es/security/products/magento/apsb23-50.html).

### Características destacadas

Esta versión introduce una nueva configuración de caché de página completa que ayuda a mitigar los riesgos asociados con el extremo `{BASE-URL}/page_cache/block/esi HTTP`. Este extremo admite fragmentos de contenido cargados dinámicamente y sin restricciones desde controladores de diseño y estructuras de bloque de Commerce. La nueva configuración **[!UICONTROL Handles Param]** establece el valor del parámetro `handles` de este extremo, que determina el número máximo permitido de identificadores por API. El valor predeterminado de esta propiedad es 100. Los comerciantes pueden cambiar este valor desde el administrador (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**. <!-- AC-9113 -->

### Revisiones incluidas en esta versión

Adobe Commerce 2.4.6-p3 incluye la resolución de la degradación del rendimiento corregida por el parche ACSD-51892. Los comerciantes no se ven afectados por el problema que resuelve este parche, que se describe en [ACSD-51892: Problema de rendimiento donde los archivos de configuración se cargan varias veces](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html?lang=es) Artículo de la Base de conocimiento.

### Problemas conocidos

**Problema**: Adobe Commerce muestra un error de `wrong checksum` durante la descarga por Compositor desde `repo.magento.com` y se interrumpe la descarga del paquete. Este problema puede ocurrir durante la descarga de los paquetes de versiones disponibles durante el período de prelanzamiento y se debe a un reempaquetado del paquete `magento/module-page-cache`.

**Solución alternativa**: Los comerciantes que ven este error durante la descarga pueden seguir estos pasos:

1) Elimine el directorio `/vendor` dentro del proyecto, si existe.
2) Ejecute el comando `bin/magento composer update magento/module-page-cache`. Este comando actualiza solamente el paquete `page cache`.

Si el problema de la suma de comprobación persiste, quite el archivo `composer.lock` antes de volver a ejecutar el comando `bin/magento composer update` para actualizar todos los paquetes.

## 2.4.6-p2

La versión de seguridad de Adobe Commerce 2.4.6-p2 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB23-42](https://helpx.adobe.com/es/security/products/magento/apsb23-42.html).

### Aplicar revisión para CVE-2022-31160

La versión 1.13.1 de la biblioteca `jQuery-UI` tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Commerce y Magento Open Source. Esta biblioteca es una dependencia de Adobe Commerce y Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecuten implementaciones afectadas deben aplicar el parche especificado en la corrección de la vulnerabilidad de seguridad de la interfaz de usuario de [jQuery CVE-2022-31160 para las versiones 2.4.4, 2.4.5 y 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=es) del artículo de la Base de conocimiento.

### Características destacadas

El valor de `fastcgi_pass` en el archivo `nginx.sample` se ha devuelto a su valor anterior (anterior a 2.4.6-p1) de `fastcgi_backend`. Este valor se cambió involuntariamente a `php-fpm:9000` en Adobe Commerce 2.4.6-p1.

### Revisiones incluidas en esta versión

Adobe Commerce 2.4.6-p2 incluye la resolución de la degradación del rendimiento a la que se dirigió el parche ACSD-51892. Los comerciantes no se ven afectados por el problema que resuelve este parche, que se describe en [ACSD-51892: Problema de rendimiento donde los archivos de configuración se cargan varias veces](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-33/acsd-51892-performance-issue-where-config-files-load-multiple-times.html?lang=es) Artículo de la Base de conocimiento.

## 2.4.6-p1

La versión de seguridad de Adobe Commerce 2.4.6-p1 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad y actualizaciones de la plataforma para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB23-35](https://helpx.adobe.com/es/security/products/magento/apsb23-35.html).

### Aplicar revisión para CVE-2022-31160

La versión 1.13.1 de la biblioteca `jQuery-UI` tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Commerce y Magento Open Source. Esta biblioteca es una dependencia de Adobe Commerce y Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecuten implementaciones afectadas deben aplicar el parche especificado en el artículo [Vulnerabilidad de seguridad de la IU de consulta CVE-2022-31160 para las versiones 2.4.4, 2.4.5 y 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html?lang=es) de la Base de conocimiento.

#### Resaltar

El comportamiento predeterminado de la consulta GraphQL [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) y el extremo REST ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) ha cambiado. De manera predeterminada, la API ahora siempre devuelve `true`. Los comerciantes pueden habilitar el comportamiento original, que consiste en devolver `true` si el correo electrónico no existe en la base de datos y `false` si existe. <!-- AC-6695 -->

### Actualizaciones de plataforma

Las actualizaciones de plataforma para esta versión mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

* **Compatibilidad con Varnish cache 7.3**. Esta versión es compatible con la última versión de Varnish Cache 7.3. La compatibilidad sigue siendo con las versiones 6.0.x y 7.2.x, pero Adobe recomienda utilizar Adobe Commerce 2.4.6-p1 solo con Varnish Cache versión 7.3 o versión 6.0 LTS.

* **Compatibilidad con RabbitMQ 3.11**. Esta versión es compatible con la última versión de RabbitMQ 3.11. La compatibilidad sigue siendo con RabbitMQ 3.9, que es compatible hasta agosto de 2023, pero Adobe recomienda utilizar Adobe Commerce 2.4.6-p1 solo con RabbitMQ 3.11.

* **Bibliotecas de JavaScript**. Las bibliotecas JavaScript obsoletas se han actualizado a las últimas versiones secundarias o de parches, incluidas la biblioteca `moment.js` (v2.29.4), la biblioteca `jQuery UI` (v1.13.2) y la biblioteca de complementos de validación `jQuery` (v1.19.5).

### Problemas conocidos

* El archivo `nginx.sample` se actualizó de forma involuntaria con un cambio que modifica el valor de `fastcgi_pass` de `fastcgi_backend` a `php-fpm:9000`. Este cambio se puede revertir o ignorar de forma segura. <!-- AC-8992 -->

* La falta de dependencias para el paquete de seguridad B2B provoca el siguiente error de instalación al instalar o actualizar la extensión B2B a 1.4.0.

  ```
  Your requirements could not be resolved to an installable set of packages.
  
    Problem 1
      - Root composer.json requires magento/extension-b2b 1.4.0 -> satisfiable by magento/extension-b2b[1.4.0].
      - magento/extension-b2b 1.4.0 requires magento/security-package-b2b 1.0.4-beta1 -> found magento/security-package-b2b[1.0.4-beta1] but it does not match your minimum-stability.
  
  Installation failed, reverting ./composer.json and ./composer.lock to their original content.
  ```

  Este problema se puede resolver agregando dependencias manuales para el paquete de seguridad B2B con una [etiqueta de estabilidad](https://getcomposer.org/doc/04-schema.md#package-links). Para obtener más información, consulte las [notas de la versión de B2B](https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html?lang=es#known-issue).
