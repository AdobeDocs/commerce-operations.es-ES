---
title: "[!DNL Data Migration Tool] requisitos previos"
description: "Aprenda lo que necesita hacer antes de empezar a usar la variable [!DNL Data Migration Tool] para transferir datos entre el Magento 1 y el Magento 2."
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---


# [!DNL Data Migration Tool] requisitos previos

Antes de iniciar la migración, asegúrese de que se cumplan los siguientes requisitos.

## sistema Magento 2

* Configure su sistema Magento 2 para que cumpla con la [requisitos del sistema](../../installation/system-requirements.md).

   Utilice una topología y un diseño que coincida al menos con su sistema Magento 1 existente.

* [Instalar Magento 2](../../installation/overview.md).

## Cron

No inicie trabajos cron de Magento 2.

## Base de datos

* Después de la instalación, realice una copia de seguridad o [volcado](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) la base de datos de Magento 2 lo antes posible. Esto le permite restaurar el estado inicial de la base de datos si la migración no se realiza correctamente.

* Compruebe si la variable [!DNL Data Migration Tool] tiene acceso a la red para conectar las bases de datos Magento 1 y Magento 2.

   Abra puertos en el cortafuegos para que la herramienta de migración pueda comunicarse con las bases de datos.

* Asegúrese de que sus cuentas de MySQL tengan todos los privilegios necesarios para acceder a las bases de datos de Magento.

Si el Inicio de sesión binario está habilitado para la base de datos de Magento 1, establezca la variable global [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) Variable de sistema MySQL a `1`o conceda la variable [Privilegio SUPER](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) a su cuenta.

* No se recomienda crear nuevas entidades (productos, categorías y atributos) en el almacén de Magento 2 antes de la migración, ya que la variable [!DNL Data Migration Tool] sobrescribe estas entidades nuevas con las antiguas del Magento 1.

## Extensiones

Migrar el código de extensión del Magento 1 al Magento 2.

Para encontrar las últimas versiones de las extensiones, visite [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) o póngase en contacto con el proveedor de extensiones.

También puede usar la variable [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
