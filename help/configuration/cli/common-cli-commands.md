---
title: Comandos comunes
description: Vea una muestra de comandos y uso comunes de Commerce CLI.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---


# Comandos comunes

A continuación se resumen algunos de los comandos disponibles.

**Para mostrar una lista completa de comandos**:

```bash
bin/magento list
```

Ejemplo de comando de ayuda:

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

Los comandos se muestran únicamente en forma de resumen; para obtener más información sobre un comando, haga clic en el vínculo de la columna Comando .

| Comando | Descripción |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | Gestiona la caché |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | Gestiona los indexadores |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Ejecuta trabajos cron de Commerce |
| [`magento setup:di:compile`](../cli/code-compiler.md) | Compila todos los proxies y fábricas inexistentes; y precompila definiciones de clases, información de herencia y definiciones de complementos para un almacén y sitio web. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | Dependencias de módulos, dependencias circulares y dependencias del marco de comercio. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | Crea un diccionario de traducción o un paquete de traducción |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | Implementa archivos de vista estáticos |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | Crea CSS a LESS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | Ejecuta pruebas automatizadas |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | Actualice los archivos XML de diseño para que coincidan con la nueva hoja de estilo Transformaciones de lenguaje de hojas de estilo ampliables (XSLT) |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | Genere datos para utilizarlos en pruebas de rendimiento. |
| [`magento sampledata:install`](https://devdocs.magento.com/guides/v2.4/install-gde/install/sample-data.html) | Instala datos de ejemplo opcionales después de instalar la aplicación Commerce.<br><br>Para obtener más información sobre los datos de ejemplo, consulte [Datos de ejemplo opcionales](https://devdocs.magento.com/guides/v2.4/install-gde/install/sample-data.html). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | Gestiona las configuraciones del servidor |
| [`magento admin:user:{create/unlock}`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-admin.html) | Crea/edita/desbloquea usuarios administradores. |
| [`magento dev:template-hints:{enable/disable}`](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/debug-theme.html) | Habilita/deshabilita las sugerencias de plantilla para desarrolladores. |

## Argumentos comunes

Los siguientes argumentos son comunes a todos los comandos. Estos comandos se pueden ejecutar antes o después de instalar el software Commerce:

| Versión larga | Versión corta | Significado |
|--- |--- |--- |
| `--help` | `-h` | Obtenga ayuda para cualquier comando. Por ejemplo, `./magento help setup:install` o `./magento help setup:config:set`. |
| `--quiet` | `-q` | Modo silencioso; sin salida. |
| `--no-interaction` | `-n` | No hay preguntas interactivas. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Nivel de detalle. Por ejemplo, `--verbose=3` o `-vvv` muestra debug verbosity, que es el resultado más detallado. El valor predeterminado es `--verbose=1` o `-v`. |
| `--version` | `-V` | Mostrar esta versión de la aplicación |
| `--ansi` | n.a | Forzar salida ANSI |
| `--no-ansi` | n.a | Deshabilitar salida ANSI |
