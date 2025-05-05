---
title: Notas de la versión del parche de seguridad de Adobe Systems Commerce 2.4.5
description: Obtenga información acerca de las correcciones de errores de seguridad, mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parche de seguridad para Adobe Systems versión 2.4.5 de Commerce.
exl-id: 1b5f6d84-877a-45ea-8ff5-db83e3d360dd
source-git-commit: 9bf1c539220d70a8e7fe449e4d91199f23cc23b2
workflow-type: tm+mt
source-wordcount: '1235'
ht-degree: 0%

---


# Notas de la versión para los parches de seguridad de Adobe Systems Commerce 2.4.5

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## 2.4.5-p12

La versión de seguridad de Adobe Systems Commerce 2.4.5-p12 proporciona correcciones de errores de seguridad para las vulnerabilidades identificadas en versiones anteriores de 2.4.5.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB25-26](https://helpx.adobe.com/es/security/products/magento/apsb25-26.html).

{{b2b-patches}}

## 2.4.5-p11

La versión de seguridad Adobe Systems Commerce 2.4.5-p11 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.5.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB25-08](https://helpx.adobe.com/es/security/products/magento/apsb25-08.html).

{{b2b-patches}}

### Resúmenes

{{$include /help/_includes/release-notes/highlights/security-2025-02.md}}

## 2.4.5-p10

La versión de seguridad Adobe Systems Commerce 2.4.5-p10 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.5.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB24-73](https://helpx.adobe.com/es/security/products/magento/apsb24-73.html).

{{b2b-patches}}

### Resúmenes

{{$include /help/_includes/release-notes/highlights/security-2024-10.md}}

### Correcciones incluidas en esta versión

{{$include /help/_includes/release-notes/hotfixes/included-2024-10.md}}

## 2.4.5-p9

La versión de seguridad de Adobe Systems Commerce 2.4.5-p9 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en versiones anteriores de 2.4.5.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB24-61](https://helpx.adobe.com/es/security/products/magento/apsb24-61.html).

### Características destacadas

{{$include /help/_includes/release-notes/highlights/security-2024-08.md}}

### Revisiones incluidas en esta versión

{{$include /help/_includes/release-notes/hotfixes/included-2024-08.md}}

## 2,4,5-p8

La versión de seguridad de Adobe Commerce 2.4.5-p8 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB24-40](https://helpx.adobe.com/es/security/products/magento/apsb24-40.html).

### Aplicar revisión para CVE-2024-34102

{{$include /help/_includes/release-notes/hotfixes/not-included-2024-06.md}}

### Platform actualizaciones

* **Soporte para MariaDB 10.5**. Esta versión de parche introduce compatibilidad con MariaDB versión 10.5. Adobe Systems Commerce sigue siendo compatible con la versión 10.4 de MariaDB, pero Adobe Systems recomienda usar Adobe Systems Commerce 2.4.5-p8 y todas las próximas versiones de parche solo de seguridad 2.4.5 solo con MariaDB versión 10.5 porque el mantenimiento de MariaDB 10.4 finaliza el 18 de junio de 2024. <!--AC-11530-->

### Resúmenes

{{$include /help/_includes/release-notes/highlights/2-4-7-security.md}}

## 2.4.5-p7

La versión de seguridad de Adobe Systems Commerce 2.4.5-p7 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB24-18](https://helpx.adobe.com/es/security/products/magento/apsb24-18.html).

## 2.4.5-p6

La versión de seguridad de Adobe Systems Commerce 2.4.5-p6 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5. Esta versión también incluye mejoras de seguridad para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB24-03](https://helpx.adobe.com/es/security/products/magento/apsb24-03.html).

### Características destacadas

Esta versión incorpora dos mejoras de seguridad significativas:

* **Cambios en el comportamiento de las claves de caché no generadas**:

   * Las claves de caché no generadas para bloques ahora incluyen prefijos que difieren de los prefijos para las claves generadas automáticamente. (Las claves de caché no generadas son claves que se establecen mediante sintaxis de directiva de plantilla para los métodos `setCacheKey` o `setData`).
   * Las claves de caché no generadas para bloques ahora deben contener solo letras, dígitos, guiones (-) y caracteres de subrayado (_).  <!-- AC-9831 -->

* **Limitaciones en el número de códigos** de cupón generados automáticamente. El comercio ahora limita el número de códigos de cupón que se generan automáticamente. El valor máximo predeterminado es 250.000. Los comerciantes pueden utilizar la nueva **[!UICONTROL Code Quantity Limit]** opción de configuración (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Promotions]**) para controlar este nuevo límite. <!-- AC-8753 -->

## 2.4.5-p5

La versión de seguridad de Adobe Systems Commerce 2.4.5-p5 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5. Esta versión también incluye mejoras de seguridad para mejorar el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín de seguridad APSB23-50](https://helpx.adobe.com/es/security/products/magento/apsb23-50.html).

### Resúmenes

Esta versión introduce una nueva opción de configuración de caché de Página completa que ayuda a mitigar los riesgos asociados con el `{BASE-URL}/page_cache/block/esi HTTP` extremo. Este extremo admite fragmentos de contenido cargados dinámicamente sin restricciones procedentes de controladores de diseño de comercio y estructuras de bloques. La nueva **[!UICONTROL Handles Param]** configuración establece el valor del `handles` parámetro de este extremo, que determina el número máximo permitido de identificadores por API. El valor predeterminado de este Propiedad es 100. Los comerciantes pueden cambiar este valor desde el Administrador (**[!UICONTROL Stores]** > **[!UICONTROL Settings:Configuration]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Handles Param]**). <!-- AC-9113 -->

### Problemas conocidos

**Problema**: Adobe Systems Commerce muestra un **error de suma** de comprobación incorrecto durante el descargar por Composer desde `repo.magento.com`, y se interrumpe la descargar del paquete. Este problema puede producirse durante descargar de paquetes de lanzamiento que estuvieron disponibles durante la `magento/module-page-cache` versión preliminar y está causado por un reempaquetado del paquete.

**Solución alternativa**: Los comerciantes que vean este error durante descargar pueden seguir estos pasos:

1) Eliminar el `/vendor` directorio dentro del proyecto, si existe.
2) Ejecute el `bin/magento composer update magento/module-page-cache` comando. Este comando actualiza sólo el `page cache` paquete.

Si el problema de suma de comprobación persiste, elimine el `composer.lock` archivo antes de volver a ejecutar el `bin/magento composer update` comando para actualizar todos los paquetes.

## 2.4.5-p4

La versión de seguridad de Adobe Commerce 2.4.5-p4 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB23-42](https://helpx.adobe.com/es/security/products/magento/apsb23-42.html).

### Aplicar revisión para CVE-2022-31160

La versión 1.13.1 de la biblioteca `jQuery-UI` tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Commerce y Magento Open Source. Este biblioteca es una dependencia de Adobe Systems Commerce y Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecutan implementaciones afectadas deben aplicar el parche especificado en el artículo de la Base de conocimiento sobre la vulnerabilidad de seguridad de IU de jQuery CVE-2022-31160 para las [versiones](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6) 2.4.4, 2.4.5 y 2.4.6.

## 2.4.5-p3

La versión de seguridad Adobe Systems Commerce 2.4.5-p3 proporciona correcciones de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5. Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente acerca de las correcciones de errores de seguridad, consulte [Adobe Systems boletín](https://helpx.adobe.com/es/security/products/magento/apsb23-35.html) de seguridad.

### Aplicar revisión para CVE-2022-31160

`jQuery-UI` biblioteca versión 1.13.1 tiene una vulnerabilidad de seguridad conocida (CVE-2022-31160) que afecta a varias versiones de Adobe Systems Commerce y Magento Open Source. Este biblioteca es una dependencia de Adobe Systems Commerce y Magento Open Source 2.4.4, 2.4.5 y 2.4.6. Los comerciantes que ejecutan implementaciones afectadas deben aplicar el parche especificado en el artículo de Knowledge Base CVE-2022-31160 [sobre la vulnerabilidad de seguridad de Query IU para las versiones](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/jquery-cve-2022-31160-fix-2-4-4-2-4-5-2-4-6) 2.4.4, 2.4.5 y 2.4.6.

### Resúmenes

El comportamiento predeterminado del punto final REST [`isEmailAvailable`](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/is-email-available/) consulta y ([`V1/customers/isEmailAvailable`](https://adobe-commerce.redoc.ly/2.4.6-admin/tag/customersisEmailAvailable/#operation/PostV1CustomersIsEmailAvailable)) de GraphQL ha cambiado. De forma predeterminada, la API ahora siempre devuelve `true`. Los comerciantes pueden habilitar el comportamiento original, que es devolver `true` si el correo electrónico no existe en la base de datos y `false` si existe. <!-- AC-6695 -->

### Platform actualizaciones

Platform actualizaciones de esta versión mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

* **Soporte de caché de barniz 7.3**. Esta versión es compatible con la última versión de Varnish Cache 7.3. Compatibilidad mantiene con las versiones 6.0.x y 7.2.x, pero recomendamos usar Adobe Systems Commerce 2.4.5-p3 solo con Varnish Cache versión 7.3 o versión 6.0 LTS.

* **Compatibilidad con** RabbitMQ 3.11. Esta versión es compatible con la última versión de RabbitMQ 3.11. Compatibilidad permanece con RabbitMQ 3.9, que es compatible hasta agosto de 2023, pero recomendamos usar Adobe Systems Commerce 2.4.5-p3 solo con RabbitMQ 3.11.

* **JavaScript bibliotecas**. Los bibliotecas de JavaScript obsoletos se han actualizado a las últimas versiones secundarias o parche, incluidas `moment.js` biblioteca (v2.29.4), `jQuery UI` biblioteca (v1.13.2) y `jQuery` validación plug-in biblioteca (v1.19.5).

## 2.4.5-p2

La versión de seguridad Adobe Systems Commerce 2.4.5-p2 proporciona tres correcciones de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB23-17](https://helpx.adobe.com/es/security/products/magento/apsb23-17.html).

## 2,4,5-p1

La versión de seguridad de Adobe Commerce 2.4.5-p1 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores de 2.4.5.

Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad de Adobe APSB22-48](https://helpx.adobe.com/es/security/products/magento/apsb22-48.html).

Una de las correcciones de errores de seguridad incluyó la creación de una nueva configuración. La **opción Requerir confirmación de correo electrónico si se ha cambiado** correo electrónico configuración permite a los administradores solicitar confirmación correo electrónico cuando un usuario de administración cambia su dirección correo electrónico. <!-- AC-6292-->
