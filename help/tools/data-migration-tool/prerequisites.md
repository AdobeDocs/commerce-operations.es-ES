---
title: '[!DNL Data Migration Tool] requisitos previos'
description: Aprenda lo que necesita hacer antes de empezar a usar  [!DNL Data Migration Tool] para transferir datos entre Magento 1 y Magento 2.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# [!DNL Data Migration Tool] requisitos previos

Antes de iniciar la migración, asegúrese de que se cumplen los siguientes requisitos.

## sistema Magento 2

* Configure su sistema Magento 2 para que cumpla con los [requisitos del sistema](../../installation/system-requirements.md).

  Utilice una topología y un diseño que coincidan al menos con su sistema Magento 1 existente.

* [Instalar Magento 2](../../installation/overview.md).

## Cron

No inicie trabajos cron de Magento 2.

## Base de datos

* Después de la instalación, haga una copia de seguridad o [volque](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) su base de datos de Magento 2 lo antes posible. Esto le permite restaurar el estado inicial de la base de datos si la migración no se realiza correctamente.

* Compruebe si [!DNL Data Migration Tool] tiene acceso de red para conectar las bases de datos de Magento 1 y Magento 2.

  Abra los puertos del cortafuegos para que la herramienta de migración pueda comunicarse con las bases de datos.

* Asegúrese de que sus cuentas MySQL tengan todos los privilegios necesarios para acceder a las bases de datos de Magento.

Si el registro binario está habilitado para su base de datos de Magento 1, establezca la variable global del sistema MySQL [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) en `1` o conceda el privilegio [SUPER](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) a su cuenta.

* No se recomienda crear nuevas entidades (productos, categorías y atributos) en la tienda de Magento 2 antes de la migración, ya que [!DNL Data Migration Tool] sobrescribe esas nuevas entidades con las antiguas de Magento 1.

## Extensiones

Migrar el código de extensión de Magento 1 a Magento 2.

Para encontrar las últimas versiones de las extensiones, visite [[!DNL [Commerce Marketplace]]](https://commercemarketplace.adobe.com//) o póngase en contacto con su proveedor de extensiones.

También puede usar [[!DNL [Code Migration Tool]]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
