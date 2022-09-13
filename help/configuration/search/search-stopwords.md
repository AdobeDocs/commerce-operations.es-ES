---
title: Configurar palabras clave de búsqueda
description: Obtenga información sobre cómo administrar palabras clave para Adobe Commerce mediante archivos CSV.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---


# Configurar palabras clave de búsqueda

En general, _palabras clave_ son palabras comunes que los motores de búsqueda filtran después de procesar texto. Originalmente, cuando el espacio en disco y la memoria eran extremadamente limitados, cada kilobyte ahorrado significaba una mejora significativa en el rendimiento. Por lo tanto, los motores de búsqueda obtuvieron ganancias de rendimiento ignorando ciertas palabras y manteniendo el índice pequeño.

Aunque hoy tenemos más almacenamiento de información, el performance sigue siendo importante. Elasticsearch y OpenSearch, al igual que otros motores de búsqueda, siguen usando palabras clave para mejorar el rendimiento.

Debe administrar las palabras clave utilizando archivos CSV ubicados en la variable `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` o `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` , dependiendo de cómo haya instalado el software Commerce.

Para obtener más información sobre cómo Elasticsearch y OpenSearch utilizan palabras clave, consulte los siguientes recursos:

- [Palabras clave: Rendimiento frente a precisión](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [Ventajas e inconvenientes de las palabras clave](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [Uso de palabras clave](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Palabras clave y rendimiento](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Configurar palabras clave

Las palabras clave se encuentran en la variable `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` directorio. Adobe Commerce y Magento Open Source se envían con un archivo CSV que contiene palabras clave para las configuraciones regionales predeterminadas y un archivo adicional, `stopwords.csv`, que tiene palabras clave para cualquier configuración regional que no esté representada por otro archivo CSV.

Duración predeterminada del archivo de palabras clave [cache](https://glossary.magento.com/cache) es de 15 minutos.

### Editar palabras clave para una configuración regional existente

**Para editar palabras clave**:

1. Inicie sesión en el servidor de Commerce o cambie a la [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
1. Utilice un editor de texto para abrir un archivo de palabra clave en la variable `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` directorio.

   Los archivos CSV utilizan la convención de nomenclatura `stopwords_<locale_code>.csv`. Por ejemplo, el nombre del archivo de palabra clave alemana es `stopwords_de_DE.csv`.

1. Agregue palabras, elimine palabras o cambie palabras en el archivo.

   (Cada palabra clave de un archivo comienza en una nueva línea).

1. Guarde los cambios y salga del editor de texto.
1. Limpie la caché de configuración.

   - Administrador: **Sistema** > Herramientas > **Administración de caché**. Seleccione el **Configuración** y, en la lista anterior, haga clic en **Actualizar**. Haga clic en **Submit** para completar la acción.

   - Línea de comandos: Como propietario del sistema de archivos, introduzca el siguiente comando:

      ```bash
      php <magento_root>/bin/magento cache:clean config
      ```

1. Compruebe los resultados buscando términos en su [storefront](https://glossary.magento.com/storefront).

### Crear palabras clave para una nueva configuración regional

**Agregar palabras clave para una configuración regional**:

1. Inicie sesión en el servidor de Commerce o cambie a la [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).

1. Utilice un editor de texto para crear un archivo de palabra clave denominado `stopwords_<locale_code>.csv` en el `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` directorio.

   Por ejemplo, para crear palabras clave para la configuración regional italiana, asigne un nombre al archivo `stopwords_it_IT.csv`.

1. En su archivo de palabra clave, asegúrese de que cada palabra de cierre esté en una línea separada.
1. Guarde los cambios y salga del editor de texto.
1. En el mismo directorio, abra `esconfig.xml` en un editor de texto.
1. Añadir una línea a `esconfig.xml` de la siguiente manera:

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Por ejemplo, para agregar un archivo de palabra de corte italiano, agregue la línea siguiente:

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. Guarde los cambios en `esconfig.xml` y salga del editor de texto.
1. Limpie la caché de configuración.

   - Administrador: **Sistema** > Herramientas > **Administración de caché**. Seleccione el **Configuración** y, en la lista anterior, haga clic en **Actualizar**. Haga clic en **Submit** para completar la acción.

   - Línea de comandos: Como propietario del sistema de archivos, introduzca el siguiente comando:

      ```bash
      php <magento_root>/bin/magento magento cache:clean config
      ```

1. Compruebe los resultados buscando términos en su tienda.

## Cambiar el directorio de palabras clave

En esta sección se explica cómo cambiar opcionalmente el directorio de palabras clave predeterminado de uno de los siguientes elementos:

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

La ubicación depende de cómo haya instalado el software Commerce. Si clona el repositorio de GitHub de Magento 2, la ruta se encuentra en `app/code`. Si ha instalado un archivo comprimido o un paquete de metapacaídas, la ruta se encuentra debajo de `vendor`.

**Para cambiar el directorio**:

1. Como propietario del sistema de archivos, abra el Elasticsearch `di.xml` en un editor de texto.

   Si clona el repositorio, se encuentra en `app/code/Magento/Elasticsearch/etc/di.xml`

   Si tienes un archivo o el metapacaol, se encuentra en `vendor/magento/module-elasticsearch/etc/di.xml`

1. Cambiar el valor de `stopwordsDirectory` al directorio deseado:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Guarde los cambios en `di.xml` y salga del editor de texto.

## Para cambiar el directorio del módulo

1. [Creación de un módulo](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. En el módulo `etc/di.xml` añadir instrucciones:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. En el módulo, cree el directorio . `etc/stopwords`, con el archivo CSV correspondiente.

1. Guarde los cambios en `di.xml` y salga del editor de texto.
