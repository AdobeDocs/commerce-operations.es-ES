---
title: Compilador de código
description: Aprenda a ejecutar el compilador de código desde la línea de comandos.
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Compilador de código

{{file-system-owner}}

La compilación de código incluye lo siguiente (sin ningún orden en particular):

- Generación de código de aplicación (fábricas, proxies)
- Agregación de configuración de área (configuraciones de inyección de dependencia optimizada por área)
- Generación de interceptores (generación de código optimizada de interceptores)
- Generación de caché de intercepción
- Generación de código de repositorios (código generado para las API)
- Generación de atributos de datos del servicio (clases de extensión generadas para objetos de datos)

Puede encontrar clases de compilación de código en el espacio de nombres [\Magento\Setup\Module\Di\App\Task\Operation][operation].

Para ejecutar el compilador de un solo inquilino:

```bash
bin/magento setup:di:compile
```

```
Generated code and dependency injection configuration successfully.
```

Para compilar el código antes de instalar la aplicación de Commerce:

En algunos casos, es posible que desee compilar el código antes de instalar la aplicación de Commerce.

1. Habilite los módulos.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Utilice la opción `[-c|--clear-static-content]` para borrar el contenido estático. Esto es necesario si ha habilitado o deshabilitado los módulos anteriormente y debe borrar el contenido estático generado anteriormente para ellos.

   Consulte [Habilitar módulos](../../installation/tutorials/manage-modules.md).

1. Compile el código.

   ```bash
   bin/magento setup:di:compile
   ```

   ```
   Generated code and dependency injection configuration successfully.
   ```

Para compilar código sin base de datos, vea [Implementar archivos de vista estática sin instalar Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
