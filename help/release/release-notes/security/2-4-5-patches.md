---
title: Notas de la versión de Adobe Commerce 2.4.5 Security Patch
description: Obtenga información acerca de las correcciones de errores de seguridad, las mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parches de seguridad para Adobe Commerce 2.4.5.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 6c8d686fd3a7ce76f966b9f390813f454aa093bf
workflow-type: tm+mt
source-wordcount: '1111'
ht-degree: 0%

---


# Notas de la versión de parches de seguridad de Adobe Commerce 2.4.5

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.5-p8

La versión de seguridad de Adobe Commerce 2.4.5-p8 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad del Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Aplicar revisión para CVE-2024-34102

{{$include /help/_includes/release-notes/2024-06/hotfixes-not-included.md}}

### Actualizaciones de plataforma

* **Compatibilidad con MariaDB 10.5**. Esta versión del parche presenta compatibilidad con MariaDB versión 10.5. Adobe Commerce sigue siendo compatible con la versión 10.4 de MariaDB, pero el Adobe recomienda utilizar Adobe Commerce 2.4.5-p8 y todas las próximas versiones de parches de solo seguridad 2.4.5 solo con la versión 10.5 de MariaDB porque el mantenimiento de MariaDB 10.4 finaliza el 18 de junio de 2024. <!--AC-11530-->

### Mejoras de seguridad adicionales

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## Adobe Commerce 2.4.5-p7

La versión de seguridad de Adobe Commerce 2.4.5-p7 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad del Adobe APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.5-p6

La versión de seguridad de Adobe Commerce 2.4.5-p6 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5. Esta versión también incluye mejoras de seguridad para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad del Adobe APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Aspectos destacados de seguridad

Esta versión incorpora dos mejoras de seguridad significativas:

* **Cambios en el comportamiento de las claves de caché no generadas**:

   * Las claves de caché no generadas para bloques ahora incluyen prefijos que difieren de los prefijos para las claves generadas automáticamente. (Las claves de caché no generadas son claves que se establecen mediante sintaxis de directiva de plantilla para los métodos `setCacheKey` o `setData`).
   * Las claves de caché no generadas para bloques ahora deben contener solo letras, dígitos, guiones (-) y caracteres de subrayado (_). <!-- AC-9831 -->

* **Limitaciones en el número de códigos de cupones generados automáticamente**. Commerce ahora limita el número de códigos de cupones que se generan automáticamente. El máximo predeterminado es 250 000. Los comerciantes pueden usar la nueva opción de configuración **[!UICONTROL Code Quantity Limit]** (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) para controlar este nuevo límite. <!-- AC-8753 -->



## Adobe Commerce 2.4.5-p5

La versión de seguridad de Adobe Commerce 2.4.5-p5 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5. Esta versión también incluye mejoras de seguridad para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad del Adobe APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Aspecto destacado de seguridad

Esta versión introduce una nueva configuración de caché de página completa que ayuda a mitigar los riesgos asociados con el extremo `{BASE-URL}/page_cache/block/esi HTTP`. Este extremo admite fragmentos de contenido cargados dinámicamente y sin restricciones desde controladores de diseño y estructuras de bloque de Commerce. La nueva configuración **[!UICONTROL Handles Param]** establece el valor del parámetro `handles` de este extremo, que determina el número máximo permitido de identificadores por API. El valor predeterminado de esta propiedad es 100. Los comerciantes pueden cambiar este valor desde el administrador (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Problema conocido

**Problema**: Adobe Commerce muestra un error de **suma de comprobación incorrecta** durante la descarga por Compositor desde `repo.magento.com` y la descarga del paquete se interrumpe. Este problema puede ocurrir durante la descarga de paquetes de versiones que estaban disponibles durante la versión preliminar y que se debe a un reempaquetado del paquete `magento/module-page-cache`.

**Solución alternativa**: Los comerciantes que ven este error durante la descarga pueden seguir estos pasos:

1) Elimine el directorio `/vendor` dentro del proyecto, si existe.
2) Ejecute el comando `bin/magento composer update magento/module-page-cache`. Este comando actualiza solamente el paquete `page cache`.

Si el problema de la suma de comprobación persiste, quite el archivo `composer.lock` antes de volver a ejecutar el comando `bin/magento composer update` para actualizar todos los paquetes.

## Adobe Commerce 2.4.5-p4

La versión de seguridad de Adobe Commerce 2.4.5-p4 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad del Adobe APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Aplicar parche para resolver la vulnerabilidad de seguridad CVE-2022-31160 en la biblioteca jQuery-UI

La versión 1.13.1 de la biblioteca `jQuery-UI` tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Commerce y Magento Open Source. Esta biblioteca es una dependencia de Adobe Commerce y de los Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecuten implementaciones afectadas deben aplicar el parche especificado en la corrección de la vulnerabilidad de seguridad de la interfaz de usuario de [jQuery CVE-2022-31160 para las versiones 2.4.4, 2.4.5 y 2.4.6](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6) del artículo de la Base de conocimiento.

## Adobe Commerce 2.4.5-p3

La versión de seguridad de Adobe Commerce 2.4.5-p3 proporciona correcciones de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.5. Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de seguridad de Adobe](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Aplicar parche para resolver la vulnerabilidad de seguridad CVE-2022-31160 en la biblioteca jQuery-UI

La versión 1.13.1 de la biblioteca `jQuery-UI` tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Commerce y Magento Open Source. Esta biblioteca es una dependencia de Adobe Commerce y de los Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecuten implementaciones afectadas deben aplicar el parche especificado en el artículo [Vulnerabilidad de seguridad de la IU de consulta CVE-2022-31160 para las versiones 2.4.4, 2.4.5 y 2.4.6](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6) de la Base de conocimiento.

### Aspecto destacado de seguridad

El comportamiento predeterminado de la consulta GraphQL [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) y el extremo REST ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) ha cambiado. De manera predeterminada, la API ahora siempre devuelve `true`. Los comerciantes pueden habilitar el comportamiento original, que consiste en devolver `true` si el correo electrónico no existe en la base de datos y `false` si existe. <!-- AC-6695 -->

### Actualizaciones de plataforma

Las actualizaciones de plataforma para esta versión mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

* **Compatibilidad con Varnish cache 7.3**. Esta versión es compatible con la última versión de Varnish Cache 7.3. La compatibilidad se mantiene con las versiones 6.0.x y 7.2.x, pero recomendamos usar Adobe Commerce 2.4.5-p3 solo con Varnish Cache versión 7.3 o versión 6.0 LTS.

* **Compatibilidad con RabbitMQ 3.11**. Esta versión es compatible con la última versión de RabbitMQ 3.11. La compatibilidad sigue siendo con RabbitMQ 3.9, compatible hasta agosto de 2023, pero recomendamos utilizar Adobe Commerce 2.4.5-p3 solo con RabbitMQ 3.11.

* **Bibliotecas de JavaScript**. Las bibliotecas JavaScript obsoletas se han actualizado a las últimas versiones secundarias o de parches, incluidas la biblioteca `moment.js` (v2.29.4), la biblioteca `jQuery UI` (v1.13.2) y la biblioteca de complementos de validación `jQuery` (v1.19.5).

## Notas de la versión de Adobe Commerce 2.4.5-p2

La versión de seguridad de Adobe Commerce 2.4.5-p2 proporciona tres correcciones de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad del Adobe APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## Adobe Commerce 2.4.5-p1

La versión de seguridad de Adobe Commerce 2.4.5-p1 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad del Adobe APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

Una de las correcciones de errores de seguridad incluía la creación de una nueva configuración. La opción de configuración **Requerir confirmación por correo electrónico si se ha cambiado el correo electrónico** permite a los administradores solicitar confirmación por correo electrónico cuando un usuario administrador cambia su dirección de correo electrónico. <!-- AC-6292-->
