---
title: Notas de la versión de los parches de seguridad de Adobe Commerce 2.4.3
description: Obtenga información acerca de las correcciones de errores de seguridad, las mejoras de seguridad y otras actualizaciones relacionadas con la seguridad incluidas en las versiones de parches de seguridad para Adobe Commerce 2.4.3.
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 0%

---

# Notas de la versión de Adobe Commerce 2.4.3 Security Patch

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.3-p3

La versión de seguridad de Adobe Commerce 2.4.3-p3 proporciona correcciones de seguridad para vulnerabilidades identificadas en la versión anterior (Adobe Commerce 2.4.3 y Magento Open Source 2.4.3). Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB22-38](https://helpx.adobe.com/security/products/magento/apsb22-38.html).


### Aplicar `AC-3022.patch` para seguir ofreciendo DHL como transportista

DHL ha introducido la versión de esquema 6.2 y dejará de utilizar la versión de esquema 6.0 en un futuro próximo. Adobe Commerce 2.4.4 y las versiones anteriores compatibles con la integración de DHL solo admiten la versión 6.0. Los comerciantes que implementen estas versiones deben aplicar `AC-3022.patch` lo antes posible para seguir ofreciendo DHL como transportista. Consulte la [Aplicar un parche para seguir ofreciendo DHL como transportista](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Artículo de Knowledge Base para obtener información sobre cómo descargar e instalar el parche.

### Aspectos destacados de seguridad

* Los recursos ACL se han agregado al inventario.
* Se ha mejorado la seguridad de la plantilla de inventario.

## Adobe Commerce 2.4.3-p2

La versión de seguridad de Adobe Commerce 2.4.3-p2 proporciona correcciones de errores de seguridad para vulnerabilidades que se han identificado en versiones anteriores. Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.

Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB22-13](https://helpx.adobe.com/security/products/magento/apsb22-13.html).  La versión del parche también resuelve la vulnerabilidad de `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`,`MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch`, y `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch`.


### Aplicar `AC-3022.patch` para seguir ofreciendo DHL como transportista

DHL ha introducido la versión de esquema 6.2 y dejará de utilizar la versión de esquema 6.0 en un futuro próximo. Adobe Commerce 2.4.4 y las versiones anteriores compatibles con la integración de DHL solo admiten la versión 6.0. Los comerciantes que implementen estas versiones deben aplicar `AC-3022.patch` lo antes posible para seguir ofreciendo DHL como transportista. Consulte la [Aplicar un parche para seguir ofreciendo DHL como transportista](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Artículo de Knowledge Base para obtener información sobre cómo descargar e instalar el parche.


### Aspectos destacados de seguridad

* El uso de variables de correo electrónico volvió a quedar obsoleto en la versión 2.3.4 como parte de una mitigación del riesgo de seguridad en favor de una sintaxis de variables más estricta. Este comportamiento heredado se ha eliminado por completo en esta versión como continuación de la mitigación de riesgos de seguridad.

  Como resultado, es posible que las plantillas de correo electrónico o de newsletter que funcionaban en versiones anteriores no funcionen correctamente después de actualizar a Adobe Commerce 2.4.3-p2. Las plantillas afectadas incluyen invalidaciones de administración, temáticas, temáticas secundarias y plantillas de módulos personalizados o extensiones de terceros. Su implementación puede seguir viéndose afectada incluso después de utilizar el [Actualizar herramienta de compatibilidad](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html?lang=en) para corregir usos obsoletos. Consulte [Migración de plantillas de correo electrónico personalizadas](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/) para obtener información sobre los posibles efectos y las directrices para migrar plantillas afectadas.

* Los tokens de acceso de OAuth y los tokens de restablecimiento de contraseña ahora se cifran cuando se almacenan en la base de datos. <!-- AC-520 1323-->

* La validación se ha reforzado para evitar la carga de extensiones de archivo no alfanuméricas. <!-- AC-479-->

* Swagger ahora está desactivado de forma predeterminada cuando Adobe Commerce está en modo de producción. <!-- AC-1450-->

* Los desarrolladores ahora pueden configurar el límite de tamaño de las matrices aceptadas por los extremos RESTful de Adobe Commerce en función del extremo. Consulte [Seguridad de API](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-465-->

* Se han añadido mecanismos para limitar el tamaño y el número de recursos que un usuario puede solicitar a través de una API web en todo el sistema y para anular los valores predeterminados en módulos individuales. Esta mejora resuelve el problema abordado por `MC-43048__set_rate_limits__2.4.3.patch`. Consulte [Seguridad de API](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-1120-->


## 2.4.3-p1

La versión de seguridad de Adobe Commerce 2.4.3-p1 proporciona correcciones de errores de seguridad para vulnerabilidades identificadas en la versión anterior (Adobe Commerce 2.4.3 y Magento Open Source 2.4.3). Esta versión también incluye mejoras de seguridad que mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes.


Para obtener la información más reciente sobre las correcciones de errores de seguridad, consulte [Boletín de Seguridad del Adobe APSB21-86](https://helpx.adobe.com/security/products/magento/apsb21-86.html). La versión del parche también proporciona correcciones de errores para [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html), [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html), y [Vértice](https://marketplace.magento.com/vertexinc-vertex-tax-module.html) extensiones desarrolladas por el proveedor.


### Aplicar `AC-3022.patch` para seguir ofreciendo DHL como transportista

DHL ha introducido la versión de esquema 6.2 y dejará de utilizar la versión de esquema 6.0 en un futuro próximo. Adobe Commerce 2.4.4 y las versiones anteriores compatibles con la integración de DHL solo admiten la versión 6.0. Los comerciantes que implementen estas versiones deben aplicar `AC-3022.patch` lo antes posible para seguir ofreciendo DHL como transportista. Consulte la [Aplicar un parche para seguir ofreciendo DHL como transportista](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Artículo de Knowledge Base para obtener información sobre cómo descargar e instalar el parche.

### Revisiones

Esta versión incluye la siguiente revisión y todas las revisiones publicadas para la versión anterior del parche.

* Parche `AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`. Consulte la [Adobe Commerce actualización 2.4.3, 2.3.7-p1 PHP Error fatal revisión](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix) Artículo de la Base de conocimiento para obtener información sobre el parche y el problema.

### Aspectos destacados de seguridad

**Los ID de sesión se han eliminado de la base de datos**. Este cambio de código puede provocar cambios importantes si los comerciantes tienen personalizaciones o extensiones instaladas que utilizan los ID de sesión sin procesar almacenados en la base de datos. <!-- MC-40976-->

**Acceso de administrador restringido a las carpetas de la Galería multimedia**. Los permisos predeterminados de la Galería multimedia ahora solo permiten operaciones de directorio (ver, cargar, eliminar y crear) permitidas explícitamente por la configuración. Los usuarios administradores ya no pueden acceder a los recursos multimedia a través de la Galería multimedia que se cargaron fuera de `catalog/category` o `wysiwyg` directorios. Los administradores que deseen acceder a los recursos de medios deben moverlos a una carpeta permitida explícitamente o ajustar su configuración. Consulte [Modificar permisos de carpeta de Media Library](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/). <!-- B2B-1897-->

**Límites reducidos a la complejidad de las consultas GraphQL**. Se ha reducido la complejidad máxima de consulta permitida de GraphQL para evitar ataques de denegación de servicio (DOS). Consulte [Configuración de seguridad de GraphQL](https://devdocs.magento.com/guides/v2.4/graphql/security-configuration.html). <!-- PWA-1700-->

**Vulnerabilidades recientes en las pruebas de penetración** se han corregido en esta versión. <!-- MC-42431-->

La expresión de origen no admitida `unsafe-inline` se ha eliminado de la directiva de seguridad de contenido `frame-ancestors` Directiva. [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->

