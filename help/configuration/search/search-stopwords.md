---
title: Configurar palabras de parada de búsqueda
description: Obtenga información sobre cómo administrar palabras de detención para Adobe Commerce mediante archivos CSV.
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# Configurar palabras de parada de búsqueda

En general, _stopwords_ son palabras comunes que los motores de búsqueda filtran después de procesar el texto. En un principio, cuando el espacio en disco y la memoria eran extremadamente limitados, cada kilobyte ahorrado significaba una mejora significativa en el rendimiento. Por lo tanto, los motores de búsqueda lograron mejoras en el rendimiento al ignorar ciertas palabras y mantener el índice pequeño.

Aunque hoy tenemos más almacenamiento, el rendimiento sigue siendo importante. Elasticsearch y OpenSearch, al igual que otros motores de búsqueda, siguen utilizando palabras de detención para mejorar el rendimiento.

Debe administrar las palabras de detención mediante archivos CSV ubicados en el directorio `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` o en el directorio `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`, según la instalación del software de Commerce.

Para obtener más información sobre cómo Elasticsearch y OpenSearch utilizan palabras de parada, consulte los siguientes recursos:

- [Palabras de parada: rendimiento frente a precisión](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [Ventajas e inconvenientes de las palabras clave](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [Usar palabras de detención](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Palabras de parada y rendimiento](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Configurar palabras de parada

Las palabras de detención se encuentran en el directorio `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`. Adobe Commerce incluye un archivo CSV que contiene palabras de parada para las configuraciones regionales predeterminadas y un archivo adicional, `stopwords.csv`, que tiene palabras de parada para cualquier configuración regional que no esté representada por otro archivo CSV.

La duración predeterminada de la caché del archivo de palabras de parada es de 15 minutos.

### Editar palabras de parada para una configuración regional existente

**Para editar palabras de detención**:

1. Inicie sesión en el servidor de Commerce o cambie a [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Use un editor de texto para abrir un archivo de palabras de detención en el directorio `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`.

   Los archivos CSV utilizan la convención de nomenclatura `stopwords_<locale_code>.csv`. Por ejemplo, el nombre del archivo de palabras de detención en alemán es `stopwords_de_DE.csv`.

1. Agregar palabras, quitar palabras o cambiar palabras en el archivo.

   (Cada palabra de parada de un archivo comienza en una nueva línea).

1. Guarde los cambios y salga del editor de texto.
1. Limpie la caché de configuración.

   - Administrador: **Sistema** > Herramientas > **Administración de caché**. Seleccione la casilla de verificación **Configuración** y, en la lista superior, haga clic en **Actualizar**. Haga clic en **Enviar** para completar la acción.

   - Línea de comandos: Como propietario del sistema de archivos, introduzca el siguiente comando:

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. Comprueba los resultados buscando términos en tu tienda.

### Crear palabras de parada para una nueva configuración regional

**Para agregar palabras de parada para una configuración regional**:

1. Inicie sesión en el servidor de Commerce o cambie a [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).

1. Use un editor de texto para crear un archivo de palabras de detención denominado `stopwords_<locale_code>.csv` en el directorio `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`.

   Por ejemplo, para crear palabras de parada para la configuración regional italiana, asigne un nombre al archivo `stopwords_it_IT.csv`.

1. En el archivo de palabras de detención, asegúrese de que cada palabra de detención está en una línea separada.
1. Guarde los cambios y salga del editor de texto.
1. En el mismo directorio, abra `esconfig.xml` en un editor de texto.
1. Agregue una línea a `esconfig.xml` de la siguiente manera:

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Por ejemplo, para agregar un archivo de palabras de cierre en italiano, agregue la siguiente línea:

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. Guarde los cambios en `esconfig.xml` y salga del editor de texto.
1. Limpie la caché de configuración.

   - Administrador: **Sistema** > Herramientas > **Administración de caché**. Seleccione la casilla de verificación **Configuración** y, en la lista superior, haga clic en **Actualizar**. Haga clic en **Enviar** para completar la acción.

   - Línea de comandos: Como propietario del sistema de archivos, introduzca el siguiente comando:

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. Comprueba los resultados buscando términos en tu tienda.

## Cambiar el directorio de palabras de detención

En esta sección se explica cómo cambiar de forma opcional el directorio de palabras de detención predeterminado de una de las siguientes opciones:

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

La ubicación depende de cómo haya instalado el software de Commerce. Si ha clonado el repositorio de GitHub de Magento 2, la ruta de acceso es `app/code`. Si instaló un archivo comprimido o un metapaquete, la ruta de acceso es de `vendor`.

**Para cambiar el directorio**:

1. Como propietario del sistema de archivos, abra Elasticsearch `di.xml` en un editor de texto.

   Si clonó el repositorio, se encuentra en `app/code/Magento/Elasticsearch/etc/di.xml`

   Si tiene un archivo o el metapaquete, se encuentra en `vendor/magento/module-elasticsearch/etc/di.xml`

1. Cambie el valor de `stopwordsDirectory` al directorio deseado:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Guarde los cambios en `di.xml` y salga del editor de texto.

## Para cambiar el directorio desde el módulo

1. [Crear un módulo](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. En su módulo `etc/di.xml` agregue instrucciones:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. En su módulo, cree el directorio `etc/stopwords`, con el archivo CSV correspondiente.

1. Guarde los cambios en `di.xml` y salga del editor de texto.
