---
title: Avanzadas [!DNL JavaScript] Agrupación
description: Obtenga información sobre cómo el agrupamiento de JavaScript puede reducir el tamaño y la frecuencia de las solicitudes del servidor.
source-git-commit: 09c4d0e09354230c8779b930f085d8c7c131b85b
workflow-type: tm+mt
source-wordcount: '2137'
ht-degree: 0%

---


# Avanzadas [!DNL JavaScript] agrupación

Agrupación [!DNL JavaScript] módulos para un mejor rendimiento se trata de reducir dos cosas:

1. Número de solicitudes del servidor.
1. El tamaño de esas solicitudes de servidor.

En una aplicación modular, el número de solicitudes de servidor puede alcanzar los cientos. Por ejemplo, la siguiente captura de pantalla muestra solo el inicio de la lista de [!DNL JavaScript] módulos cargados en la página de inicio de una instalación limpia.

![Sin agrupamiento](../assets/performance/images/noBundling.png)

## Combinación y agrupación

Fuera de la caja, [!DNL Commerce] proporciona dos maneras de reducir el número de solicitudes del servidor: combinación y agrupación. Estos ajustes están desactivados de forma predeterminada. Puede activarlos en la interfaz de usuario del administrador en **[!UICONTROL Stores]** > **Configuración** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL [!DNL JavaScript] Settings]** o desde la línea de comandos.

![Agrupación](../assets/performance/images/bundlingImage.png)

### Agrupamiento básico

Para habilitar el agrupamiento integrado desde la línea de comandos:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

Esto es nativo [!DNL Commerce] mecanismo que combina todos los recursos presentes en el sistema y los distribuye entre paquetes del mismo tamaño (bundle_0.js, bundle_1.js ... bundle_x.js):

![[!DNL Commerce] agrupación](../assets/performance/images/magentoBundling.png)

Mejor, pero el navegador sigue cargando TODO el [!DNL JavaScript] paquetes, no solo los necesarios.

[!DNL Commerce] el agrupamiento reduce el número de conexiones por página, pero para cada solicitud de página carga todos los paquetes, incluso cuando la página solicitada solo puede depender de archivos dentro de uno o dos de los paquetes. El rendimiento mejora después de que el explorador almacene en caché los paquetes. Sin embargo, como el explorador carga estos paquetes sincrónicamente, la primera visita del usuario a un [!DNL Commerce] la tienda podría tardar un rato en renderizar y dañar la experiencia del usuario.

### Combinación básica

Para habilitar la combinación integrada desde la línea de comandos:

```bash
php -f bin/magento config:set dev/js/merge_files 1
```

Este comando combina todos los sincrónicos [!DNL JavaScript] en un archivo. Habilitar la combinación sin habilitar también el agrupamiento no es útil porque [!DNL Commerce] utiliza RequireJS. Si no habilita el agrupamiento, [!DNL Commerce] solo combina RequireJS y su configuración. Al habilitar la agrupación y la combinación, [!DNL Commerce] crea un único [!DNL JavaScript] archivo:

![Fusión en el mundo real](../assets/performance/images/magentoMergingDevWorld.png)

## Tiempos de renderización del mundo real

Los tiempos de carga combinados y combinados anteriores parecen buenos en un entorno de desarrollo. Pero en el mundo real, muchas cosas pueden ralentizar la renderización: conexiones lentas, umbrales de conexión grandes, redes limitadas. Además, los dispositivos móviles no se procesan tan rápido como los equipos de escritorio.

Para probar y preparar su implementación de tienda para el mundo real, le recomendamos que pruebe con el perfil de regulación nativo de Chrome, &quot;Slow 3G&quot;. Con Slow 3G, nuestros tiempos de salida agrupados anteriores ahora reflejan las realidades de conexión de muchos usuarios:

![Agrupación en el mundo real](../assets/performance/images/magentoBundlingRealWorld.png)

Con una conectividad 3G lenta, se tardan unos 44 segundos en cargar todos los paquetes para la página principal de un [!DNL Commerce] instalación.

Lo mismo ocurre cuando se combinan los paquetes en un solo archivo. Los usuarios aún podrían esperar unos 42 segundos para la carga inicial de la página, como se muestra aquí:

![Fusión en el mundo real](../assets/performance/images/magentoMergingRealWorld.png)

Con un enfoque más avanzado para [!DNL JavaScript] agrupando, podemos mejorar estos tiempos de carga.

## Agrupación avanzada

Recuerde, el objetivo de [!DNL JavaScript] el agrupamiento es reducir el número y el tamaño de los recursos solicitados para cada página cargada en el explorador. Para ello, queremos crear nuestros paquetes para que cada página de nuestra tienda solo necesite descargar un paquete común y un paquete específico para cada página a la que se accede.

Una forma de conseguirlo es definir los paquetes por tipos de página. Puede clasificar [!DNL Commerce]Las páginas de en varios tipos de página, incluyendo Categoría, Producto, CMS, Cliente, Carro de compras y Cierre de compra. Cada página clasificada en uno de estos tipos de página tiene un conjunto diferente de dependencias del módulo RequireJS. Al empaquetar los módulos RequireJS por tipo de página, solo acabará con un puñado de paquetes que cubren las dependencias de cualquier página de la tienda.

Por ejemplo, puede terminar con un paquete para las dependencias comunes a todas las páginas, un paquete para páginas solo de CMS, un paquete para páginas solo de catálogo, otro paquete para páginas solo de búsqueda y un paquete para páginas de cierre de compra.

También puede crear paquetes por propósito: para funciones comunes, características relacionadas con productos, características de envío, características de cierre de compra, impuestos y validaciones de formularios. La forma de definir los paquetes depende de usted y de la estructura de su tienda. Puede que descubra que algunas estrategias de agrupamiento funcionarán mejor que otras.

Una limpieza [!DNL Commerce] la instalación permite alcanzar un buen rendimiento dividiendo los paquetes por tipos de página, pero algunas personalizaciones pueden requerir un análisis más profundo y otras distribuciones de recursos.

### Herramientas necesarias

Los pasos siguientes requieren la instalación de las siguientes herramientas, que están familiarizadas con ellas:

- [nodejs](https://nodejs.org/en/download/)
- [r.js](http://requirejs.org/docs/optimization.html#download)
- [[!DNL PhantomJS]](http://phantomjs.org/) (opcional)

### Código de muestra

Las versiones completas del código de muestra utilizado en este artículo están disponibles aquí:

- [build.js](../assets/performance/code-samples/build.js)
- [deps.js](../assets/performance/code-samples/deps.js)
- [deps-map.sh](../assets/performance/code-samples/deps-map.sh.txt)

### Parte 1: Crear una configuración de paquete

#### 1\. Añadir un archivo build.js

Cree un `build.js` en el [!DNL Commerce] directorio raíz. Este archivo contendrá la configuración de compilación completa para sus paquetes.

```javascript
({
    optimize: 'none',
    inlineText: true
})
```

Más tarde, cambiaremos el `optimize:` configurar desde_ `none` a `uglify2` para minimizar la salida del paquete. Pero por ahora, durante el desarrollo, se puede dejar configurado como `none` para garantizar compilaciones más rápidas.

#### 2\. Agregar dependencias, suplementos, rutas y asignación de RequireJS

Agregue los siguientes nodos de configuración de compilación de RequireJS, `deps`, `shim`, `paths`y `map`, al archivo de compilación:

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

#### 3\. Agregue los valores de instancia requeridos js-config.js

En este paso, tendrá que acumular todos los `deps`, `shim`, `paths`y `map` nodos de configuración de la tienda `requirejs-config.js` en los nodos correspondientes de su `build.js` archivo. Para ello, puede abrir el **[!UICONTROL Network]** en el panel Herramientas para desarrolladores del explorador y vaya a cualquier página de la tienda, como la página principal. En la pestaña Red , verá la instancia de la tienda del `requirejs-config.js` cerca de la parte superior, resaltado aquí:

![Configuración de RequireJS](../assets/performance/images/RequireJSConfig.png)

Dentro de este archivo, encontrará varias entradas para cada uno de los nodos de configuración (`deps`, `shim`, `paths`, `map`). Debe acumular estos valores de nodo múltiples en el nodo de configuración único del archivo build.js. Por ejemplo, si la tienda `requirejs-config.js` La instancia tiene entradas para 15 independientes `map` , tendrá que combinar las entradas de los 15 nodos en el único `map` en su `build.js` archivo. Lo mismo ocurre con el `deps`, `shim`y `paths` nodos. Sin un script para automatizar este proceso, puede tardar un tiempo.

Deberá cambiar la ruta `mage/requirejs/text` a `requirejs/text` en `paths` nodo de configuración como se indica a continuación:

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

Al final del `build.js` , agregue los módulos[] como marcador de posición para los paquetes que definirá para su tienda más adelante.

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

Puede recuperar todas las variables [!DNL RequireJS] dependencias de módulo de los tipos de página de su tienda mediante:

1. [!DNL PhantomJS] desde la línea de comandos (suponiendo que [!DNL PhantomJS] instalado).
1. RequireJS en la consola del explorador.

#### Para usar [!DNL PhantomJS]:

En el [!DNL Commerce] directorio raíz, cree un nuevo archivo llamado `deps.js` y copie en el código siguiente. Este código utiliza [!DNL [!DNL PhantomJS]] para abrir una página y esperar a que el explorador cargue todos los recursos de la página. Luego genera todas las [!DNL RequireJS] dependencias de una página determinada.

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

Abra un terminal dentro del [!DNL Commerce] directorio raíz y ejecute el script con cada página de la tienda que represente un tipo de página específico:

<pre>
phantomjs deps.js <i>url-to-specific-page</i> &gt; <i>text-file-representation-pagetype-dependencias</i>
</pre>

Por ejemplo, estas son cuatro páginas del almacén de muestras temático de Luma que representan los cuatro tipos de página que vamos a utilizar para crear nuestros cuatro paquetes (página principal, categoría, producto, carro de compras):

```terminal
phantomjs deps.js http://m2.loc/ > bundle/homepage.txt
phantomjs deps.js http://m2.loc/women/tops-women/jackets-women.html > bundle/category.txt
phantomjs deps.js http://m2.loc/beaumont-summit-kit.html > bundle/product.txt
phantomjs deps.js http://m2.loc/checkout/cart/?SID=m2tjdt7ipvep9g0h8pmsgie975 > bundle/cart.txt (prepare a shopping cart)
..............
```

#### Para usar la consola del explorador:

Si no desea usar [!DNL PhantomJS], puede ejecutar el siguiente comando desde la consola de su explorador mientras ve cada tipo de página en su tienda:

```shell
Object.keys(window.require.s.contexts._.defined)
```

Este comando (usado dentro de la variable [!DNL PhantomJS] script) crea la misma lista de [!DNL RequireJS] y las muestra en la consola del explorador. La desventaja de este enfoque es que tendrá que crear sus propios archivos de texto de tipo paquete/página.

#### 6\. Formato y filtro de la salida

Después de combinar el [!DNL RequireJS] dependencias en archivos de texto de tipo página, puede utilizar el siguiente comando en cada archivo de dependencia de tipo página para reemplazar las comas de los archivos con nuevas líneas:

```terminal
sed -i -e $'s/,/\\\n/g' bundle/category.txt
sed -i -e $'s/,/\\\n/g' bundle/homepage.txt
sed -i -e $'s/,/\\\n/g' bundle/product.txt
....
```

También debe eliminar todas las mezclas para cada archivo porque mezcla dependencias duplicadas. Utilice el siguiente comando en cada archivo de dependencia:

```terminal
sed -i -e 's/mixins\!.*$//g' bundle/homepage.txt
sed -i -e 's/mixins\!.*$//g' bundle/category.txt
sed -i -e 's/mixins\!.*$//g' bundle/product.txt
...
```

#### 7\. Identificar paquetes únicos y comunes

El objetivo es crear un paquete común de [!DNL JavaScript] archivos necesarios para todas las páginas. De este modo, el explorador solo necesita cargar el paquete común junto con uno o más tipos de página específicos.

Abra un terminal en el [!DNL Commerce] directorio raíz y utilice el siguiente comando para verificar que tiene dependencias que puede dividir en paquetes separados:

```bash
sort bundle/*.txt |uniq -c |sort -n
```

Este comando combina y ordena las dependencias que se encuentran en la variable `bundle/*.txt` archivos.  El resultado también muestra el número de archivos que contienen cada dependencia:

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

Este resultado muestra que `buildTools` es una dependencia solo en uno de los archivos bundle/*.txt. La variable `jquery/jquery.metadata` la dependencia está en dos (2) archivos y `es6-collections` está en tres (3) archivos.

Nuestro resultado muestra solo tres tipos de página (página de inicio, categoría y producto), que nos indica:

- Tres dependencias son únicas para un solo tipo de página (el número 1 lo muestra).
- Se producen tres dependencias más en dos tipos de página (indicadas por el número 2).
- Las tres últimas dependencias son comunes a los tres tipos de página (indicadas por el número 3).

Esto nos dice que es probable que podamos mejorar las velocidades de carga de página de nuestra tienda dividiendo nuestras dependencias en diferentes paquetes, una vez que sepamos qué tipos de página necesitan qué dependencias.

#### 8\. Creación de un archivo de distribución de dependencias

Para averiguar qué tipos de página necesitan qué dependencias, cree un nuevo archivo en la [!DNL Commerce] directorio raíz llamado `deps-map.sh` y copie en el siguiente código:

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

También puede encontrar la secuencia de comandos en [https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html](https://www.unix.com/shell-programming-and-scripting/140390-get-common-lines-multiple-files.html)

Abra un terminal en el [!DNL Commerce] directorio raíz y ejecute el archivo:

```bash
bash deps-map.sh
```

El resultado de esta secuencia de comandos, aplicado a los tres tipos de página de ejemplo, debería tener este aspecto (pero mucho más largo):

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

#### 9\. Crear paquetes en el archivo build.js

Abra el `build.js` archivo de configuración y agregue los paquetes a `modules` nodo . Cada paquete debe definir las siguientes propiedades:

- `name`— el nombre del paquete. Por ejemplo, un nombre de `bundles/cart` genera un `cart.js` paquete en un `bundles` subdirectorio.

- `create`— un indicador booleano para crear el paquete (valores: `true` o `false`).

- `include`— una matriz de activos (cadenas) incluidos como dependencias para la página. RequireJS rastrea todas las dependencias y las incluye en el paquete a menos que se excluya.

- `exclude`— una matriz de paquetes o recursos para excluir del paquete.

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

Este ejemplo se reutiliza `mage/bootstrap` y `requirejs/require` activos, dando mayor prioridad a los componentes y componentes más importantes que deben cargarse sincrónicamente. Los paquetes presentes son:

- `requirejs/require`: el único paquete cargado sincrónicamente
- `mage/bootstrap`: el paquete de arranque con componentes de interfaz de usuario.
- `bundles/default`: paquete predeterminado requerido para todas las páginas
- `bundles/cart`: un paquete necesario para la página del carro de compras
- `bundles/shipping`: paquete común para el carro de compras y la página de cierre de compra (suponiendo que el cierre de compra nunca se abre directamente, la página de cierre de compra se carga aún más rápido si la página del carro de compras se abrió anteriormente y el paquete de envío ya estaba cargado)
- `bundles/checkout`—todo para cierre de compra
- `bundles/catalog`: todo para páginas de productos y categorías

### Parte 2: Generar paquetes

Los pasos siguientes describen el proceso básico para generar más eficiencia [!DNL Commerce] paquetes. Puede automatizar este proceso de la forma que desee, pero aún tendrá que utilizar `nodejs` y `r.js` para generar sus paquetes. Y si sus temas tienen [!DNL JavaScript]personalizaciones relacionadas con y no pueden reutilizar lo mismo `build.js` , puede que necesite crear varias `build.js` configuraciones por tema.

#### 1. Generar sitios de tiendas estáticas

Antes de generar paquetes, ejecute el comando de implementación estático:

```bash
php -f bin/magento setup:static-content:deploy -f -a frontend
```

Este comando genera implementaciones estáticas de almacén para cada tema y configuración regional que haya configurado. Por ejemplo, si utiliza el tema de Luma y un tema personalizado con configuraciones regionales en inglés y francés, generaría cuatro implementaciones estáticas:

- ...luma/es_ES
- ...luma/fr_FR
- ...custom/en_US
- ...custom/fr_FR

Para generar paquetes para todos los temas y configuraciones regionales de la tienda, repita los pasos siguientes para cada tema y configuración regional de la tienda.

#### 2. Mover el contenido estático del almacén a un directorio temporal

En primer lugar, debe mover el contenido estático del directorio de destino a algún directorio temporal porque RequireJS reemplaza todo el contenido del directorio de destino.

```bash
mv pub/static/frontend/Magento/{theme}/{locale} pub/static/frontend/Magento/{theme}/{locale}_tmp
```

Por ejemplo:

```bash
mv pub/static/frontend/Magento/luma/en_US pub/static/frontend/Magento/luma/en_US_tmp
```

#### 3. Ejecute el optimizador r.js

A continuación, ejecute el optimizador r.js en la variable `build.js` del archivo [!DNL Commerce]del directorio raíz de . Las rutas a todos los directorios y archivos son relativas al directorio de trabajo.

```bash
r.js -o build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Este comando genera paquetes en un `bundles` subdirectorio del directorio de destino, que en este caso resulta en `pub/static/frontend/Magento/luma/en_US/bundles`.

El listado del contenido del nuevo directorio de paquetes puede tener este aspecto:

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

#### 4. Configure RequireJS para que utilice paquetes

Para que RequireJS use sus paquetes, agregue un `onModuleBundleComplete` devolución de llamada después de `modules` en el `build.js` archivo:

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

#### 5. Volver a ejecutar el comando implementar

Ejecute el siguiente comando para implementar:

```bash
r.js -o app/design/frontend/Magento/luma/build.js baseUrl=pub/static/frontend/Magento/luma/en_US_tmp dir=pub/static/frontend/Magento/luma/en_US
```

Apertura `requirejs-config.js` en el `pub/static/frontend/Magento/luma/en_US` para comprobar que RequireJS anexó el archivo con llamadas de configuración de agrupamiento:

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
>Al configurar paquetes, asegúrese de colocar la variable `requirejs.config()` llamadas en el orden en que desee que se ejecuten, ya que las llamadas se ejecutan en el orden en que aparecen.

#### 6. Probar los resultados

Después de cargar la página, observe que el explorador carga diferentes dependencias y paquetes. Por ejemplo, estos son los resultados del perfil &quot;3G lento&quot;:

![Dos veces más rápido](../assets/performance/images/TwiceAsFast.png)

El tiempo de carga de la página para una página principal vacía ahora es el doble de rápido que el uso de nativa [!DNL Commerce] paquete. Pero podemos hacerlo aún mejor.

#### 7. Optimizar los paquetes

Aunque esté comprimido, el [!DNL JavaScript] los archivos siguen siendo grandes. Minimizarlos con RequireJS, que usa un simulador para minimizar [!DNL JavaScript] a buen resultado.

Para habilitar el optimizador en su `build.js` archivo, agregar `uglify2` como el valor de la propiedad optimize en la parte superior del `build.js` archivo:

```javascript
({
    optimize: 'uglify2',
    inlineText: true
})
```

Los resultados pueden ser significativos:
![Tres veces más rápido](../assets/performance/images/ThreeTimesFaster.png)

Ahora, los tiempos de carga son tres veces más rápidos que con los valores nativos [!DNL Commerce] paquete.
