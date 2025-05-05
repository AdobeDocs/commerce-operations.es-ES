---
title: Diccionarios de traducción y paquetes de idiomas
description: Obtenga información sobre cómo generar diccionarios de traducción y paquetes de idiomas.
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 4116d0983edc797ce42d24e711fb5ecdbf8fdec9
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 0%

---

# Localización

{{file-system-owner}}

Las traducciones de Commerce le permiten personalizar y localizar su tienda para varias regiones y mercados mediante la generación de:

- **Diccionarios de traducción**, que son una manera conveniente de personalizar o traducir _algunas_ palabras y frases, como las de un módulo o tema personalizado.
- **Paquetes de idioma** que le permiten traducir _cualquiera o todas las_ palabras y frases de la aplicación Commerce.

Ver [Resumen de traducciones].

## Generación de un diccionario de traducción

Puede generar un [diccionario de traducción] para personalizar las cadenas existentes, traducir palabras y frases en un módulo personalizado, localizar un tema o crear paquetes de idiomas.

Para empezar a traducir, utilice un comando para generar un archivo CSV de diccionario con una lista recopilada de todas las frases y palabras existentes.

Para generar el diccionario y comenzar la traducción:

1. Extraiga palabras y frases traducibles de los componentes habilitados mediante el comando de recopilación de traducción. El contenido se extrae en un archivo CSV.
1. Traducir las palabras y frases existentes. Puede agregar términos personalizados adicionales según sea necesario.

   Tiene opciones para utilizar el diccionario traducido:

1. Puede empaquetar los diccionarios de traducción en un paquete de idioma y proporcionar el paquete al administrador de la tienda de Commerce.

1. En el Administrador, el administrador del almacén [configura las traducciones].

Opciones de comando:

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

En la tabla siguiente se explican los parámetros y valores de:

| Parámetro | Valor | ¿Requerido? |
|--- |--- |--- |
| `<path to directory to translate>` | Ruta a un directorio que tiene código traducible; es decir, archivos PHP, PHTML o XML que tienen frases para traducir.<br><br>La herramienta empieza a buscar en la ruta de acceso especificada y busca en todos los archivos y subdirectorios que contiene.<br><br>No use este parámetro si usa `-m --magento`. | Sí (diccionarios), no (paquetes). |
| `-m --magento` | Necesario para crear un paquete de idioma a partir de este diccionario de traducción. Si se utiliza, busca en los directorios que contienen bin/magento. Esta opción agrega temáticas o módulos a cada línea del diccionario.<br><br>A continuación se muestra un ejemplo:<br><br>&quot;No se encontraron elementos&quot;,&quot;No se encontraron elementos&quot;,module,Magento_Wishlist | No |
| `-o --output="<path>"` | Especifica la ruta absoluta del sistema de archivos y el nombre del archivo CSV del diccionario de traducción que se va a crear. El valor que introduzca distingue entre mayúsculas y minúsculas. El nombre del archivo CSV debe coincidir exactamente con el nombre de la configuración regional, incluidas las mayúsculas y minúsculas.<br><br>Si omite este parámetro, el resultado se dirigirá a stdout. | No |

>[!INFO]
>
>Para crear un paquete de idioma a partir de un diccionario de traducción, _debe_ usar la opción `-m|--magento`.

### Directrices de traducción

Utilice las siguientes directrices al traducir palabras y frases:

- Cambie únicamente el contenido de la segunda columna. Traduzca las frases del inglés (`US`) al idioma deseado.
- Cuando cree diccionarios para configuraciones regionales, utilice las cadenas predeterminadas de Commerce.
- Mientras traduce, preste atención a los marcadores de posición: `%1`, `%2`

Commerce usa los marcadores de posición para insertar valores de contexto; se usan _no_ para las traducciones. Por ejemplo:

```text
Product '%1' has been added to shopping cart.
```

Rellena con un valor:

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

La frase resultante debe contener al menos uno de cada marcador de posición. Por ejemplo, supongamos que hay marcadores de posición de `%1` a `%3` en la frase original. La traducción puede tener tantos marcadores de posición como desee, pero debe haber al menos una incidencia de `%1`, `%2` y `%3`. La traducción no puede contener valores de marcador de posición que no estén presentes en el valor original (por ejemplo, `%4`, `%5`, etc.).

Un ejemplo de traducción de una frase:

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Creación de un paquete de idioma

A diferencia de un diccionario de traducción, puede traducir cualquiera o todas las palabras y frases de la aplicación de Commerce mediante un paquete de idiomas. Puede traducir un componente en particular, como un módulo o una temática, mediante un diccionario de traducción. [Más información sobre los paquetes de idiomas].

En esta sección se explica cómo crear un paquete de idioma, que escribe archivos CSV en módulos y temáticas. Para crear un paquete de idioma, debe realizar las tareas que se describen en las siguientes secciones:

1. [Recopilar y traducir palabras y frases](#generate-a-translation-dictionary). (El parámetro `--magento` es obligatorio).
1. [Ejecute el comando del paquete de idioma](#run-the-language-package-command).
1. [Crear directorios y archivos](#create-directories-and-files).
1. (Opcional.) [Configure varios paquetes para un idioma](#configure-multiple-packages-for-a-language).

### Ejecute el comando del paquete de idioma

Uso de comandos:

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

En la tabla siguiente se explican los parámetros y valores del comando del paquete de idioma:

| Parámetro | Valor | ¿Requerido? |
|--- |--- |--- |
| `<source>` | Ruta absoluta del sistema de archivos y nombre de archivo de un archivo CSV que contiene el diccionario de traducción combinado y la metainformación necesaria para el desglose en un paquete de idioma.<br><br>Use [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) para crear el archivo CSV y después cree el paquete de idioma como se describe en [Crear directorios y archivos](#m2devgde-xlate-files). | Sí |
| `<locale>` | El identificador de idioma [ISO 639-1] (idioma) y [ISO 3166] (país) usado como nombre de archivo para todos los archivos CSV resultantes. Ejemplos: `de_DE`, `pt_PT`, `pt_BR`. | Sí |
| `-m --mode` | Si existe un archivo de destino, especifica si se debe reemplazar el paquete de idioma existente o combinarlo con el nuevo. La combinación anula las frases que existían y agrega otras nuevas.<br><br>Valores: combinar o reemplazar (predeterminado). | No |
| `-d --allow-duplicates` | Incluya esta opción para permitir duplicados en el paquete de idioma. De lo contrario, el comando falla con un error si encuentra la misma frase en varias entradas con traducciones diferentes. | No |

### Crear directorios y archivos

Los paquetes de idioma se encuentran en un directorio bajo `app/i18n/<VendorName>` en el sistema de archivos de Commerce con el siguiente contenido:

- Archivos de licencia requeridos
- `composer.json`
- `registration.php` que [registra] el paquete de idioma
- [`language.xml`](#language-package-languagexml) archivo de metainformación

>[!INFO]
>
>Debe escribir en minúsculas toda la ruta. Por ejemplo, vea [`de_de`].

Para crear estos archivos:

1. Cree un directorio en `app/i18n`.

   Por ejemplo, los paquetes de idioma de Commerce se encuentran en `app/i18n/magento`

1. Añada los archivos de licencia necesarios.
1. Agregue [`composer.json`] que especifique las dependencias del paquete de idioma.
1. Registrar el paquete de idioma con [`registration.php`]
1. Agregar `language.xml` archivo de metainformación como se describe en la siguiente sección.

#### Paquete de idioma language.xml

Al declarar un paquete de idioma en el archivo de configuración `language.xml`, debe especificar la secuencia de la herencia de idioma para este paquete.

La herencia de idiomas le permite crear una traducción llamada _elemento secundario_ basada en una traducción existente llamada _elemento principal_. Las traducciones secundarias anulan a la principal. Sin embargo, si la traducción secundaria no se puede cargar o mostrar, o si falta una frase o palabra, Commerce utiliza la configuración regional principal. [Ejemplos de herencia del paquete de idioma](#example-of-language-inheritance).

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

- `code`: configuración regional del paquete de idioma (obligatorio)
- `vendor`: nombre de proveedor del módulo (obligatorio)
- `package`: nombre del paquete de idioma (obligatorio)
- `sort_order`: prioridad al cargar un paquete cuando hay varios paquetes de idioma disponibles para una tienda.
- `use`: configuración regional del paquete de idioma principal desde la que heredar diccionarios

Si es necesario, puede especificar varios paquetes principales. Los paquetes principales se aplican según la primera lista y el primer uso.

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

Si la aplicación Commerce no encuentra palabras o frases en el paquete `en_GB`, busca en otros paquetes en la siguiente secuencia:

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

Si especifica todas las herencias entre los paquetes de idioma, se podrían crear cadenas de herencia circulares. Use la prueba [Magento\Test\Integrity\App\Language\CircularDependencyTest] para localizar y corregir estas cadenas.

### Configuración de varios paquetes para un idioma

Para que tu tienda sea más flexible, puedes cargar varios paquetes de idiomas para el mismo idioma en tu tienda. Por lo tanto, puede utilizar diferentes paquetes personalizados para diferentes partes del almacén porque el sistema compila un solo paquete de todos los paquetes disponibles para un idioma.

Para habilitar un paquete adicional para un idioma existente, asigne al nuevo paquete cualquier nombre excepto el nombre de un código de idioma existente (para evitar confusiones). Especifique las configuraciones de un paquete en el archivo de metainformación `language.xml` del paquete de idioma, tal como se describe en la siguiente sección.

## Ejemplos de uso de comandos de traducción

Las siguientes secciones proporcionan ejemplos completos del uso de los comandos mencionados en este tema para crear diccionarios de traducción y paquetes de traducción:

### Ejemplo: Creación de un diccionario de traducción para un módulo o tema

Para agregar una traducción al alemán a un módulo o tema que desee distribuir a otros comerciantes:

1. Recopile frases de su módulo:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >El nombre del archivo CSV debe _coincidir exactamente_ con la configuración regional, incluidas las mayúsculas y minúsculas de los caracteres.

1. Traduzca las palabras y frases utilizando [estas directrices](#translation-guidelines).
1. Si es necesario, copie `xx_YY.csv` en `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` o en el directorio de temas del módulo (dependiendo de si el diccionario de traducción es para un módulo o un tema).

### Ejemplo: Creación de un paquete de idioma

De forma similar al ejemplo anterior, genere un archivo CSV, pero en lugar de especificar un directorio de módulo o tema, especifique todo el directorio raíz de la aplicación de Commerce. El CSV resultante contiene todas las frases que el comando pudo encontrar en el código.

1. Recopile frases de su módulo:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >El nombre del archivo CSV debe _coincidir exactamente_ con la configuración regional, incluidas las mayúsculas y minúsculas de los caracteres.

1. Traduzca las palabras y frases utilizando [estas directrices](#translation-guidelines).
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
    * Copyright [first year code created] Adobe
    * All Rights Reserved.
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
   <!--
   Copyright [first year code created] Adobe
   All Rights Reserved.
   -->
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[Resumen de traducciones]: https://developer.adobe.com/commerce/frontend-core/guide/translations/
[diccionario de traducción]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries
[configura las traducciones]: https://experienceleague.adobe.com/es/docs/commerce-admin/stores-sales/site-store/store-localize
[Más información sobre los paquetes de idiomas]: https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[registros]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[`de_de`]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[`composer.json`]: https://developer.adobe.com/commerce/php/development/build/composer-integration/
[`registration.php`]: https://developer.adobe.com/commerce/php/development/build/component-registration/
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
