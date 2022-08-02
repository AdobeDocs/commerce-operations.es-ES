---
title: Diccionarios de traducción y paquetes de idiomas
description: Aprenda a generar diccionarios de traducción y a crear paquetes de idiomas.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 0%

---


# Localización

{{file-system-owner}}

Las traducciones comerciales le permiten personalizar y localizar su tienda para varias regiones y mercados mediante la generación de:

- **Diccionarios de traducción**, que son una forma cómoda de personalizar o traducir _some_ palabras y frases, como las de un módulo o tema personalizado.
- **Paquetes de idioma** que le permiten traducir _cualquiera o todos_ palabras y frases en la aplicación Commerce.

Consulte [Resumen de traducciones].

## Generar un diccionario de traducción

Puede generar un [diccionario de traducción] para personalizar cadenas existentes, traducir palabras y frases en un módulo personalizado, localizar un tema o crear [paquetes de idioma](https://glossary.magento.com/language-package).

Para empezar a traducir, utilice un comando para generar un archivo CSV de diccionario con una lista recopilada de todas las frases y palabras existentes.

Para generar el diccionario e iniciar la traducción:

1. Extraiga palabras y frases traducibles de componentes habilitados usando el comando de recopilación de traducción. El contenido se extrae en un archivo CSV.
1. Traduzca las palabras y frases existentes. Puede agregar otros términos personalizados según sea necesario.

   Tiene opciones para usar el diccionario traducido:

1. Puede empaquetar los diccionarios de traducción en un paquete de idioma y proporcionar el paquete al administrador de Commerce Store.

1. En el Administrador, el administrador del almacén [configura las traducciones].

Opciones de comando:

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

En la tabla siguiente se explican los parámetros y valores:

| Parámetro | Valor | ¿Requerido? |
|--- |--- |--- |
| `<path to directory to translate>` | Ruta a un directorio que tenga código traducible; en otras palabras, archivos PHP, PHTML o XML que tienen frases que traducir.<br><br>La herramienta comienza a buscar en la ruta que se introduce y busca todos los archivos y subdirectorios que contiene.<br><br>No utilice este parámetro si utiliza `-m --magento`. | Sí (diccionarios), no (paquetes). |
| `-m --magento` | Necesario para crear un paquete de idioma a partir de este diccionario de traducción. Si se utiliza, busca en los directorios que contienen bin/magento. Esta opción agrega temas o módulos a cada línea del diccionario.<br><br>A continuación se muestra una muestra:<br><br>&quot;No se encontraron elementos&quot;,&quot;No se encontraron elementos&quot;, módulo,Magento_lista de deseos | No |
| `-o --output="<path>"` | Especifica la ruta absoluta del sistema de archivos y el nombre de archivo del archivo CSV del diccionario de traducción que se va a crear. El valor introducido distingue entre mayúsculas y minúsculas. El nombre del archivo CSV debe coincidir exactamente con el nombre de la configuración regional, incluidas las mayúsculas y minúsculas de los caracteres.<br><br>Si omite este parámetro, la salida se dirige a stdout. | No |

>[!INFO]
>
>Para crear un paquete de idioma a partir de un diccionario de traducción, debe _must_ use el `-m|--magento` .

### Directrices de traducción

Utilice las siguientes directrices para traducir palabras y frases:

- Cambie solo el contenido de la segunda columna. Traducción de las frases al inglés (`US`) al idioma deseado.
- Al crear diccionarios para configuraciones regionales, utilice las cadenas de comercio predeterminadas.
- Mientras traduce, preste atención a los marcadores de posición: `%1`, `%2`

Commerce utiliza los marcadores de posición para insertar valores de contexto; son _not_ se utiliza para las traducciones. Por ejemplo:

```text
Product '%1' has been added to shopping cart.
```

Rellena con un valor:

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

La frase resultante debe contener al menos uno de cada marcador de posición. Por ejemplo, supongamos que hay marcadores de posición de `%1` a `%3` en la frase original. La traducción puede tener tantos de estos marcadores de posición en cualquier orden, pero debe haber al menos una incidencia de `%1`, `%2`y `%3`. La traducción no puede contener valores de marcador de posición que no estén presentes en el valor original (por ejemplo, `%4`, `%5`, etc.).

Ejemplo de traducción de una frase:

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Creación de un paquete de idioma

A diferencia de un diccionario de traducción, puede traducir cualquier palabra o frase en la aplicación Commerce utilizando un paquete de idioma. Puede traducir un componente concreto (como un módulo o un tema) mediante un diccionario de traducción. [Más información sobre paquetes de idiomas].

En esta sección se explica cómo crear un paquete de idioma, que escribe archivos CSV en módulos y temas. Para crear un paquete de idioma, debe realizar las tareas descritas en las siguientes secciones:

1. [Recopilar y traducir palabras y frases](#generate-a-translation-dictionary). (El `--magento` es obligatorio).
1. [Ejecute el comando paquete de idioma](#run-the-language-package-command).
1. [Creación de directorios y archivos](#create-directories-and-files).
1. (Opcional.) [Configurar varios paquetes para un idioma](#configure-multiple-packages-for-a-language).

### Ejecute el comando paquete de idioma

Uso de comandos:

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

La siguiente tabla explica los parámetros y valores del comando language package:

| Parámetro | Valor | ¿Requerido? |
|--- |--- |--- |
| `<source>` | Ruta absoluta del sistema de archivos y nombre de archivo de un archivo CSV que contiene el diccionario de traducción combinado y la metainformación necesaria para el desglose en un paquete de idioma.<br><br>Uso [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) para crear el archivo CSV, cree el paquete de idioma tal como se describe en [Creación de directorios y archivos](#m2devgde-xlate-files). | Sí |
| `<locale>` | [ISO 639-1] (idioma) y [ISO 3166] Identificador (país) del idioma utilizado como nombre de archivo para todos los archivos CSV resultantes. Ejemplos: `de_DE`, `pt_PT`, `pt_BR`. | Sí |
| `-m --mode` | Si existe un archivo de destino, especifica si se reemplazará el paquete de idioma existente o se combinará con el nuevo paquete de idioma. La combinación anula las frases existentes y agrega otras nuevas.<br><br>Valores: combinar o reemplazar (predeterminado). | No |
| `-d --allow-duplicates` | Incluya esta opción para permitir duplicados en el paquete de idioma. De lo contrario, el comando falla con un error si encuentra la misma frase en varias entradas con diferentes traducciones. | No |

### Creación de directorios y archivos

Los paquetes de idioma se encuentran en un directorio bajo `app/i18n/<VendorName>` en el sistema de archivos de Commerce con el siguiente contenido:

- Archivos de licencia necesarios
- `composer.json`
- `registration.php` that [registros] el paquete de idioma
- [`language.xml`](#language-package-languagexml) archivo de información meta

>[!INFO]
>
>Debe escribir en minúsculas toda la ruta. Por ejemplo, consulte [`de_de`].

Para crear estos archivos:

1. Cree un directorio en `app/i18n`.

   Por ejemplo, los paquetes de idioma comercial se encuentran en `app/i18n/magento`

1. Añada los archivos de licencia necesarios.
1. Agregar [`composer.json`] que especifica dependencias para el paquete de idioma.
1. Registre el paquete de idioma con [`registration.php`]
1. Agregar `language.xml` archivo de información meta tal como se describe en la sección siguiente.

#### Language package language.xml

Al declarar un paquete de idioma en la variable `language.xml` archivo de configuración, debe especificar la secuencia de la herencia de idioma para este paquete.

La herencia de idioma permite crear una traducción llamada _secundario_ en función de una traducción existente denominada _parent_. Las traducciones secundarias anulan al principal. Sin embargo, si la traducción secundaria no se carga o muestra, o si falta una frase o palabra, Commerce utiliza la traducción principal [locale](https://glossary.magento.com/locale). [Ejemplos de la herencia del paquete de idioma](#example-of-language-inheritance).

Para declarar un paquete, especifique la siguiente información:

```xml
<?xml version="1.0"?>
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>en_gb</package>
    <sort_order>100</sort_order>
    <use vendor="oxford-university" package="en_us"/>
</language>
```

Donde:

- `code`—Configuración regional del paquete de idioma (requerido)
- `vendor`—Nombre del proveedor del módulo (obligatorio)
- `package`—Nombre del paquete de idioma (obligatorio)
- `sort_order`—Prioridad de cargar un paquete cuando hay varios paquetes de idioma disponibles para una tienda
- `use`—Configuración regional del paquete de idioma principal de la cual heredar diccionarios

Si es necesario, puede especificar varios paquetes principales. Los paquetes principales se aplican por primera vez en la lista y se utilizan por primera vez.

#### Ejemplo de herencia de idioma

Supongamos que un paquete de idioma hereda de otros dos paquetes, y que esos paquetes también tienen paquetes principales y &quot;abuelos&quot;.

Si un paquete de idioma hereda de dos paquetes, su `language.xml` puede tener el siguiente aspecto:

```xml
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>language_pack</package>
    <sort_order>100</sort_order>
    <use vendor="parent-package-one" package="language_package_one"/>
    <use vendor= "parent-package-two" package="language_package_two"/>
</language>
```

En el ejemplo anterior:

- `language_package_one` hereda de `en_au_package` y `en_au_package` hereda de `en_ie_package`
- `language_package_two` hereda de `en_ca_package` y `en_ca_package` hereda de `en_us_package`

Si la aplicación Commerce no encuentra la palabra o frase en la variable `en_GB` , se busca en otros paquetes en la siguiente secuencia:

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

Si se especifican todas las heredaciones entre los paquetes de idioma, es posible que se creen cadenas de herencia circulares. Uso [Magento\Test\Integrity\App\Language\CircularDependencyTest] realice pruebas para localizar y corregir dichas cadenas.

### Configurar varios paquetes para un idioma

Para ayudarle a hacer su tienda más flexible, puede cargar varios paquetes de idiomas para el mismo idioma en su tienda. Por lo tanto, puede utilizar diferentes paquetes personalizados para diferentes partes de su tienda porque el sistema compila un solo paquete de todos los paquetes que están disponibles para un idioma.

Para habilitar un paquete adicional para un idioma existente, asigne un nombre al nuevo paquete con el nombre que no sea un nombre de código de idioma existente (para evitar confusiones). Especificar configuraciones de un paquete en el paquete de idioma `language.xml` archivo de información meta tal como se describe en la sección siguiente.

## Ejemplos del uso de comandos de traducción

Las siguientes secciones proporcionan ejemplos de uso integral de los comandos discutidos en este tema para crear diccionarios de traducción y paquetes de traducción:

### Ejemplo: Creación de un diccionario de traducción para un módulo o tema

Para agregar una traducción al alemán a un módulo o tema que desee distribuir a otros comerciantes:

1. Recopile frases de su módulo:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >El nombre del archivo CSV debe _match_ la configuración regional, incluido el caso de los caracteres.

1. Traducción de palabras y frases utilizando [estas directrices](#translation-guidelines).
1. Si es necesario, copie `xx_YY.csv` a `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` o al directorio de temas del módulo (dependiendo de si el diccionario de traducción es para un módulo o un tema).

### Ejemplo: Creación de un paquete de idioma

De forma similar al ejemplo anterior, genere un archivo CSV, pero en lugar de especificar un módulo o un directorio de temas, especifique todo el directorio raíz de la aplicación Commerce. El CSV resultante contiene todas las frases que el comando podría encontrar en el código.

1. Recopile frases de su módulo:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >El nombre del archivo CSV debe _match_ la configuración regional, incluido el caso de los caracteres.

1. Traducción de palabras y frases utilizando [estas directrices](#translation-guidelines).
1. Cree el paquete de idioma.

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. Cree un directorio para el paquete de idioma.

   Por ejemplo, `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. En ese directorio, agregue lo siguiente:

   - Una licencia, si es necesario
   - `composer.json` (ejemplo siguiente)
   - `registration.php` (ejemplo siguiente)
   - `language.xml` (ejemplo siguiente)

   **Ejemplo`composer.json`**:

   ```json
   {
       "name": "examplecorp/language-xx_yy",
       "description": "Sample language",
       "version": "100.0.2",
       "license": [
           "OSL-3.0",
           "AFL-3.0"
       ],
       "require": {
           "magento/framework": "100.0.*"
       },
       "type": "magento2-language",
       "autoload": {
           "files": [
               "registration.php"
           ]
       }
   }
   ```

   **Ejemplo`registration.php`**:

   ```php
   <?php
   /**
    * Copyright © Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **Ejemplo`language.xml`**:

   ```xml
   <?xml version="1.0"?>
   /**
   * Copyright © Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
   
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[Translate theme strings]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/translate_theory.html
[Resumen de traducciones]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html
[Community Engineering contributions]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#translations-project
[diccionario de traducción]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#m2devgde-xlate-dictionaries
[configura las traducciones]: https://docs.magento.com/user-guide/stores/store-language-add.html?Highlight=translation
[Más información sobre paquetes de idiomas]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#m2devgde-xlate-languagepack
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[registros]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/component-registration.html
[`de_de`]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[`composer.json`]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/composer-integration.html
[`registration.php`]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/component-registration.html
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
