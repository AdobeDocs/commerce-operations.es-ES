---
title: Paquete  [!DNL JavaScript] avanzado
description: Obtenga información sobre cómo el paquete de JavaScript puede reducir el tamaño y la frecuencia de las solicitudes de servidor.
exl-id: 81a313f8-e541-4da6-801b-8bbd892d6252
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2134'
ht-degree: 0%

---

# Paquete [!DNL JavaScript] avanzado

Agrupar [!DNL JavaScript] módulos para obtener un mejor rendimiento implica reducir dos cosas:

1. Número de solicitudes del servidor.
1. El tamaño de esas solicitudes de servidor.

En una aplicación modular, el número de solicitudes de servidor puede alcanzar los cientos. Por ejemplo, la captura de pantalla siguiente muestra solamente el inicio de la lista de [!DNL JavaScript] módulos cargados en la página principal de una instalación limpia.

![Sin agrupamiento](../assets/performance/images/noBundling.png)

## Combinación y agrupamiento

De serie, [!DNL Commerce] proporciona dos formas de reducir el número de solicitudes de servidor: combinando y agrupando. Esta configuración está desactivada de forma predeterminada. Puede activarlos en la interfaz de usuario de administración en **[!UICONTROL Stores]** > **Configuración** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL [!DNL JavaScript] Settings]**, o desde la línea de comandos.

![Paquete](../assets/performance/images/bundlingImage.png)

### Agrupación básica

Para habilitar el agrupamiento integrado desde la línea de comandos:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

Este es un mecanismo [!DNL Commerce] nativo que combina todos los recursos presentes en el sistema y los distribuye entre paquetes del mismo tamaño (bundle_0.js, bundle_1.js ... bundle_x.js):

![[!DNL Commerce] paquete](../assets/performance/images/magentoBundling.png)

Mejor, pero el explorador sigue cargando TODOS los paquetes de [!DNL JavaScript], no solo los necesarios.

El paquete [!DNL Commerce] reduce el número de conexiones por página, pero para cada solicitud de página carga todos los paquetes, incluso cuando la página solicitada solo puede depender de archivos dentro de uno o dos de los paquetes. El rendimiento mejora después de que el explorador almacene en caché los paquetes. Sin embargo, como el explorador carga estos paquetes sincrónicamente, la primera visita del usuario a una tienda de [!DNL Commerce] podría tardar un poco en procesarse y dañar la experiencia del usuario.

### Combinación básica

Para habilitar la combinación integrada desde la línea de comandos:

```bash
php -f bin/magento config:set dev/js/merge_files 1
```

Este comando combina todos los archivos sincrónicos de [!DNL JavaScript] en un archivo. Habilitar la combinación sin habilitar también el agrupamiento no es útil porque [!DNL Commerce] usa RequireJS. Si no habilita el agrupamiento, [!DNL Commerce] solo combina RequireJS y su configuración. Al habilitar el agrupamiento y la combinación, [!DNL Commerce] crea un solo archivo [!DNL JavaScript]:

![Combinación en el mundo real](../assets/performance/images/magentoMergingDevWorld.png)

## Tiempos de procesamiento reales

Los tiempos de carga agrupados y combinados anteriores tienen un aspecto excelente en un entorno de desarrollo. Pero en el mundo real, muchas cosas pueden ralentizar el renderizado: conexiones lentas, umbrales de conexión grandes, redes limitadas. Además, los dispositivos móviles no se representan tan rápido como los equipos de escritorio.

Para probar y preparar la implementación de tu tienda para el mundo real, te recomendamos que pruebes con el perfil nativo de regulación de Chrome &quot;Slow 3G&quot;. Con Slow 3G, nuestros tiempos de salida agrupados anteriores ahora reflejan las realidades de conexión de muchos usuarios:

![Paquete para el mundo real](../assets/performance/images/magentoBundlingRealWorld.png)

Con una conectividad 3G lenta, se tardan unos 44 segundos en cargar todos los paquetes para la página principal de una instalación [!DNL Commerce] limpia.

Lo mismo ocurre al combinar los paquetes en un solo archivo. Los usuarios aún pueden esperar alrededor de 42 segundos para la carga inicial de la página, como se muestra a continuación:

![Combinación en el mundo real](../assets/performance/images/magentoMergingRealWorld.png)

Con un enfoque más avanzado para el agrupamiento de [!DNL JavaScript], podemos mejorar estos tiempos de carga.

## Agrupación avanzada

Recuerde, el objetivo del agrupamiento de [!DNL JavaScript] es reducir el número y el tamaño de los recursos solicitados para cada página cargada en el explorador. Para ello, queremos crear nuestros paquetes para que cada página de nuestra tienda solo necesite descargar un paquete común y un paquete específico para cada página a la que se acceda.

Una manera de conseguirlo es definir los paquetes por tipos de página. Puede clasificar las páginas de [!DNL Commerce] en varios tipos de página, incluidos Categoría, Producto, CMS, Cliente, Carro de compras y Cierre de compra. Cada página clasificada en uno de estos tipos de página tiene un conjunto diferente de dependencias del módulo RequireJS. Cuando agrupa los módulos RequireJS por tipo de página, acaba teniendo solo un puñado de paquetes que cubren las dependencias de cualquier página de su tienda.

Por ejemplo, puede terminar con un paquete para las dependencias comunes a todas las páginas, un paquete para páginas solo CMS, un paquete para páginas solo catálogo, otro paquete para páginas solo búsqueda y un paquete para páginas de cierre de compra.

También puede crear paquetes por propósito: para funciones comunes, funciones relacionadas con productos, funciones de envío, funciones de cierre de compra, impuestos y validaciones de formularios. La forma de definir los paquetes depende de usted y de la estructura de su tienda. Es posible que algunas estrategias de agrupamiento funcionen mejor que otras.

Una instalación limpia de [!DNL Commerce] permite alcanzar un rendimiento suficientemente bueno dividiendo los paquetes por tipos de página, pero algunas personalizaciones pueden requerir un análisis más profundo y otras distribuciones de recursos.

### Herramientas necesarias

Los siguientes pasos requieren que instale y esté familiarizado con las siguientes herramientas:

- [nodejs](https://nodejs.org/en/download/)
- [r.js](http://requirejs.org/docs/optimization.html#download)
- [[!DNL PhantomJS]](https://phantomjs.org/) (opcional)

### Código de muestra

Las versiones completas del código de ejemplo utilizado en este artículo están disponibles aquí:

- [build.js](../assets/performance/code-samples/build.js)
- [deps.js](../assets/performance/code-samples/deps.js)
- [deps-map.sh](../assets/performance/code-samples/deps-map.sh.txt)

### Parte 1: Crear una configuración de paquete

#### 1\. Añadir un archivo build.js

Crear un archivo de `build.js` en el directorio raíz de [!DNL Commerce]. Este archivo contendrá toda la configuración de compilación de los paquetes.

```javascript
({
    optimize: 'none',
    inlineText: true
})
```

Más adelante, cambiaremos la configuración de `optimize:` de_ `none` a `uglify2` para minimizar la salida del paquete. Pero por ahora, durante el desarrollo, puede dejarlo establecido en `none` para garantizar compilaciones más rápidas.

#### 2\. Agregar dependencias, correcciones de compatibilidad, rutas y asignaciones de RequireJS

Agregue los siguientes nodos de configuración de compilación de RequireJS, `deps`, `shim`, `paths` y `map`, a su archivo de compilación:

```javascript
({
    optimize: 'none',
    inlineText: true,

    deps: [],
    shim: {},
    paths: {},
    map: { "*": {} },
})
```

#### 3\. Agregue los valores de instancia requirements-config.js

En este paso, tendrá que agregar todos los nodos de configuración de `deps`, `shim`, `paths` y `map` del archivo `requirejs-config.js` de su tienda a los nodos correspondientes del archivo `build.js`. Para ello, puede abrir la pestaña **[!UICONTROL Network]** en el panel Herramientas para desarrolladores del explorador y navegar a cualquier página de la tienda, como la página principal. En la pestaña Red, verá la instancia del archivo `requirejs-config.js` que tiene su tienda cerca de la parte superior y que se resalta aquí:

![Requerir configuración de JS](../assets/performance/images/RequireJSConfig.png)

Dentro de este archivo, encontrará varias entradas para cada uno de los nodos de configuración (`deps`, `shim`, `paths`, `map`). Debe agregar estos valores de varios nodos al nodo de configuración único del archivo build.js. Por ejemplo, si la instancia `requirejs-config.js` de su almacén tiene entradas para 15 nodos `map` separados, deberá combinar las entradas de los 15 nodos en el nodo `map` único del archivo `build.js`. Lo mismo ocurrirá con los nodos `deps`, `shim` y `paths`. Sin un script para automatizar este proceso, puede llevar tiempo.

Deberá cambiar la ruta de acceso `mage/requirejs/text` a `requirejs/text` en el nodo de configuración `paths` de la siguiente manera:

```javascript
({
    //...
    paths: {
        //...
        "text": "requirejs/text"
    },
})
```

#### 4\. Añadir un nodo de módulos

Al final del archivo `build.js`, agregue la matriz module[] como marcador de posición para los paquetes que definirá para su tienda más adelante.

```javascript
({
    optimize: 'none',
    inlineText: true,

    deps: [],
    shim: {},
    paths: {},
    map: { "*": {} },

    modules: [],
})
```

#### 5\. Recuperar dependencias de RequireJS

Puede recuperar todas las dependencias del módulo [!DNL RequireJS] de los tipos de página del almacén mediante:

1. [!DNL PhantomJS] desde la línea de comandos (suponiendo que tenga [!DNL PhantomJS] instalado).
1. Requiera el comando JS en la consola del explorador.

#### Para usar [!DNL PhantomJS]:

En el directorio raíz [!DNL Commerce], cree un nuevo archivo llamado `deps.js` y copie el código siguiente. Este código utiliza [!DNL [!DNL PhantomJS]] para abrir una página y esperar a que el explorador cargue todos los recursos de la página. Luego genera todas las dependencias [!DNL RequireJS] para una página determinada.

```javascript
"use strict";
var page = require('webpage').create(),
    system = require('system'),
    address;

if (system.args.length === 1) {
    console.log('Usage: $phantomjs deps.js url');
    phantom.exit(1);
} else {
    address = system.args[1];
    page.open(address, function (status) {
        if (status !== 'success') {
            console.log('FAIL to load the address');
        } else {
            setTimeout(function () {
                console.log(page.evaluate(function () {
                    return Object.keys(window.require.s.contexts._.defined);
                }));
                phantom.exit();
            }, 5000);
        }
    });
}
```

Abra un terminal dentro del directorio raíz [!DNL Commerce] y ejecute el script con cada página del almacén que represente un tipo de página específico:

<pre>
phantomjs deps.js <i>url-to-specific-page</i> &gt; <i>text-file-representation-pagetype-dependencies</i>
</pre>

Por ejemplo, aquí hay cuatro páginas de la tienda de muestras con temas de Luma que representan los cuatro tipos de página que utilizaremos para crear nuestros cuatro paquetes (página principal, categoría, producto, carro de compras):

```terminal
phantomjs deps.js http://m2.loc/ > bundle/homepage.txt
phantomjs deps.js http://m2.loc/women/tops-women/jackets-women.html > bundle/category.txt
phantomjs deps.js http://m2.loc/beaumont-summit-kit.html > bundle/product.txt
phantomjs deps.js http://m2.loc/checkout/cart/?SID=m2tjdt7ipvep9g0h8pmsgie975 > bundle/cart.txt (prepare a shopping cart)
..............
```

#### Para utilizar la consola del explorador:

Si no desea usar [!DNL PhantomJS], puede ejecutar el siguiente comando desde la consola del explorador mientras ve cada tipo de página en la tienda:

```shell
Object.keys(window.require.s.contexts._.defined)
```

Este comando (utilizado en el script [!DNL PhantomJS]) crea la misma lista de dependencias [!DNL RequireJS] y las muestra en la consola del explorador. La desventaja de este enfoque es que tendrá que crear sus propios archivos de texto de tipo paquete/página.

#### 6\. Dar formato y filtrar la salida

Después de combinar las dependencias [!DNL RequireJS] en archivos de texto de tipo de página, puede utilizar el siguiente comando en cada archivo de dependencia de tipo de página para reemplazar las comas de los archivos por líneas nuevas:

```terminal
sed -i -e $'s/,/\\\n/g' bundle/category.txt
sed -i -e $'s/,/\\\n/g' bundle/homepage.txt
sed -i -e $'s/,/\\\n/g' bundle/product.txt
....
```

También debe quitar todos los mixins de cada archivo porque los mixins duplican dependencias. Utilice el siguiente comando en cada archivo de dependencia:

```terminal
sed -i -e 's/mixins\!.*$//g' bundle/homepage.txt
sed -i -e 's/mixins\!.*$//g' bundle/category.txt
sed -i -e 's/mixins\!.*$//g' bundle/product.txt
...
```

#### 7\. Identificación de paquetes únicos y comunes

El objetivo es crear un paquete común de [!DNL JavaScript] archivos necesarios para todas las páginas. De este modo, el explorador solo necesita cargar el paquete común junto con uno o más tipos de página específicos.

Abra un terminal en el directorio raíz [!DNL Commerce] y utilice el siguiente comando para comprobar que dispone de dependencias que puede dividir en paquetes independientes:

```bash
sort bundle/*.txt |uniq -c |sort -n
```

Este comando combina y ordena las dependencias encontradas en los archivos `bundle/*.txt`.  El resultado también muestra el número de archivos que contienen cada dependencia:

```terminal
1 buildTools,
1 jquery/jquery.parsequery,
1 jsbuild,
2 jquery/jquery.metadata,
2 jquery/validate,
2 mage/bootstrap,
3 jquery
3 jquery/ui
3 knockoutjs/knockout
...
```

Este resultado muestra que `buildTools` es una dependencia solamente en uno de los archivos bundle/*.txt. La dependencia `jquery/jquery.metadata` se encuentra en dos (2) archivos y `es6-collections` en tres (3) archivos.

Nuestra salida muestra solo tres tipos de página (página principal, categoría y producto), lo que nos indica:

- Tres dependencias son únicas para un solo tipo de página (mostrado por el número 1).
- Hay tres dependencias más en dos tipos de página (el número 2 lo muestra).
- Las tres últimas dependencias son comunes a los tres tipos de página (indicados por el número 3).

Esto nos indica que es probable que podamos mejorar las velocidades de carga de páginas de nuestra tienda dividiendo nuestras dependencias en diferentes paquetes, una vez que sepamos qué tipos de página necesitan qué dependencias.

#### 8\. Creación de un archivo de distribución de dependencias

Para saber qué tipos de página necesitan qué dependencias, cree un nuevo archivo en el directorio raíz [!DNL Commerce] llamado `deps-map.sh` y copie el código siguiente:

```shell
awk 'END {
 for (R in rec) {
   n = split(rec[R], t, "/")
   if (n > 1)
     dup[n] = dup[n] ? dup[n] RS sprintf("\t%-20s -->\t%s", rec[R], R) : \
       sprintf("\t%-20s -->\t%s", rec[R], R)
   }
 for (D in dup) {
   printf "records found in %d files:\n\n", D
   printf "%s\n\n", dup[D]
   }
 }
{
 rec[$0] = rec[$0] ? rec[$0] "/" FILENAME : FILENAME
}' bundle/*.txt
```

También puede encontrar el script en [https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html](https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html)

Abra un terminal en el directorio raíz [!DNL Commerce] y ejecute el archivo:

```bash
bash deps-map.sh
```

El resultado de este script, aplicado a nuestros tres tipos de página de ejemplo, debería tener un aspecto similar al siguiente (pero mucho más largo):

```terminal
bundle/product.txt   -->   buildTools,
bundle/category.txt  -->   jquery/jquery.parsequery,
bundle/product.txt   -->   jsbuild,

bundle/category.txt/bundle/homepage.txt -->    jquery/jquery.metadata,
bundle/category.txt/bundle/homepage.txt -->    jquery/validate,
bundle/category.txt/bundle/homepage.txt -->    mage/bootstrap,

bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> jquery,
bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> jquery/ui,
bundle/category.txt/bundle/homepage.txt/bundle/product.txt --> knockoutjs/knockout,
```

Esta información es suficiente para crear una configuración de paquetes.

#### 9\. Creación de paquetes en el archivo build.js

Abra el archivo de configuración `build.js` y agregue los paquetes al nodo `modules`. Cada paquete debe definir las siguientes propiedades:

- `name`: el nombre del paquete. Por ejemplo, un nombre de `bundles/cart` genera un paquete `cart.js` en un subdirectorio `bundles`.

- `create`: un indicador booleano para crear el paquete (valores: `true` o `false`).

- `include`: una matriz de recursos (cadenas) incluidos como dependencias para la página. RequireJS rastrea todas las dependencias e las incluye en el paquete a menos que se excluyan.

- `exclude`: una matriz de paquetes o recursos que se excluirán del paquete.

```javascript
{
    name: 'bundles/catalog',
    create: true,
    include: [
        'addToWishlist',
        'priceBundle',
        'priceUtils',
        'priceOptions',
        'sticky',
        'productSummary',
        'slide'
    ],
    exclude: [
        'requirejs/require',
        'bundles/default',
        'mage/bootstrap'
    ],
}
```

Este ejemplo reutiliza los recursos `mage/bootstrap` y `requirejs/require`, lo que otorga mayor prioridad a los componentes más importantes que deben cargarse sincrónicamente. Los paquetes que están presentes son:

- `requirejs/require`: el único paquete cargado sincrónicamente
- `mage/bootstrap`: el paquete de arranque con componentes de interfaz de usuario
- `bundles/default`: paquete predeterminado necesario para todas las páginas
- `bundles/cart`: un paquete necesario para la página del carro de compras
- `bundles/shipping`: paquete común para el carro de compras y la página de cierre de compra (suponiendo que el cierre de compra nunca se abra directamente, la página de cierre de compra se cargará incluso más rápido si la página del carro de compras se abrió anteriormente y el paquete de envío ya se cargó).
- `bundles/checkout`: todo para el cierre de compra
- `bundles/catalog`: todo para páginas de productos y categorías

### Parte 2: Generación de paquetes

Los pasos siguientes describen el proceso básico para generar paquetes de [!DNL Commerce] más eficientes. Puede automatizar este proceso como desee, pero aún necesitará utilizar `nodejs` y `r.js` para generar los paquetes. Y si las temáticas tienen [!DNL JavaScript] personalizaciones relacionadas y no pueden reutilizar el mismo archivo de `build.js`, es posible que necesite crear varias `build.js` configuraciones por temática.

#### 1. Generar sitios de almacenamiento estáticos

Antes de generar paquetes, ejecute el comando de implementación estática:

```bash
php -f bin/magento setup:static-content:deploy -f -a frontend
```

Este comando genera implementaciones de almacén estáticas para cada tema y configuración regional que haya configurado. Por ejemplo, si utiliza la temática de Luma y una temática personalizada con configuraciones regionales en inglés y francés, generaría cuatro implementaciones estáticas:

- ...luma/en_US
- ...luma/fr_FR
- ...custom/en_US
- ...custom/fr_FR

Para generar paquetes para todas las temáticas y configuraciones regionales de la tienda, repita los pasos a continuación para cada temática y configuración regional de la tienda.

#### 2. Mueva el contenido del almacén estático a un directorio temporal

En primer lugar, debe mover el contenido estático del directorio de destino a algún directorio temporal porque RequireJS reemplaza todo el contenido del directorio de destino.

```bash
mv pub/static/frontend/Magento/{theme}/{locale} pub/static/frontend/Magento/{theme}/{locale}_tmp
```

Por ejemplo:

```bash
mv pub/static/frontend/Magento/luma/en_US pub/static/frontend/Magento/luma/en_US_tmp
```

#### 3. Ejecute el optimizador r.js

A continuación, ejecute el optimizador r.js en el archivo `build.js` desde el directorio raíz de [!DNL Commerce]. Las rutas a todos los directorios y archivos son relativas al directorio de trabajo.

```bash
r.js -o build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Este comando genera paquetes en un subdirectorio `bundles` del directorio de destino, lo que en este caso resulta en `pub/static/frontend/Magento/luma/en_US/bundles`.

La lista del contenido del nuevo directorio de paquetes puede tener este aspecto:

```bash
ll pub/static/frontend/Magento/luma/en_US/bundles
```

```terminal
total 1900
drwxr-xr-x  2 root root    4096 Mar 28 11:24 ./
drwxr-xr-x 70 root root    4096 Mar 28 11:24 ../
-rw-r--r--  1 root root  116417 Mar 28 11:24 cart.js
-rw-r--r--  1 root root  187090 Mar 28 11:24 catalog.js
-rw-r--r--  1 root root  307619 Mar 28 11:24 checkout.js
-rw-r--r--  1 root root 1240608 Mar 28 11:24 default.js
-rw-r--r--  1 root root   74233 Mar 28 11:24 shipping.js
```

#### 4. Configurar RequireJS para que utilice paquetes

Para que RequireJS use los paquetes, agregue una llamada de retorno `onModuleBundleComplete` después del nodo `modules` en el archivo `build.js`:

```javascript
[
    {
       //...
       exclude: [
           'requirejs/require',
           'bundles/default',
           'bundles/checkout',
           'bundles/cart',
           'bundles/shipping',
           'mage/bootstrap'
       ],
   },
],
bundlesConfigOutFile: `${config.dir}/requirejs-config.js`,
onModuleBundleComplete: function(data) {
    if (this.bundleConfigAppended) {
        return;
    }
    this.bundleConfigAppended = true;

    // bundlesConfigOutFile requires a simple require.config call in order to modify the configuration
    const bundleConfigPlaceholder = `
(function (require) {
require.config({});
})(require);
    `;

    fs.appendFileSync(this.bundlesConfigOutFile, bundleConfigPlaceholder);
}
```

#### 5. Vuelva a ejecutar el comando de implementación

Ejecute el siguiente comando para implementar:

```bash
r.js -o app/design/frontend/Magento/luma/build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Abra `requirejs-config.js` en el directorio `pub/static/frontend/Magento/luma/en_US` para comprobar que RequireJS anexó el archivo con llamadas de configuración de agrupamiento:

```javascript
require.config({
    bundles: {
        "bundles/default": ["mage/template", "mage/apply/scripts", "mage/apply/main", "mage/mage", "mage/translate", "mage/loader"],
        "bundles/cart": ["Magento_Ui/js/lib/validation/utils", "Magento_Ui/js/lib/validation/rules", "Magento_Ui/js/lib/validation/validation"]
    }
}
```

>[!NOTE]
>
>Al configurar paquetes, asegúrese de colocar las llamadas de `requirejs.config()` en el orden en que desea que se ejecuten, ya que las llamadas se ejecutan en el orden en que aparecen.

#### 6. Pruebe los resultados

Una vez que se carga la página, observe que el explorador carga diferentes dependencias y paquetes. Por ejemplo, estos son los resultados para el perfil &quot;3G lento&quot;:

![Dos veces más rápido](../assets/performance/images/TwiceAsFast.png)

El tiempo de carga de una página principal vacía ahora es dos veces más rápido que usar el paquete [!DNL Commerce] nativo. Pero podemos hacerlo aún mejor.

#### 7. Optimizar los paquetes

Aunque estén comprimidos en gzip, los [!DNL JavaScript] archivos siguen siendo grandes. Minimícelos con RequireJS, que usa uglifier para minificar [!DNL JavaScript] con buenos resultados.

Para habilitar el optimizador en el archivo `build.js`, agregue `uglify2` como valor para la propiedad de optimización en la parte superior del archivo `build.js`:

```javascript
({
    optimize: 'uglify2',
    inlineText: true
})
```

Los resultados pueden ser significativos:
![Tres veces más rápido](../assets/performance/images/ThreeTimesFaster.png)

Los tiempos de carga ahora son tres veces más rápidos que con el paquete [!DNL Commerce] nativo.
