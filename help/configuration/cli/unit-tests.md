---
title: Ejecutar pruebas unitarias
description: Obtenga información sobre cómo ejecutar pruebas unitarias definidas en el código base de Adobe Commerce. Descubra los comandos de prueba, las opciones de ejecución y los informes de resultados.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
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

  ```bash
  bin/magento module:enable [--force] Magento_Developer
  ```

  Utilice la opción `--force` solo si es necesario.

- El sistema debe estar configurado para ejecutar las pruebas deseadas.

Por ejemplo, para ejecutar pruebas de integración, debe copiar `dev/tests/integration/etc/install-config-mysql.php.dist` en `dev/tests/integration/etc/install-config-mysql.php` y modificarlo para adaptarlo a su entorno.

## Ejecución de pruebas

Uso de comandos:

```bash
bin/magento dev:tests:run <test>
```

Para enumerar los tipos de prueba disponibles:

```bash
bin/magento dev:tests:run --help
```

Devolución de muestra:

```
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Por ejemplo, para ejecutar pruebas de integración:

```bash
bin/magento dev:tests:run integration
```
