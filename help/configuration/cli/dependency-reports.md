---
title: Informes de dependencias
description: Cree informes que muestren los totales de las dependencias de módulo, circular y marco.
exl-id: b7a32fe1-71c5-495f-8276-242503fb50ae
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Informes de dependencias

{{file-system-owner}}

Puede ejecutar los siguientes tipos de informes:

- **Dependencias de módulo**: Muestra el número total de dependencias entre módulos y si las dependencias son duras o suaves.
- **Dependencias circulares**: Muestra el número total de cadenas de dependencias y el número y la lista de dependencias circulares de cada módulo.
- **Dependencias de marco de trabajo**: Muestra el número total de dependencias en el marco de trabajo de Commerce por módulo (incluido el número total de entradas de marco de trabajo para cada biblioteca).

Una dependencia en un comentario también es una dependencia.

## Ejecutar informes de dependencias

Opciones de comando:

```bash
bin/magento info:dependencies:{show-modules|show-modules-circular|show-framework} [-d|--directory="<path>"] [-o|--output="<path and filename"]
```

En la tabla siguiente se explican las opciones, los parámetros y los valores de este comando.

| Parámetro | Valor | ¿Requerido? |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------- | --------- |
| `show-modules` | Informe de dependencias del módulo. | Sí |
| `show-modules-circular` | Informe de dependencias circulares. | Sí |
| `show-framework` | Informe de dependencias del marco. | Sí |
| `-d --directory` | Ruta al directorio base para comenzar a buscar datos del informe. | No |
| `-o --output` | Especifica la ruta de acceso absoluta del sistema de archivos y el nombre del archivo de salida del valor separado por comas (csv) para el informe. | No |

Si no se pasa ningún directorio o nombre de archivo como argumento, se utiliza la siguiente raíz de aplicación como directorio predeterminado y los siguientes nombres de archivo predeterminados:

| Comando | Nombre de archivo |
| ----------------------------------------------------- | ----------------------------------- |
| `bin/magento info:dependencies:show-modules` | `modules-dependencies.csv` |
| `bin/magento info:dependencies:show-modules-circular` | `modules-circular-dependencies.csv` |
| `bin/magento info:dependencies:show-framework` | `framework-dependencies.csv` |

### Informe de dependencias del módulo de ejemplo

El siguiente es una parte del resultado de un informe de dependencias de módulo de ejemplo:

```
"","All","Hard","Soft"
"Total number of dependencies","602","587","15"

"Dependencies for each module:","All","Hard","Soft"
"magento/module-cron","2","2","0"
" -- magento/module-config","","1","0"
" -- magento/module-store","","1","0"

"magento/module-catalog-rule","8","8","0"
" -- magento/module-store","","1","0"
" -- magento/module-rule","","1","0"
" -- magento/module-catalog","","1","0"
" -- magento/module-customer","","1","0"
" -- magento/module-backend","","1","0"
" -- magento/module-eav","","1","0"
" -- magento/module-indexer","","1","0"
" -- magento/module-import-export","","1","0"
```

### Ejemplo de informe de dependencias circulares

El siguiente es una parte del resultado de un ejemplo de informe de dependencias circulares:

```
"Circular dependencies:","Total number of chains"
"","848"

"Circular dependencies for each module:",""
"magento/module-config","70"
"magento/module-config->magento/module-store->magento/module-directory->magento/module-config"
"magento/module-config->magento/module-store->magento/module-config"
"magento/module-config->magento/module-cron->magento/module-config"
"magento/module-config->magento/module-email->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-theme->magento/module-customer->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-reports->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-theme->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-log->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-catalog-inventory->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-theme->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-payment->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-themeax->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-catalog-rule->magento/module-rule->magento/module-eav->magento/module-config"
```

### Ejemplo de informe de dependencias del marco

A continuación se muestra una parte del resultado de un informe de dependencias de marco de trabajo de ejemplo:

```
"Dependencies of framework:","Total number"
"","111"

"Dependencies for each module:",""
"Magento\Cron","1"
" -- Magento\Framework","143"

"Magento\CatalogRule","1"
" -- Magento\Framework","234"

"Magento\Webapi","2"
" -- Magento\Framework","347"
" -- Magento\Server","1"

"Magento\Checkout","1"
" -- Magento\Framework","759"

"Magento\Reports","1"
" -- Magento\Framework","553"
```
