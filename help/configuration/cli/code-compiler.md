---
title: Compilador de código
description: Aprenda a ejecutar el compilador de código desde la línea de comandos.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# Compilador de código

{{file-system-owner}}

La compilación de código incluye lo siguiente (sin orden particular):

- Generación de código de aplicación (fábricas, proxies)
- Agregación de configuración de área (optimizada) [inyección de dependencia](https://glossary.magento.com/dependency-injection) configuraciones por área)
- Generación de interceptores (generación de código optimizada de interceptores)
- Generación de caché de intercepción
- Generación de código de repositorios (código generado para API)
- Generación de atributos de datos de servicio (generada [Extensión](https://glossary.magento.com/extension) clases para objetos de datos)

Puede encontrar las clases de compilación de código en la [\Magento\Setup\Module\Di\App\Task\Operation][operation] espacio de nombres.

Para ejecutar el compilador de un solo inquilino:

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

Para compilar código antes de instalar la aplicación Commerce:

En algunos casos, es posible que desee compilar código antes de instalar la aplicación Commerce.

1. Active los módulos.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Utilice la variable `[-c|--clear-static-content]` para borrar [contenido estático](https://glossary.magento.com/static-content). Esto es necesario si previamente ha habilitado o deshabilitado los módulos y debe borrar el contenido estático generado previamente para ellos.

   Consulte [Habilitar módulos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-enable.html).

1. Compile el código.

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

Para compilar código sin una base de datos, consulte [Implementar archivos de vista estáticos sin instalar el Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
