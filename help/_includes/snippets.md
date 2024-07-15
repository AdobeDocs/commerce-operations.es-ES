---
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '269'
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
>Todos los comandos CLI del Magento deben ser ejecutados por el [propietario del sistema de archivos](/help/configuration/cli/config-cli.md#prerequisites).

## Comandos de copia de seguridad {#tip-backup-command}

>[!TIP]
>
>El comando `support:backup` es _no_ la misma copia de seguridad de código realizada por el comando `setup:backup`. El comando `support:backup` está diseñado para hacer una copia de seguridad del código y que el soporte técnico de Adobe Commerce lo examine.

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
>Las versiones de Adobe Commerce pueden contener cambios incompatibles con versiones anteriores (BIC). Para revisar los cambios incompatibles con versiones anteriores, consulte [Referencia de BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Los principales problemas incompatibles con versiones anteriores se describen en [resaltados de BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). No todas las versiones introducen BIC importantes.

## aviso de CVE {#cve-notice}

>[!NOTE]
>
>A partir de la versión 2.3.2 de, asignaremos y publicaremos números de Vulnerabilidades comunes y exposiciones (CVE) indexados con cada error de seguridad que nos comuniquen partes externas. Esto permite a los usuarios identificar con mayor facilidad las vulnerabilidades sin solucionar en su implementación. Puede obtener más información sobre los identificadores CVE en [CVE](https://cve.mitre.org/).

## Otra información de la versión {#other-release-info}

>[!NOTE]
>
>Aunque el código para mejoras y correcciones de errores descrito en estas notas de la versión está incorporado en Adobe Commerce, varios de estos proyectos (por ejemplo, B2B, Page Builder y Progressive Web Application (PWA) Studio) también se publican de forma independiente. Las correcciones de errores para estos proyectos se documentan en la información de versión independiente y específica del proyecto que está disponible en la documentación de cada proyecto. Ver [descripción general de la versión del producto](/help/release/release-notes/overview.md).

## Control de procesos PHP {#php-process-control}

Para poder ejecutar indizadores en modo paralelo, debe habilitar la compatibilidad con Control de procesos (`pcntl`) en PHP. Consulte [Instalación](https://www.php.net/manual/en/pcntl.installation.php) en la documentación de PHP.
