---
title: '[!DNL Data Migration Tool] requisitos previos'
description: Aprenda lo que debe hacer antes de empezar a utilizar el [!DNL Data Migration Tool] para transferir datos entre Magento 1 y Magento 2.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# [!DNL Data Migration Tool] requisitos previos

Antes de iniciar la migración, asegúrese de que se cumplen los siguientes requisitos.

## sistema Magento 2

* Configure el sistema Magento 2 para que cumpla los requisitos de [requisitos del sistema](../../installation/system-requirements.md).

   Utilice una topología y un diseño que coincidan al menos con el sistema Magento 1 existente.

* [Magento de instalación 2](../../installation/overview.md).

## Cron

No inicie trabajos cron del Magento 2.

## Base de datos

* Después de la instalación, haga una copia de seguridad o [basurero](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) su base de datos de Magento 2 lo antes posible. Esto le permite restaurar el estado inicial de la base de datos si la migración no se realiza correctamente.

* Compruebe si la variable [!DNL Data Migration Tool] tiene acceso a la red para conectar las bases de datos de Magento 1 y Magento 2.

   Abra los puertos del cortafuegos para que la herramienta de migración pueda comunicarse con las bases de datos.

* Asegúrese de que sus cuentas MySQL tengan todos los privilegios necesarios para acceder a las bases de datos de Magento.

Si el registro binario está habilitado para la base de datos de Magento 1, establezca el global [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) Variable del sistema MySQL a `1`, o conceda el [Privilegio SUPER](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) a su cuenta.

* No se recomienda crear nuevas entidades (productos, categorías y atributos) en la tienda de Magento 2 antes de la migración porque la variable [!DNL Data Migration Tool] sobrescribe estas nuevas entidades con las antiguas del Magento 1.

## Extensiones

Migre el código de extensión de Magento 1 al Magento 2.

Para buscar las últimas versiones de las extensiones, visite [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) o póngase en contacto con su proveedor de extensiones.

También puede utilizar la variable [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
