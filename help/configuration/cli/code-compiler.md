---
title: Compilador de código
description: Aprenda a ejecutar el compilador de código de Adobe Commerce desde la línea de comandos. Descubra procesos de compilación y técnicas de optimización.
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '184'
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

Puede encontrar clases de compilación de código en el espacio de nombres [\Magento\Setup\Module\Di\App\Task\Operation](https://github.com/magento/magento2/blob/2.4.8/setup/src/Magento/Setup/Module/Di/App/Task/Operation).

Para ejecutar el compilador de un solo inquilino:

```shell
bin/magento setup:di:compile
```

```text
Generated code and dependency injection configuration successfully.
```

Para compilar el código antes de instalar la aplicación de Commerce:

En algunos casos, es posible que desee compilar el código antes de instalar la aplicación de Commerce.

1. Habilite los módulos.

   ```shell
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Utilice la opción `[-c|--clear-static-content]` para borrar el contenido estático. Esto es necesario si ha habilitado o deshabilitado los módulos anteriormente y debe borrar el contenido estático generado anteriormente para ellos.

   Consulte [Habilitar módulos](../../installation/tutorials/manage-modules.md).

1. Compile el código.

   ```shell
   bin/magento setup:di:compile
   ```

   ```text
   Generated code and dependency injection configuration successfully.
   ```

Para compilar código sin base de datos, vea [Implementar archivos de vista estática sin instalar Magento](../cli/static-view-file-deployment.md).

