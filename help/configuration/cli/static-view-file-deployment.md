---
title: Implementación de archivos de vista estática
description: Aprenda a escribir archivos estáticos en el sistema de archivos de Commerce durante el modo de producción.
exl-id: 51954738-b999-4982-954b-70f7a70c5a17
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 0%

---

# Implementación de archivos de vista estática

{{file-system-owner}}

El comando de implementación de archivos de vista estática le permite escribir archivos estáticos en el sistema de archivos Commerce cuando el software Commerce está configurado para [modo de producción](../bootstrap/application-modes.md#production-mode).

El término _archivo de vista estática_ hace referencia a lo siguiente:

- Estático significa que se puede almacenar en caché para un sitio (es decir, el archivo no se genera dinámicamente). Algunos ejemplos son imágenes y CSS generadas a partir de LESS.
- &quot;Ver&quot; se refiere a la capa de presentación (de MVC).

Los archivos de vista estática se encuentran en el directorio `<magento_root>/pub/static` y algunos también se almacenan en caché en el directorio `<magento_root>/var/view_preprocessed`.

La implementación de archivos de vista estática se ve afectada por los modos de aplicación de la siguiente manera:

- Modos [Default](../bootstrap/application-modes.md#default-mode) y [developer](../bootstrap/application-modes.md#developer-mode): Commerce los genera bajo demanda, pero el resto se almacena en caché en un archivo para mayor velocidad de acceso.
- Modo [Producción](../bootstrap/application-modes.md#production-mode): los archivos estáticos _no_ se generan o almacenan en caché.

Debe escribir archivos de vista estática en el sistema de archivos de Commerce manualmente mediante el comando que se describe en este tema; después, puede restringir los permisos para limitar las vulnerabilidades y evitar la sobrescritura accidental o maliciosa de archivos.

>[!WARNING]
>
>_Solo modo de desarrollador_: al instalar o habilitar un módulo nuevo, podría cargar JavaScript, CSS, diseños, etc. nuevos. Para evitar problemas con los archivos estáticos, debe limpiar los archivos antiguos para asegurarse de obtener todos los cambios para el nuevo módulo. Puede limpiar los archivos de vista estática generados de varias formas. Consulte el tema [Limpiar la caché de archivos estáticos para obtener más información](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache).

**Para implementar archivos de vista estática**:

1. Inicie sesión en el servidor de Commerce como o [cambie al propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Eliminar el contenido de `<magento_root>/pub/static`, excepto el archivo `.htaccess`. No elimine este archivo.
1. Ejecute la herramienta de implementación de archivos de vista estática `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >Si habilita la combinación de archivos de vista estática en el administrador, el sistema de directorios `pub/static` debe poder escribirse.

   Opciones de comando:

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

En la tabla siguiente se explican los parámetros y valores de este comando.

| Opción | Descripción | ¿Requerido? |
| ------ | ----------- | --------- |
| `<languages>` | Lista separada por espacios de [códigos de idioma ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php) para los que se mostrarán archivos de vista estática. (El valor predeterminado es `en_US`).<br>Busque la lista ejecutando: `bin/magento info:language:list` | No |
| `--language (-l)` | Genere archivos solo para los idiomas especificados. El valor predeterminado, sin especificar ninguna opción, es generar archivos para todos los códigos de idioma ISO-639. Puede especificar el nombre de un código de idioma a la vez. El valor predeterminado es **all**.<br>Por ejemplo: `--language en_US --language es_ES` | No |
| `--exclude-language` | Generar archivos para los códigos de idioma especificados. El valor predeterminado, sin especificar ninguna opción, es no excluir nada. Puede especificar el nombre de un código de idioma o una lista de códigos de idioma separados por comas. El valor predeterminado es **none**. | No |
| `--theme <theme>` | Temas para los que se va a implementar contenido estático. El valor predeterminado es **all**.<br>Por ejemplo: `--theme Magento/blank --theme Magento/luma` | No |
| `--exclude-theme <theme>` | Temas que se deben excluir al implementar contenido estático. El valor predeterminado es **none**.<br>Por ejemplo, `--exclude-theme Magento/blank` | No |
| `--area (-a)` | Genere archivos solo para las áreas especificadas. El valor predeterminado, sin especificar ninguna opción, es generar archivos para todas las áreas. Los valores válidos son `adminhtml` y `frontend`. El valor predeterminado es **all**.<br>Por ejemplo: `--area adminhtml` | No |
| `--exclude-area` | No genere archivos para las áreas especificadas. El valor predeterminado, sin especificar ninguna opción, es no excluir nada. El valor predeterminado es **none**. | No |
| `--jobs (-j)` | Habilitar [procesamiento paralelo](manage-indexers.md#reindexing-in-parallel-mode) con el número de trabajos especificado. El valor predeterminado es 0 (no ejecutar en procesos en paralelo). El valor predeterminado es **0**. | No |
| `--symlink-locale` | Cree enlaces simbólicos para los archivos de esas configuraciones regionales, que se pasan para su implementación, pero no tienen personalizaciones. | No |
| `--content-version=CONTENT-VERSION` | Se puede utilizar una versión personalizada del contenido estático si se ejecuta la implementación en varios nodos para garantizar que la versión del contenido estático sea idéntica y que el almacenamiento en caché funcione correctamente. | No |
| `--no-javascript` | No implementar archivos de JavaScript | No |
| `--no-css` | No implemente archivos CSS. | No |
| `--no-less` | No implemente archivos LESS. | No |
| `--no-images` | No implemente imágenes. | No |
| `--no-fonts` | No implemente archivos de fuentes. | No |
| `--no-html` | No implemente archivos de HTML. | No |
| `--no-misc` | No implemente otros tipos de archivos: MD, JBF, CSV, JSON, TXT, HTC o SWF | No |
| `--no-html-minify` | No minifique los archivos de HTML. | No |
| `-s <quick\|standard\|compact>` | Defina la estrategia de implementación. Utilice estas opciones solo si tiene más de un local.<ul><li>Use la [estrategia rápida](static-view-file-strategy.md#quick-strategy) para minimizar el tiempo de implementación. Esta es la opción de comando predeterminada si no se especifica.</li><li>Use la [estrategia estándar](static-view-file-strategy.md#standard-strategy) para implementar todos los archivos de vista estática para todos los paquetes.</li><li>Use la [estrategia compacta](static-view-file-strategy.md#compact-strategy) para conservar espacio en disco en el servidor.</li></ul> | No |
| `--no-parent` | No generar archivos para las temáticas principales del tema actual. Se recomienda utilizar este indicador si no utiliza explícitamente la temática principal de la temática actual que intenta implementar. Esto aumenta significativamente la velocidad del proceso. Este indicador está disponible en Commerce 2.4.2 | No |
| `--force (-f)` | Implemente archivos en cualquier modo. (de forma predeterminada, la herramienta de implementación de contenido estático solo se puede ejecutar en el modo de producción. Utilice esta opción para ejecutarla en modo predeterminado o de desarrollador). | No |

>[!INFO]
>
>Si especifica valores para `<languages>` y `--language`, `<languages>` tiene prioridad.

## Ejemplos

A continuación se muestran algunos comandos de ejemplo.

### Exclusión de una temática y minificación de HTML

El siguiente comando implementa contenido estático para el idioma inglés de EE. UU. (`en_US`), excluye el tema de Luma proporcionado con Commerce y no minimiza los archivos HTML.

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

Salida de ejemplo:

```
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/backend
=== frontend -> Magento/blank -> en_US ===
=== adminhtml -> Magento/backend -> en_US ===
...........................................................
... more ...
Successful: 2055 files; errors: 0
---

New version of deployed files: 1466710645
............
Successful: 1993 files; errors: 0
---
```

El siguiente comando implementa únicamente JavaScript, con 4 trabajos, con una estrategia de implementación estándar:

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

El siguiente comando implementa solo CSS y LESS con 3 trabajos, y una estrategia de implementación rápida:

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### Generar archivos de vista estática para una temática y un área

El siguiente comando genera archivos de vista estática para todos los idiomas, solo para el área de front-end y solo para la temática de Commerce Luma, sin generar fuentes:

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

Salida de ejemplo:

```
Requested languages: en_US
Requested areas: frontend
Requested themes: Magento/luma
=== frontend -> Magento/luma -> en_US ===
...........................................................
... more ...
........................................................................
Successful: 2092 files; errors: 0
---

New version of deployed files: 1466711110
```

## Implementar archivos de vista estática sin instalar Commerce

Es posible que desee ejecutar el proceso de implementación en un entorno independiente, que no sea de producción, para evitar procesos de generación en equipos de producción confidenciales.

Para ello, siga los siguientes pasos:

1. Ejecute [`bin/magento app:config:dump`](../cli/export-configuration.md) para exportar la configuración desde el sistema de producción.
1. Copie los archivos exportados en la base del código que no sea de producción.
1. Implementar archivos de vista estática: `bin/magento setup:static-content:deploy`

## Solución de problemas de la herramienta de implementación de archivos de vista estática

[Instale primero el software de Commerce](../../installation/overview.md); de lo contrario, no podrá ejecutar la herramienta de implementación de archivos de vista estática.

**Síntoma**: se muestra el siguiente error al ejecutar la herramienta de implementación de archivos de vista estática:

```
ERROR: You need to install the Commerce application before running this utility.
```

**Solución**:

Siga estos pasos:

1. Instale el software de Commerce mediante la [línea de comandos](../../installation/composer.md).
1. Inicie sesión en el servidor de aplicaciones como propietario del sistema de archivos o [cambie a](../../installation/prerequisites/file-system/overview.md).
1. Elimine el contenido del directorio `<app_root>/pub/static`, excepto el archivo `.htaccess`. No elimine este archivo.
1. Implementar archivos de vista estática: `bin/magento setup:static-content:deploy`

## Sugerencia para que los desarrolladores personalicen la herramienta de implementación de contenido estático

Al crear una implementación personalizada de la herramienta de implementación de contenido estático, utilice únicamente la escritura de archivos atómicos para los archivos que deben estar disponibles en el cliente. Si utiliza la escritura de archivos no atómicos, esos archivos podrían cargarse en el cliente con contenido parcial.

Una de las opciones para hacerlo atómico es escribir en archivos almacenados en un directorio temporal y copiarlos o moverlos al directorio de destino (desde donde se cargan en el cliente) después de que termine la escritura. Para obtener más información sobre cómo escribir en archivos, consulte [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
