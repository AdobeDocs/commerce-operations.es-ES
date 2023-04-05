---
title: Compilador de código
description: Aprenda a ejecutar el compilador de código desde la línea de comandos.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# Compilador de código

{{file-system-owner}}

La compilación de código incluye lo siguiente (sin orden particular):

- Generación de código de aplicación (fábricas, proxies)
- Agregación de configuración de área (configuraciones de inyección de dependencia optimizada por área)
- Generación de interceptores (generación de código optimizada de interceptores)
- Generación de caché de intercepción
- Generación de código de repositorios (código generado para API)
- Generación de atributos de datos de servicio (clases de extensión generadas para objetos de datos)

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

   Utilice la variable `[-c|--clear-static-content]` para borrar contenido estático. Esto es necesario si previamente ha habilitado o deshabilitado los módulos y debe borrar el contenido estático generado previamente para ellos.

   Consulte [Habilitar módulos](../../installation/tutorials/manage-modules.md).

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
