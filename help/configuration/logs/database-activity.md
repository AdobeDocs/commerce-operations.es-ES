---
title: Registrar actividad de base de datos
description: Configure Commerce para registrar la actividad de la base de datos mediante la interfaz del registrador.
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# Registrar actividad de base de datos

El siguiente ejemplo muestra cómo registrar la actividad de la base de datos utilizando [`Magento\Framework\DB\LoggerInterface`][interface], que tiene dos implementaciones:

- No registra nada (predeterminado): [`Magento\Framework\DB\Logger\Quiet`][quiet]
- Registra en `var/log` directorio: [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>Puede utilizar la CLI de Commerce para lo siguiente [habilitar y deshabilitar el registro de base de datos](../cli/enable-logging.md#database-logging).

Para cambiar la configuración predeterminada de `\Magento\Framework\DB\Logger\LoggerProxy`, edite su `app/etc/di.xml`.

Primero, cambie los valores predeterminados de `loggerAlias` y `logCallStack` argumentos para:

```xml
<type name="Magento\Framework\DB\Logger\LoggerProxy">
    <arguments>
        <argument name="loggerAlias" xsi:type="const">Magento\Framework\DB\Logger\LoggerProxy::LOGGER_ALIAS_FILE</argument>
        <argument name="logAllQueries" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_LOG_EVERYTHING</argument>
        <argument name="logQueryTime" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_QUERY_TIME_THRESHOLD</argument>
        <argument name="logCallStack" xsi:type="boolean">false</argument>
    </arguments>
</type>
```

A continuación, proporcione la ruta de archivo para `Magento\Framework\DB\Logger\File`:

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

Finalmente, compile el código con:

```bash
bin/magento setup:di:compile
```

Y limpie la caché con:

```bash
bin/magento cache:clean
```

<!-- link definitions -->

[file]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/File.php
[interface]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/LoggerInterface.php
[quiet]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/Quiet.php
