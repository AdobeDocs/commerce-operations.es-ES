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
>La variable [!DNL Upgrade Compatibility Tool] solo está disponible para instancias de Adobe Commerce.

<!-- Configuration guide snippets -->

## Propietario del sistema de archivos {#file-system-owner}

>[!WARNING]
>
>Todos los comandos CLI del Magento deben ser ejecutados por [propietario del sistema de archivos](/help/configuration/cli/config-cli.md#prerequisites).

## Comandos de copia de seguridad {#tip-backup-command}

>[!TIP]
>
>La variable `support:backup` command is _not_ la misma copia de seguridad de código realizada por el `setup:backup` comando. La variable `support:backup` está diseñado para realizar una copia de seguridad del código para que la asistencia de Adobe Commerce lo examine.

## Solo Adobe Commerce {#ee-only}

>[!NOTE]
>
>Esta función solo está disponible para instancias de Adobe Commerce.

## Dividir base de datos en desuso {#deprecate-split-db}

>[!IMPORTANT]
>
>La función de base de datos dividida era [obsoleto](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) en la versión 2.4.2 de Adobe Commerce. Consulte [Revertir de una base de datos dividida a una única base de datos](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Cambios incompatibles con versiones anteriores {#bics}

>[!NOTE]
>
>Las versiones de Adobe Commerce y Magento Open Source pueden contener cambios incompatibles con versiones anteriores (BIC). Para revisar los cambios incompatibles con versiones anteriores, consulte [Referencia BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Los principales problemas incompatibles con versiones anteriores se describen en [Aspectos destacados de BIC](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). No todas las versiones introducen BIC importantes.

## Aviso de CVE {#cve-notice}

>[!NOTE]
>
>A partir de la versión 2.3.2, asignaremos y publicaremos números indexados de Vulnerabilidades y Exposiciones Comunes (CVE) con cada error de seguridad que nos notifiquen partes externas. Esto permite a los usuarios identificar con mayor facilidad las vulnerabilidades no atendidas en su implementación. Puede obtener más información sobre los identificadores CVE en [CVE](https://cve.mitre.org/).
