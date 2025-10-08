---
title: Comandos comunes
description: Obtenga información sobre los comandos CLI comunes de Adobe Commerce y sus ejemplos de uso. Descubra herramientas esenciales de línea de comandos para el desarrollo y la administración.
exl-id: d35a1dd9-10b3-4364-b6f4-b1e259a04e3d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Comandos comunes

A continuación se resumen algunos de los comandos disponibles.

**Para mostrar una lista completa de comandos**:

```bash
bin/magento list
```

Ejemplo de comando help:

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

Los comandos sólo se muestran en forma de resumen; para obtener más información sobre un comando, haga clic en el vínculo de la columna Comando.

| Comando | Descripción |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | Administra la caché |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | Gestiona los indexadores |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Ejecuta trabajos cron de Commerce |
| [`magento setup:di:compile`](../cli/code-compiler.md) | Compila todos los proxies y fábricas inexistentes, y precompila definiciones de clase, información de herencia y definiciones de complementos para un almacén y sitio web. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | Dependencias de módulo, dependencias circulares y dependencias de marco de trabajo de Commerce. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | Crea un diccionario de traducción o un paquete de traducción |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | Implementa archivos de vista estática |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | Crea CSS a partir de LESS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | Ejecuta pruebas automatizadas |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | Actualice los archivos XML de diseño para que coincidan con la nueva hoja de estilos XSLT (Extensible Stylesheet Language Transformations) |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | Generar datos para utilizarlos en las pruebas de rendimiento. |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | Instala datos de ejemplo opcionales después de instalar la aplicación Commerce.<br><br>Para obtener más información acerca de los datos de ejemplo, vea [Datos de ejemplo opcionales](../../installation/sample-data/overview.md). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | Gestiona las configuraciones back-end |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | Crea/edita/desbloquea usuarios administradores. |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | Activa/desactiva las sugerencias de plantillas para desarrolladores. |

## Argumentos comunes

Los siguientes argumentos son comunes a [todos los comandos](/help/tools/reference/commerce-on-premises.md). Estos comandos se pueden ejecutar antes o después de instalar el software de Commerce:

| Versión larga | Versión corta | Significado |
|--- |--- |--- |
| `--help` | `-h` | Obtener ayuda para cualquier comando. Por ejemplo, `./magento help setup:install` o `./magento help setup:config:set`. |
| `--quiet` | `-q` | Modo silencioso; sin salida. |
| `--no-interaction` | `-n` | No hay preguntas interactivas. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Nivel de detalle. Por ejemplo, `--verbose=3` o `-vvv` muestran el nivel de detalle de la depuración, que es el resultado más detallado. El valor predeterminado es `--verbose=1` o `-v`. |
| `--version` | `-V` | Mostrar esta versión de la aplicación |
| `--ansi` | n/a | Forzar salida ANSI |
| `--no-ansi` | n/a | Deshabilitar salida ANSI |
