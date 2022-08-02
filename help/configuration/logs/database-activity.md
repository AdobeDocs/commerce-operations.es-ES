---
title: Actividad de la base de datos de registro
description: Configure Commerce para registrar la actividad de la base de datos mediante la interfaz Logger.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# Actividad de la base de datos de registro

El siguiente ejemplo muestra cómo registrar la actividad de la base de datos mediante el [`Magento\Framework\DB\LoggerInterface`][interface], que tiene dos implementaciones:

- Registra nada (predeterminado): [`Magento\Framework\DB\Logger\Quiet`][quiet]
- Registra en `var/log` directorio: [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>Puede utilizar Commerce CLI para [habilitar y deshabilitar el registro de bases de datos](../cli/enable-logging.md#database-logging).

Para cambiar la configuración predeterminada de `\Magento\Framework\DB\Logger\LoggerProxy`, edite el `app/etc/di.xml`.

En primer lugar, cambie los valores predeterminados de `loggerAlias` y `logCallStack` argumentos para:

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

Después, proporcione la ruta del archivo para `Magento\Framework\DB\Logger\File`:

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
