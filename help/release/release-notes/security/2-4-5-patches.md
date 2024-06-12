---
title: Notas de la versión de Adobe Commerce 2.4.5 Security Patch
description: Obtenga información acerca de las correcciones de errores de seguridad, las mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parches de seguridad para Adobe Commerce 2.4.5.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 59a5306c8329ddc3ca2a2e086f5ebe81b49eab3a
workflow-type: tm+mt
source-wordcount: '1095'
ht-degree: 0%

---


# Notas de la versión de parches de seguridad de Adobe Commerce 2.4.5

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.5-p8

La versión de seguridad de Adobe Commerce 2.4.5-p7 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB24-40](https://helpx.adobe.com/security/products/magento/apsb24-40.html).

### Actualizaciones de plataforma

* **Compatibilidad con MariaDB 10.5**. Esta versión del parche presenta compatibilidad con MariaDB versión 10.5. Adobe Commerce sigue siendo compatible con MariaDB versión 10.4, pero Adobe recomienda utilizar Adobe Commerce 2.4.5-p8 y todas las próximas versiones de parches solo de seguridad 2.4.5 solo con MariaDB versión 10.5 porque el mantenimiento de MariaDB 10.4 finaliza el 18 de junio de 2024. <!--AC-11530-->

### Mejoras de seguridad adicionales

{{$include /help/_includes/release-notes/2-4-7-security.md}}

## Adobe Commerce 2.4.5-p7

La versión de seguridad de Adobe Commerce 2.4.5-p7 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB24-18](https://helpx.adobe.com/security/products/magento/apsb24-18.html).

## Adobe Commerce 2.4.5-p6

La versión de seguridad de Adobe Commerce 2.4.5-p6 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB24-03](https://helpx.adobe.com/security/products/magento/apsb24-03.html).

### Aspectos destacados de seguridad

Esta versión incorpora dos mejoras de seguridad significativas:

* **Cambios en el comportamiento de las claves de caché no generadas**:

   * Las claves de caché no generadas para bloques ahora incluyen prefijos que difieren de los prefijos para las claves generadas automáticamente. (Las claves de caché no generadas son claves que se establecen mediante sintaxis de directiva de plantilla o la variable `setCacheKey` o `setData` métodos.)
   * Las claves de caché no generadas para bloques ahora solo deben contener letras, dígitos, guiones (-) y caracteres de subrayado (_).  <!-- AC-9831 -->

* **Limitaciones en el número de códigos de cupones generados automáticamente**. Commerce ahora limita el número de códigos de cupones que se generan automáticamente. El máximo predeterminado es 250 000. Los comerciantes pueden utilizar el nuevo **[!UICONTROL Code Quantity Limit]** opción de configuración (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) para controlar este nuevo límite. <!-- AC-8753 -->



## Adobe Commerce 2.4.5-p5

La versión de seguridad de Adobe Commerce 2.4.5-p5 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB23-50](https://helpx.adobe.com/security/products/magento/apsb23-50.html).

### Aspecto destacado de seguridad

Esta versión introduce una nueva configuración de caché de página completa que ayuda a mitigar los riesgos asociados con el `{BASE-URL}/page_cache/block/esi HTTP` punto final. Este extremo admite fragmentos de contenido cargados dinámicamente y sin restricciones desde controladores de diseño y estructuras de bloque de Commerce. El nuevo **[!UICONTROL Handles Param]** La configuración de establece el valor del punto de conexión `handles` , que determina el número máximo permitido de identificadores por API. El valor predeterminado de esta propiedad es 100. Los comerciantes pueden cambiar este valor desde el Administrador (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Problema conocido

**Problema**: Adobe Commerce muestra un **suma de comprobación incorrecta** error durante la descarga por Compositor desde `repo.magento.com`y se interrumpe la descarga del paquete. Este problema puede producirse durante la descarga de los paquetes de versiones preliminares que estaban disponibles durante la versión preliminar y que se debe a un reempaquetado del `magento/module-page-cache` paquete.

**Solución**: Los comerciantes que ven este error durante la descarga pueden seguir estos pasos:

1) Elimine el `/vendor` dentro del proyecto, si existe.
2) Ejecute el `bin/magento composer update magento/module-page-cache` comando. Este comando actualiza solo la variable `page cache` paquete.

Si el problema de la suma de comprobación persiste, elimine la `composer.lock` antes de volver a ejecutar el `bin/magento composer update` para actualizar cada paquete.

## Adobe Commerce 2.4.5-p4

La versión de seguridad de Adobe Commerce 2.4.5-p4 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB23-42](https://helpx.adobe.com/security/products/magento/apsb23-42.html).

### Aplicar parche para resolver la vulnerabilidad de seguridad CVE-2022-31160 en la biblioteca jQuery-UI

`jQuery-UI` La versión 1.13.1 de la biblioteca de tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Commerce y Magento Open Source. Esta biblioteca es una dependencia de Adobe Commerce y de los Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecuten implementaciones afectadas deben aplicar el parche especificado en la [Vulnerabilidad de seguridad de la IU de jQuery CVE-2022-31160 corregida para las versiones 2.4.4, 2.4.5 y 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Artículo de la Base de conocimiento.

## Adobe Commerce 2.4.5-p3

La versión de seguridad de Adobe Commerce 2.4.5-p3 proporciona correcciones de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de seguridad del Adobe](https://helpx.adobe.com/security/products/magento/apsb23-35.html).

### Aplicar parche para resolver la vulnerabilidad de seguridad CVE-2022-31160 en la biblioteca jQuery-UI

`jQuery-UI` La versión 1.13.1 de la biblioteca de tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Commerce y Magento Open Source. Esta biblioteca es una dependencia de Adobe Commerce y de los Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecuten implementaciones afectadas deben aplicar el parche especificado en la [Vulnerabilidad de seguridad de la IU de consulta CVE-2022-31160 para las versiones 2.4.4, 2.4.5 y 2.4.6](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2.4.4-2.4.5-2.4.6.html) Artículo de la Base de conocimiento.

### Aspecto destacado de seguridad

El comportamiento predeterminado del [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) GraphQL query y ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) El extremo REST ha cambiado. De forma predeterminada, la API ahora siempre devuelve `true`. Los comerciantes pueden activar el comportamiento original, que es devolver `true` si el correo electrónico no existe en la base de datos y `false` si existe. <!-- AC-6695 -->

### Actualizaciones de plataforma

Las actualizaciones de plataforma para esta versión mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

* **Compatibilidad con caché de barniz 7.3**. Esta versión es compatible con la última versión de Varnish Cache 7.3. La compatibilidad se mantiene con las versiones 6.0.x y 7.2.x, pero recomendamos usar Adobe Commerce 2.4.5-p3 solo con Varnish Cache versión 7.3 o versión 6.0 LTS.

* **Compatibilidad con RabbitMQ 3.11**. Esta versión es compatible con la última versión de RabbitMQ 3.11. La compatibilidad sigue siendo con RabbitMQ 3.9, compatible hasta agosto de 2023, pero recomendamos utilizar Adobe Commerce 2.4.5-p3 solo con RabbitMQ 3.11.

* **Bibliotecas de JavaScript**. Las bibliotecas de JavaScript obsoletas se han actualizado a las últimas versiones secundarias o de parches, que incluyen `moment.js` biblioteca (v2.29.4), `jQuery UI` biblioteca (v1.13.2) y `jQuery` biblioteca de complementos de validación (versión 1.19.5).

## Notas de la versión de Adobe Commerce 2.4.5-p2

La versión de seguridad de Adobe Commerce 2.4.5-p2 proporciona tres correcciones de seguridad para vulnerabilidades que se han identificado en versiones anteriores.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB23-17](https://helpx.adobe.com/security/products/magento/apsb23-17.html).

## Adobe Commerce 2.4.5-p1

La versión de seguridad de Adobe Commerce 2.4.5-p1 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en la versión anterior (Adobe Commerce 2.4.5 y Magento Open Source 2.4.5).

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB22-48](https://helpx.adobe.com/security/products/magento/apsb22-48.html).

Una de las correcciones de errores de seguridad incluía la creación de una nueva configuración. El **Requerir confirmación por correo electrónico si el correo electrónico se ha cambiado** La configuración de permite a los administradores solicitar confirmación por correo electrónico cuando un usuario administrador cambia su dirección de correo electrónico. <!-- AC-6292-->
