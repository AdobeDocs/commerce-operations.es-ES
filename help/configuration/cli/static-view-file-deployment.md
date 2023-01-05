---
title: Implementación de archivos de vista estáticos
description: Aprenda a escribir archivos estáticos en el sistema de archivos de Commerce durante el modo de producción.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '1135'
ht-degree: 0%

---


# Implementación de archivos de vista estáticos

{{file-system-owner}}

El comando static view files deploy permite escribir [archivos estáticos](https://glossary.magento.com/static-files) al sistema de archivos Commerce cuando el software Commerce esté configurado para [modo de producción](../bootstrap/application-modes.md#production-mode).

El término _archivo de vista estática_ hace referencia a lo siguiente:

- &quot;Estático&quot; significa que se puede almacenar en caché para un sitio (es decir, el archivo no se genera dinámicamente). Algunos ejemplos son imágenes y CSS generadas desde LESS.
- &quot;Vista&quot; se refiere a la capa de presentación (de MVC).

Los archivos de vista estáticos se encuentran en la variable `<magento_root>/pub/static` y algunos se almacenan en la caché del `<magento_root>/var/view_preprocessed` también.

La implementación de archivos de vista estática se ve afectada por los modos de aplicación de la siguiente manera:

- [Predeterminado](../bootstrap/application-modes.md#default-mode) y [desarrollador](../bootstrap/application-modes.md#developer-mode) modos: El comercio los genera bajo demanda, pero el resto se almacena en caché en un archivo para acelerar el acceso.
- [Producción](../bootstrap/application-modes.md#production-mode) modo: Los archivos estáticos son _not_ generado o almacenado en caché.

Debe escribir manualmente archivos de vista estáticos en el sistema de archivos de comercio mediante el comando abordado en este tema; después de esto, puede restringir los permisos para limitar sus vulnerabilidades y para evitar la sobrescritura accidental o maliciosa de archivos.

>[!WARNING]
>
>_Solo modo desarrollador_: Al instalar o habilitar un nuevo módulo, es posible que se carguen nuevos JavaScript, CSS, diseños, etc. Para evitar problemas con los archivos estáticos, debe limpiar los archivos antiguos para asegurarse de que obtiene todos los cambios para el nuevo módulo. Puede limpiar los archivos de vista estáticos generados de varias formas. Consulte [Limpiar el tema de la caché de archivos estáticos para obtener más información](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) para obtener más información.

**Para implementar archivos de vista estáticos**:

1. Inicie sesión en el servidor de comercio como o [cambie al propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Eliminar el contenido de `<magento_root>/pub/static`, excepto para el `.htaccess` archivo. No elimine este archivo.
1. Ejecute la herramienta de implementación de archivos de vista estática `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >Si habilita la combinación de archivos de vista estáticos en el Administrador, la variable `pub/static` sistema de directorios debe ser grabable.

   Opciones de comando:

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

La siguiente tabla explica los parámetros y valores de este comando.

| Opción | Descripción | ¿Requerido? |
| ------ | ----------- | --------- |
| `<languages>` | Lista separada por espacios de [ISO-639](https://www.loc.gov/standards/iso639-2/php/code_list.php) códigos de idioma para los que se van a generar archivos de vista estáticos. (El valor predeterminado es `en_US`.)<br>Busque la lista ejecutando: `bin/magento info:language:list` | No |
| `--language (-l)` | Genere archivos solo para los idiomas especificados. La opción predeterminada, sin especificar, es generar archivos para todos los códigos de idioma ISO-639. Puede especificar el nombre de un código de idioma a la vez. El valor predeterminado es **all**.<br>Por ejemplo: `--language en_US --language es_ES` | No |
| `--exclude-language` | Genere archivos para los códigos de idioma especificados. El valor predeterminado, sin opción especificada, es no excluir nada. Puede especificar el nombre de un código de idioma o una lista de códigos de idioma separados por coma. El valor predeterminado es **ninguno**. | No |
| `--theme <theme>` | Temas para los que implementar contenido estático. El valor predeterminado es **all**.<br>Por ejemplo: `--theme Magento/blank --theme Magento/luma` | No |
| `--exclude-theme <theme>` | Temas a excluir al implementar contenido estático. El valor predeterminado es **ninguno**.<br>Por ejemplo, `--exclude-theme Magento/blank` | No |
| `--area (-a)` | Genere archivos sólo para las áreas especificadas. La opción predeterminada, sin especificar, es generar archivos para todas las áreas. Los valores válidos son `adminhtml` y `frontend`. El valor predeterminado es **all**.<br>Por ejemplo: `--area adminhtml` | No |
| `--exclude-area` | No genere archivos para las áreas especificadas. El valor predeterminado, sin opción especificada, es no excluir nada. El valor predeterminado es **ninguno**. | No |
| `--jobs (-j)` | Habilite el procesamiento paralelo con el número especificado de trabajos. El valor predeterminado es 0 (no se ejecuta en procesos paralelos). El valor predeterminado es **0**. | No |
| `--symlink-locale` | Cree enlaces simbólicos para los archivos de esas configuraciones regionales, que se pasan para su implementación, pero que no tienen personalizaciones. | No |
| `--content-version=CONTENT-VERSION` | Se puede utilizar una versión personalizada del contenido estático si se ejecuta la implementación en varios nodos para garantizar que la versión del contenido estático sea idéntica y el almacenamiento en caché funcione correctamente. | No |
| `--no-javascript` | No implementar archivos JavaScript | No |
| `--no-css` | No implemente archivos CSS. | No |
| `--no-less` | No implemente archivos LESS. | No |
| `--no-images` | No implemente imágenes. | No |
| `--no-fonts` | No implemente archivos de fuente. | No |
| `--no-html` | No implemente archivos HTML. | No |
| `--no-misc` | No implemente otros tipos de archivos: MD, JBF, CSV, JSON, TXT, HTC, SWF | No |
| `--no-html-minify` | No minifique los archivos HTML. | No |
| `-s <quick\|standard\|compact>` | Defina la estrategia de implementación. Utilice estas opciones solo si tiene más de un local.<ul><li>Utilice la variable [estrategia rápida](static-view-file-strategy.md#quick-strategy) para minimizar el tiempo de implementación. Esta es la opción de comando predeterminada si no se especifica.</li><li>Utilice la variable [estrategia estándar](static-view-file-strategy.md#standard-strategy) para implementar todos los archivos de vista estáticos para todos los paquetes.</li><li>Utilice la variable [estrategia compacta](static-view-file-strategy.md#compact-strategy) para conservar espacio en disco en el servidor.</li></ul> | No |
| `--no-parent` | No genere archivos para los temas principales del tema actual. Se recomienda utilizar este indicador si no utiliza explícitamente el tema principal del tema actual que está intentando implementar. Esto aumenta significativamente la velocidad del proceso. Este indicador está disponible en Commerce 2.4.2 | No |
| `--force (-f)` | Implemente archivos en cualquier modo. (de forma predeterminada, la herramienta de implementación de contenido estático solo se puede ejecutar en modo de producción. Utilice esta opción para ejecutarla en modo predeterminado o de desarrollador). | No |

>[!INFO]
>
>Si especifica valores para ambas `<languages>` y `--language`, `<languages>` tiene prioridad.

## Ejemplos

A continuación se muestran algunos comandos de ejemplo.

### Exclusión de un tema y minificación de HTML

El siguiente comando implementa contenido estático para el inglés de EE. UU. (`en_US`), excluye el tema de Luma proporcionado con Commerce y no minimiza los archivos de HTML.

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

Salida de ejemplo:

```terminal
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

El siguiente comando implementa solo JavaScript, con 4 trabajos, con una estrategia de implementación estándar:

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

El siguiente comando implementa únicamente CSS y LESS con 3 trabajos y una estrategia de implementación rápida:

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### Generación de archivos de vista estáticos para un tema y un área

El siguiente comando genera archivos de vista estáticos para todos los idiomas, solo el área frontal, solo el tema Commerce Luma, sin generar fuentes:

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

Salida de ejemplo:

```terminal
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

## Implementar archivos de vista estáticos sin instalar Commerce

Es posible que desee ejecutar el proceso de implementación en un entorno independiente que no sea de producción, para evitar procesos de compilación en máquinas de producción sensibles.

Para ello, siga estos pasos:

1. Ejecutar [`bin/magento app:config:dump`](../cli/export-configuration.md) para exportar la configuración desde el sistema de producción.
1. Copie los archivos exportados a la base de código que no sea de producción.
1. Implementar archivos de vista estáticos: `bin/magento setup:static-content:deploy`

## Solución de problemas de la herramienta de implementación de archivos de vista estáticos

[Instale primero el software Commerce](../../installation/overview.md); de lo contrario, no puede ejecutar la herramienta de implementación de archivos de vista estáticos.

**Síntoma**: El siguiente error se muestra al ejecutar la herramienta de implementación de archivos de vista estática:

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**Solución**:

Siga estos pasos:

1. Instale el software Commerce utilizando el [línea de comandos](../../installation/composer.md).
1. Inicie sesión en el servidor de aplicaciones como o [cambiar a](../../installation/prerequisites/file-system/overview.md), el propietario del sistema de archivos.
1. Eliminar el contenido de `<app_root>/pub/static` , excepto para el `.htaccess` archivo. No elimine este archivo.
1. Implementar archivos de vista estáticos: `bin/magento setup:static-content:deploy`

## Sugerencia para desarrolladores que personalizan la herramienta de implementación de contenido estático

Al crear una implementación personalizada de la herramienta de implementación de contenido estático, utilice solamente la escritura atómica de archivos para los archivos que deberían estar disponibles en el cliente. Si utiliza la escritura de archivos no atómicos, es posible que esos archivos se carguen en el cliente con contenido parcial.

Una de las opciones para hacerlo atómico es escribir en archivos almacenados en un directorio temporal y copiarlos o moverlos al directorio de destino (desde donde se cargan al cliente) después de que la escritura haya terminado. Para obtener más información sobre cómo escribir en archivos, consulte [php fwrite](https://www.php.net/manual/en/function.fwrite.php).
