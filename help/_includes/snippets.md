---
source-git-commit: c8a20ad1b0b57724f389cfa5c63f6ae542758c2b
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---
# Fragmentos

## Solo Commerce {#commerce-only}

>[!NOTE]
>
>[!DNL Upgrade Compatibility Tool] solo está disponible para instancias de Adobe Commerce.

<!-- Configuration guide snippets -->

## Propietario del sistema de archivos {#file-system-owner}

>[!WARNING]
>
>Todos los comandos CLI de Magento deben ser ejecutados por el [propietario del sistema de archivos](/help/configuration/cli/config-cli.md#prerequisites).

## Comandos de copia de seguridad {#tip-backup-command}

>[!TIP]
>
>El comando `support:backup` es _no_ la misma copia de seguridad de código realizada por el comando `setup:backup`. El comando `support:backup` está diseñado para hacer una copia de seguridad del código y que el soporte técnico de Adobe Commerce lo examine.

## Parches B2B {#b2b-patches}

>[!NOTE]
>
>Después de instalar este parche de seguridad, los comerciantes de Adobe Commerce B2B también deben actualizar a la última versión del parche de seguridad B2B compatible. Ver [notas de la versión B2B](https://experienceleague.adobe.com/es/docs/commerce-admin/b2b/release-notes).

## Solo Adobe Commerce {#ee-only}

>[!NOTE]
>
>Esta función solo está disponible para instancias de Adobe Commerce.

## Base de datos dividida en desuso {#deprecate-split-db}

>[!IMPORTANT]
>
>La función de base de datos dividida estaba [obsoleta](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) en la versión 2.4.2 de Adobe Commerce. Ver [Revertir de una base de datos dividida a una sola base de datos](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Cambios incompatibles con versiones anteriores {#bics}

>[!NOTE]
>
>Las versiones de Adobe Commerce pueden contener cambios incompatibles con versiones anteriores (BIC). Para revisar los cambios incompatibles con versiones anteriores, consulte [Referencia de BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Los principales problemas incompatibles con versiones anteriores se describen en [resaltados de BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/). No todas las versiones introducen BIC importantes.

## exención de responsabilidad de Alpha {#alpha}

>[!IMPORTANT]
>
>Las versiones de [Alpha](/help/release/versioning-policy.md#alpha-patch-release) pueden estar incompletas y es probable que contengan defectos. Se proporcionan &quot;TAL CUAL&quot; sin garantía de ningún tipo. Adobe no tiene obligación de mantener, corregir, actualizar, cambiar, modificar o dar otro tipo de soporte (a través de los servicios de soporte de Adobe o de otro modo) a las versiones de Alpha. Los clientes no deben confiar en el funcionamiento o el rendimiento correctos de las versiones de Alpha ni de la documentación o los materiales adjuntos. El uso de las versiones de Alpha es totalmente bajo el propio riesgo del cliente.

## exención de responsabilidad de Beta {#beta}

>[!IMPORTANT]
>
>Las versiones de Beta pueden contener defectos y se proporcionan &quot;TAL CUAL&quot; sin garantía de ningún tipo. Adobe no tiene ninguna obligación de mantener, corregir, actualizar, cambiar, modificar o apoyar de otro modo (desde los Servicios de Soporte de Adobe o cualquier otro servicio) las versiones beta. Los clientes deben tener cuidado y no confiar en modo alguno en el funcionamiento o el rendimiento correctos de las versiones beta ni en la documentación o los materiales adjuntos. Por lo tanto, cualquier uso de las versiones beta es totalmente bajo el propio riesgo del cliente.

## aviso de CVE {#cve-notice}

>[!NOTE]
>
>A partir de la versión 2.3.2 de, asignaremos y publicaremos números de Vulnerabilidades comunes y exposiciones (CVE) indexados con cada error de seguridad que nos comuniquen partes externas. Esto permite a los usuarios identificar con mayor facilidad las vulnerabilidades sin solucionar en su implementación. Puede obtener más información sobre los identificadores CVE en [CVE](https://cve.mitre.org/).

## Otra información de la versión {#other-release-info}

>[!NOTE]
>
>Aunque el código para mejoras y correcciones de errores descrito en estas notas de la versión está incorporado en Adobe Commerce, varios de estos proyectos (por ejemplo, B2B, Page Builder y Progressive Web Applications (PWA) Studio) también se publican de forma independiente. Las correcciones de errores para estos proyectos se documentan en la información de versión independiente y específica del proyecto que está disponible en la documentación de cada proyecto. Ver [descripción general de la versión del producto](/help/release/release-notes/overview.md).

## Control de procesos PHP {#php-process-control}

Para poder ejecutar indizadores en modo paralelo, debe habilitar la compatibilidad con Control de procesos (`pcntl`) en PHP. Consulte [Instalación](https://www.php.net/manual/en/pcntl.installation.php) en la documentación de PHP.

## Parches personalizados {#custom-patches-disclaimer}

>[!IMPORTANT]
>
>Adobe no admite la aplicación de parches oficiales proporcionados por Adobe mediante este método. Utilice el siguiente método bajo su propia responsabilidad. Para aplicar parches oficiales, use [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es){target="_blank"}. Realice siempre pruebas exhaustivas antes de implementar cualquier parche personalizado.
