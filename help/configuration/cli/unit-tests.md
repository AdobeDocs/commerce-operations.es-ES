---
title: Ejecutar pruebas unitarias
description: Ejecute las pruebas unitarias definidas en la base de código de Adobe Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Ejecutar pruebas unitarias

{{file-system-owner}}

Este comando ejecuta un conjunto de pruebas definidas en la base de código de Commerce 2. Puede ejecutar todas las pruebas o pruebas que seleccione. Siempre que se especifica un tipo no compatible, el programa finaliza y enumera todos los tipos disponibles. Después de la ejecución, aparece un informe detallado que muestra la ejecución de la prueba y los resultados.

## Requisitos previos

Antes de ejecutar este comando, haga lo siguiente: _must_ sea verdadero:

- La variable `Magento_Developer` debe estar habilitado. Puede habilitarlo de la siguiente manera:

   ```bash
   bin/magento module:enable [--force] Magento_Developer
   ```

   Utilice la variable `--force` solo si es necesario.

- El sistema debe estar configurado para ejecutar las pruebas deseadas.

Por ejemplo, para ejecutar pruebas de integración, debe copiar `dev/tests/integration/etc/install-config-mysql.php.dist` a `dev/tests/integration/etc/install-config-mysql.php` y modifíquelo para adaptarlo a su entorno.

## Ejecución de pruebas

Uso de comandos:

```bash
bin/magento dev:tests:run <test>
```

Para enumerar los tipos de prueba disponibles:

```bash
bin/magento dev:tests:run --help
```

Ejemplo de retorno:

```terminal
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Por ejemplo, para ejecutar pruebas de integración:

```bash
bin/magento dev:tests:run integration
```
