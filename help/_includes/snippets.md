---
source-git-commit: 74cb55f4552bc1b2dace37d9a6f7e68939d1c262
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---
# Fragmentos

## Solo comercio {#commerce-only}

>[!NOTE]
>
>El [!DNL Upgrade Compatibility Tool] solo está disponible para instancias de Adobe Commerce.

<!-- Configuration guide snippets -->

## Propietario del sistema de archivos {#file-system-owner}

>[!WARNING]
>
>Todos los comandos de CLI del Magento deben ser ejecutados por el [propietario del sistema de archivos](/help/configuration/cli/config-cli.md#prerequisites).

## Comandos de copia de seguridad {#tip-backup-command}

>[!TIP]
>
>El `support:backup` el comando es _no_ la misma copia de seguridad de código realizada por el `setup:backup` comando. El `support:backup` El comando está diseñado para realizar una copia de seguridad del código y que el servicio de asistencia de Adobe Commerce lo examine.

## Solo Adobe Commerce {#ee-only}

>[!NOTE]
>
>Esta función solo está disponible para instancias de Adobe Commerce.

## Base de datos dividida en desuso {#deprecate-split-db}

>[!IMPORTANT]
>
>La función de base de datos dividida era [obsoleto](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) en la versión 2.4.2 de Adobe Commerce. Consulte [Revertir de una base de datos dividida a una única base de datos](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Cambios incompatibles con versiones anteriores {#bics}

>[!NOTE]
>
>Las versiones de Adobe Commerce y Magento Open Source pueden contener cambios incompatibles con versiones anteriores (BIC). Para revisar los cambios incompatibles con versiones anteriores, consulte [Referencia BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Los principales problemas incompatibles con versiones anteriores se describen en [Puntos destacados de BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). No todas las versiones introducen BIC importantes.

## aviso de CVE {#cve-notice}

>[!NOTE]
>
>A partir de la versión 2.3.2 de, asignaremos y publicaremos números de Vulnerabilidades comunes y exposiciones (CVE) indexados con cada error de seguridad que nos comuniquen partes externas. Esto permite a los usuarios identificar con mayor facilidad las vulnerabilidades sin solucionar en su implementación. Puede obtener más información sobre los identificadores CVE en [CVE](https://cve.mitre.org/).
