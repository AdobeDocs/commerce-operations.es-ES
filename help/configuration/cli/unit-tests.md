---
title: Ejecutar pruebas unitarias
description: Obtenga información sobre cómo ejecutar pruebas unitarias definidas en el código base de Adobe Commerce. Descubra los comandos de prueba, las opciones de ejecución y los informes de resultados.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
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
source-wordcount: '152'
ht-degree: 0%
---
# Ejecutar pruebas unitarias

{{file-system-owner}}

Este comando ejecuta un conjunto de pruebas definidas en la base de código de Commerce 2. Puede ejecutar todas las pruebas o las pruebas que seleccione. Siempre que se especifica un tipo no admitido, el programa finaliza y enumera todos los tipos disponibles. Después de la ejecución, se muestra un informe detallado con la ejecución de la prueba y los resultados.

## Requisitos previos

Antes de ejecutar este comando, el siguiente _debe_ ser verdadero:

- El módulo `Magento_Developer` debe estar habilitado. Puede habilitarlo de la siguiente manera:

  ```shell
  bin/magento module:enable [--force] Magento_Developer
  ```

  Utilice la opción `--force` solo si es necesario.

- El sistema debe estar configurado para ejecutar las pruebas deseadas.

Por ejemplo, para ejecutar pruebas de integración, debe copiar `dev/tests/integration/etc/install-config-mysql.php.dist` en `dev/tests/integration/etc/install-config-mysql.php` y modificarlo para adaptarlo a su entorno.

## Ejecución de pruebas

Uso de comandos:

```shell
bin/magento dev:tests:run <test>
```

Para enumerar los tipos de prueba disponibles:

```shell
bin/magento dev:tests:run --help
```

Devolución de muestra:

```text
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Por ejemplo, para ejecutar pruebas de integración:

```shell
bin/magento dev:tests:run integration
```
