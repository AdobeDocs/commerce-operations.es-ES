---
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '6363'
ht-degree: 0%

---
# Glosario de Adobe Commerce

## A

### sobre el pliegue

_adjetivo_

En una ventana del explorador, el contenido que es visible inmediatamente después de cargar una página web y antes de que un usuario se desplace hacia abajo por la página.
Al diseñar el diseño, utilice formatos flexibles para mostrar de la mejor manera los productos, las funciones, las ventas, las notificaciones, las opciones, etc. de mayor prioridad en esta área.

En móviles y tabletas, el área de sobre el pliegue difiere considerablemente, especialmente en el tamaño y las dimensiones de la pantalla y la orientación al ver (vertical u horizontal).
El uso de temáticas interactivas y pruebas puede ayudar a encontrar la combinación adecuada de contenido y diseño.

_Atributos de término:_

* _Campo: diseño_

### rama activa

_sustantivo_

Una rama o entorno activo es aquel que está conectado a una instancia implementada o en ejecución con acceso a servicios.
Cuando se desactiva, se elimina la conexión con los servicios y con la instancia en ejecución, pero se conserva el código.
Se convierte en una rama de Git normal.

_Atributos de término:_

* _Campo: nube_

### adaptador

_sustantivo_

Una clase que permite que dos sistemas incompatibles funcionen juntos sin modificar el código fuente del sistema.
Algunos ejemplos son adaptadores de base de datos, adaptadores de caché, adaptadores del sistema de archivos, adaptadores de bibliotecas de postprocesador y otros tipos de adaptadores informáticos.

_Atributos de término:_

* _Campo: programación_

### administrador

_sustantivo_

En el software, una función de usuario con privilegios de administrador completos para administrar todas las funcionalidades.
En Adobe Commerce, los usuarios administradores tienen permisos y acceso completos a todas las funciones, opciones y funcionalidades de la variable Administración.
También pueden crear usuarios y funciones.

Más información: [Agregando usuarios](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html)

_Atributos de término:_

* _Campo: software de comercio_
* _Sinónimos: administrador, superusuario_
* _Términos relacionados: administración de comercio_

### Área de administración

_sustantivo_

El back office protegido por contraseña de su tienda donde se administran los pedidos, el catálogo, el contenido y las configuraciones.
Los usuarios acceden al área de Administración para administrar la tienda, incluidos productos, pedidos, envíos, contenido de CMS, diseño de la tienda, información del cliente, etc.
Los usuarios administradores tienen una función asociada con permisos que controlan el acceso a las funciones, opciones y funcionalidades.

Más información: [Guía del usuario de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Atributos de término:_

* _Campo: software de comercio_
* _Sinónimos: Administrador, Panel de administración, servidor, Interfaz de administración, IU de administración_
* _Términos relacionados: admin_

### Variables de ADMINISTRACIÓN

_sustantivo_

Las variables ADMIN son variables de entorno de proyecto para anular los ajustes de configuración de la cuenta de usuario Administrador para acceder a la IU de Administración.

Más información: [Variables de administrador](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html)

_Atributos de término:_

* _Campo: admin, cloud_

### adminhtml

_sustantivo_

El nombre de área interna asignado al administrador.

Más información: [Guía del usuario de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: área, administración de comercio_

### área

_sustantivo_

Área es un término abstracto para un ámbito de aplicación Magento.
Las áreas son componentes lógicos que organizan el código para un procesamiento de solicitudes optimizado.
Las áreas reducen la demanda de memoria de los objetos de configuración a los que se accede desde la tienda y optimizan las llamadas al servicio web al cargar únicamente el código dependiente requerido.
Cada área puede contener un código completamente diferente para procesar direcciones URL y solicitudes.

Las áreas de Adobe Commerce incluyen:

* Administrador (adminhtml)
* Tienda
* REST de API web (webapi_rest)

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: componente de comercio, tienda_

### atributo

_sustantivo_

Característica o propiedad de un producto que describe algún aspecto del producto.
Los usuarios de Adobe Commerce pueden crear atributos personalizados para agregarlos al conjunto de atributos predeterminado o a un conjunto de atributos personalizado.
Cree estos atributos mediante el administrador o mediante programación.
Ejemplos: color, tamaño, peso, precio, edad, sexo, etc.

Los atributos personalizados son un tipo de atributo Entity-Attribute-Value (EAV).

Para integraciones como el canal de anuncios de compra de Google y la Sales Channel de Amazon, los atributos de Commerce se asignan a atributos de terceros para mostrar y vender correctamente productos y anuncios de visualización.

Más información: [EAV y extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Sinónimos: atributo de producto, atributo personalizado_
* _Términos relacionados: atributo de extensión_

### grupo de atributos

_sustantivo_

Agrupación lógica de atributos dentro de un conjunto de atributos.

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: attribute_

### conjunto de atributos

_sustantivo_

Colección de grupos de atributos, personalizados para un producto específico.
Ejemplo: un conjunto de atributos de camiseta puede incluir color, tamaño, sexo y marca.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: attribute_

### coste de inventario promedio

_sustantivo_

Precio del producto, menos cupones o descuentos, más flete e impuestos aplicables.
El promedio se determina sumando el costo inicial de inventario cada mes, más el costo final de inventario para el último mes del período.

_Atributos de término:_

* _Campo: producto, precios, inventario_

## B

### divisa base

_sustantivo_

La divisa principal que se utiliza por vista de tienda para todos los pagos en línea.
Las tiendas pueden aceptar divisas de más de 200 países de todo el mundo.
La tienda proporciona un selector de moneda para varias monedas aceptadas en un país o configuración regional específicos.
Los símbolos de moneda aparecen en los precios de los productos y en los documentos de venta, como pedidos y facturas.
Puede personalizar los símbolos de moneda según sea necesario y establecer la visualización del precio por separado para cada tienda o vista.

Más información: [Moneda](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency.html)

_Atributos de término:_

* _Campo: precios_

### procesamiento por lotes

_sustantivo_

Para realizar una tarea o cambiar varios artículos a la vez, sin repetición manual.

_Atributos de término:_

* _Campo: programación_
* _Sinónimos: operaciones masivas_

### bloquear

_sustantivo_

Una unidad de salida de página que procesa contenido distintivo (un fragmento de información, un elemento de interfaz de usuario) o cualquier cosa visualmente tangible para el usuario final.
Los módulos implementaron [bloques](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) y los proporcionaron.
Los bloques utilizan plantillas para generar HTML.
Algunos ejemplos de bloques son una lista de categorías, un minicarrito, etiquetas de productos y una lista de productos.

[Los bloques dinámicos](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/dynamic-blocks/dynamic-blocks.html) proporcionan contenido basado en lógica, como reglas de precios.

Page Builder amplía la interactividad y la creación de [bloques](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/block.html) y [bloques dinámicos](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/dynamic-block.html).

_Atributos de término:_

* _Campo: software de comercio_
* _Sinónimos: Bloques Dinámicos_
* _Términos relacionados: bloque cms, bloque estático, contenedor, diseño_

### marca

_sustantivo, verbo_

Identidad única que define un producto o grupo de productos determinado por el fabricante o Designer.
Estas incluyen marcas de nombre para ropa, electrodomésticos, artículos de lujo, etc.
Su empresa también puede ser la marca, que vende productos con varias marcas en función de la unidad de negocio, la audiencia objetivo, etc.

Utilice atributos personalizados para guardar la información de marca de los productos.

Algunas extensiones e integraciones pueden utilizar o requerir una marca para sus productos, como Google Shopping ads Channel y Amazon Sales Channel.

_Atributos de término:_

* _Campo: empresarial_

### de ladrillo y mortero

_adjetivo_

Un negocio minorista con una ubicación física permanente, a diferencia de los negocios que funcionan de forma virtual o exclusiva a través de Internet.

Para [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) y [Order Management](https://omsdocs.magento.com/getting-started/terminology/), esta tienda es una fuente para rastrear cantidades de productos, enviar pedidos y admitir la recogida en la tienda.

_Atributos de término:_

* _Campo: empresa, inventario_

### operaciones por lotes

_sustantivo_

Las operaciones por lotes son acciones que se realizan a gran escala.
Algunas tareas de operaciones por lotes incluyen la importación o exportación de artículos, el cambio de precios a escala masiva y la asignación de productos a un almacén.

Más información: [Operaciones masivas de DevDocs](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

_Atributos de término:_

* _Campo: programación_

### paquete de producto

_sustantivo_

Permite a los clientes ensamblar un producto personalizable &quot;crear el suyo propio&quot; a partir de diversas opciones y configuraciones.
Cada elemento del paquete es un producto simple o virtual independiente.

Más información: [Productos configurables](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: producto simple, producto virtual, tipos de producto_

### extensión agrupada

_sustantivo_

El código que amplía o personaliza el comportamiento de Adobe Commerce se considera una extensión agrupada.
Puede incluir módulos, temáticas y paquetes de idiomas.

_Atributos de término:_

* _Campo: extensión agrupada, extensión_
* _Sinónimos: extension_
* _Términos relacionados: extensión, extensión agrupada por proveedor_

## C

### servidor de caché

_sustantivo_

Almacena registros de caché en un sistema backend de dos niveles dentro del marco predeterminado de Zend.
Una caché de primer nivel es rápida (por ejemplo, un servidor APC o Memcached), pero es limitada y no admite el etiquetado y la agrupación de entradas de caché.
Una caché de segundo nivel (por ejemplo, un sistema de archivos o un backend de Redis) es más lenta, pero admite etiquetado y agrupación.

_Atributos de término:_

* _Campo: programación_
* _Términos relacionados: backend_

### front-end de caché

_sustantivo_

Especifica qué tipo de datos se almacenan en el servidor de caché.

_Atributos de término:_

* _Campo: programación_
* _Términos relacionados: frontend_

### tipo de caché

_sustantivo_

Una caché almacena datos para que las llamadas futuras a dichos datos se carguen más rápido.

Adobe Commerce incluye estos tipos:
* Configuración
* Diseños
* Bloquear salida del HTML
* Datos de colecciones
* Datos de reflexión
* Operaciones DDL de base de datos
* Configuración compilada
* Tipos y atributos de EAV
* Notificación al cliente
* Configuración de integraciones
* Configuración de API de integraciones
* Caché de páginas (la más conocida)
* Configuración de servicios web
* Traducciones
* Regla de destino
* Caché de producto de Google
* Vértice

Se pueden crear y definir otros tipos.

_Atributos de término:_

* _Campo: programación_

### captar

_verbo_

Proceso de conversión de un importe de pedido autorizado en una transacción facturable.
Las transacciones no se pueden capturar hasta que se autorice, y las autorizaciones no se pueden capturar hasta que se hayan enviado los productos o servicios.

_Atributos de término:_

* _Campo: empresarial_
* _Términos relacionados: autorización, estado del pedido_

### titular de la tarjeta

_sustantivo_

Una persona autorizada por una institución financiera para realizar compras en una cuenta de tarjeta de crédito.

_Atributos de término:_

* _Campo: negocio, pedido_

### reglas de carrito

_sustantivo_

Las reglas de precios que se aplican al carro de compras y que almacenan en déclencheur una acción en respuesta a un conjunto de condiciones.
Se utiliza para crear promociones.

_Atributos de término:_

* _Campo: software de comercio, precios, producto_
* _Términos relacionados: reglas de catálogo, carro de compras_

### catalogar

_sustantivo_

Para los comerciantes, el catálogo representa su inventario de productos.
Dentro de la arquitectura de Adobe Commerce, el catálogo consta de categorías, productos y atributos de productos.

Cada tienda Commerce tiene un solo catálogo de productos, que comparten todas las vistas de la tienda.
En una instalación de varias tiendas, cada tienda puede tener un catálogo independiente o compartirlo.
El catálogo de tiendas actual está determinado por la categoría raíz predeterminada, visible para el usuario en la barra de navegación superior (menú principal) de la tienda.
(El término &quot;categoría raíz&quot; puede resultar confuso, ya que la &quot;categoría raíz&quot; no es en realidad una categoría, sino un contenedor del menú, que consta de categorías y subcategorías.)

Puede crear tantas categorías raíz como desee, pero solo se puede utilizar una (la predeterminada) a la vez.

_Atributos de término:_

* _Campo: software de comercio, precios, producto_
* _Términos relacionados: catálogo compartido, regla de catálogo_

### reglas de catálogo

_sustantivo_

Reglas de precios que se aplican a productos específicos y que déclencheur una acción en respuesta a un conjunto de condiciones.
Se utiliza para crear promociones.

_Atributos de término:_

* _Campo: software de comercio, precios, producto_
* _Términos relacionados: reglas del carro de compras, catálogo_

### categoría

_sustantivo_

Un grupo de productos que tienen algo en común.
El menú principal de la tienda está organizado en categorías y subcategorías de productos.

_Atributos de término:_

* _Campo: software de comercio, producto_

### pago y envío

_sustantivo_

Proceso de recopilar la información de pago y envío necesaria para completar la compra de artículos en el carro de compras.
Una vez que el cliente revisa la información y envía el pedido, se le envía una confirmación por correo electrónico.

La desprotección tiene muchas opciones y configuraciones listas para usar y mediante extensión.

Más información: [Tutorial de cierre de compra](https://developer.adobe.com/commerce/php/tutorials/frontend/custom-checkout/)

_Atributos de término:_

* _Campo: empresa, diseño, pedido, producto, programación_

### variables de nube

_sustantivo_

Las variables de nube son variables de entorno específicas de Adobe Commerce en la infraestructura de la nube y utilizan el prefijo **`MAGENTO_CLOUD`**.

Más información: [Variables de nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html)

_Atributos de término:_

* _Campo: nube_

### Bloque CMS

_sustantivo_

Una variante especial de [block](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) que solamente se puede crear en el administrador y no se puede hacer referencia a ella a través de archivos de diseño.

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: block, static block_

### datos complejos

_sustantivo_

Datos asociados con varias opciones de producto.

_Atributos de término:_

* _Campo: programación_

### componente

_sustantivo_

Se utiliza para hacer referencia a un módulo, tema o paquete de idioma en Adobe Commerce.

_Atributos de término:_

* _Campo: software de comercio_
* _Sinónimos: componente_
* _Términos relacionados: componente de interfaz de usuario_

### producto configurable

_sustantivo_

Un producto configurable parece un único producto con listas desplegables de opciones para cada variación.
Cada opción es en realidad un producto simple independiente con un SKU único, lo que permite rastrear el inventario para cada variación de producto.
Para lograr un efecto similar, se puede utilizar un producto simple con opciones personalizadas, pero sin la capacidad de realizar un seguimiento del inventario para cada variación.
Los productos con varias opciones a veces se denominan productos compuestos.

Aunque un producto configurable utiliza más SKU y puede tardar un poco más en configurarse al principio, puede ahorrarle tiempo al final.
Si planea hacer crecer su negocio, el tipo de producto configurable podría ser una mejor opción para un producto con varias opciones.

Ejemplo: camisetas disponibles en dos colores y tres tallas.
Se deben crear seis variantes como productos individuales (cada una con su propio SKU).
A continuación, todas las variantes se añaden a un producto configurable en el que los clientes pueden elegir el tamaño y el color y, a continuación, agregarlo al carro de compras.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: tipos de productos_

### tasa de conversión

_sustantivo_

El porcentaje de visitantes que se convierten en compradores.

_Atributos de término:_

* _Campo: negocio, pedido_

### escalado de nivel principal

_sustantivo_

La escala del nivel principal consta de tres nodos de servicio para el almacenamiento de datos, la caché y los servicios, como OpenSearch, Elasticsearch, MariaDB y Redis.

_Atributos de término:_

* _Campo: nube_

### nota de crédito

_sustantivo_

Documento emitido por el comerciante a un cliente para eliminar un saldo pendiente debido a cargos excesivos, devoluciones o devolución de mercancías.
La nota restaura los fondos en la cuenta del cliente.

_Atributos de término:_

* _Campo: negocio, pedido_

### comentario de nota de crédito

_sustantivo_

Detalles de por qué se abonó un importe de nota de abono al cliente.

_Atributos de término:_

* _Campo: negocio, pedido_

### elemento de nota de crédito

_sustantivo_

Artículo facturado para el que un comerciante crea una nota de abono.

_Atributos de término:_

* _Campo: negocio, pedido_

### realizar venta cruzada

_sustantivo, adjetivo, verbo_

Producto que aparece junto al carro de compras.
Cuando un cliente navega a la página del carro de compras, estos productos se muestran como ventas cruzadas de los artículos que ya están en el carro de compras.
Son similares a las compras por impulso, como las revistas y los dulces en las cajas registradoras de las tiendas de comestibles.

_Atributos de término:_

* _Campo: empresa, producto_
* _Términos relacionados: ampliar ventas_

### CVM

_sustantivo_

Una abreviatura de &quot;Método de verificación del titular de la tarjeta&quot;.
Una forma de verificar la identidad del cliente confirmando un código de seguridad de tarjeta de crédito de 3 o 4 dígitos con el procesador de pagos.

_Atributos de término:_

* _Campo: negocio, pedido_
* _Sinónimos: método de verificación del titular de la tarjeta_
* _Términos relacionados: código de seguridad_

## D

### esquema base datos

_sustantivo_

Estructura de los datos de una base de datos.
Define cómo se organizan los datos y cómo se rigen las relaciones de datos, incluidas todas las restricciones aplicadas a los datos.
Un módulo puede contener fragmentos del esquema de la base de datos si ese módulo tiene datos que deben almacenarse en la base de datos.

_Atributos de término:_

* _Campo: programación_
* _Sinónimos: schema_

### inyección de dependencia

_sustantivo_

Patrón de diseño de software que permite a una clase especificar sus dependencias sin tener que construirlas.
Esta clase delega la responsabilidad de insertar la dependencia en la clase que realiza la llamada.
Se utiliza para facilitar las pruebas.
Para definir dependencias para clases, edite el archivo de configuración di.xml.

_Atributos de término:_

* _Campo: programación_

### clave de implementación

_sustantivo_

Una clave de implementación es la clave pública SSH del proyecto y habilita el acceso de solo lectura o de lectura-escritura (si está habilitado) a un repositorio Git.

Más información: [Conexiones seguras](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)

_Atributos de término:_

* _Campo: nube_

### inclusión doble

_sustantivo, verbo_

Proceso de verificación por correo electrónico que requiere que los suscriptores potenciales completen un segundo paso que confirme su intención de suscribirse.

_Atributos de término:_

* _Campo: empresarial_

### producto descargable

_sustantivo_

Producto descargable digitalmente que consta de uno o más archivos descargados, como un libro electrónico, música, vídeo, aplicación de software o una actualización.
Puedes ofrecer un álbum a la venta y vender cada canción individualmente.
Un producto descargable puede entregar una versión electrónica del catálogo de productos.

Los archivos descargables pueden residir en el servidor o proporcionarse como direcciones URL a cualquier otro servidor o red de distribución de contenido.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: tipos de productos_

### contenido dinámico

_sustantivo_

Contenido que se genera mediante código en lugar de leerse desde una plantilla estática.
Después de que el contenido dinámico se represente inicialmente cuando un usuario visita una página, a veces el contenido se puede almacenar en caché y reutilizar sin requerir otra llamada dinámica tras una visita.

_Atributos de término:_

* _Campo: diseño_
* _Términos relacionados: php_

### URL de dynamic media

_sustantivo_

Una dirección URL que el sistema genera dinámicamente para hacer referencia a una imagen u otro medio.
La dirección se vincula directamente a los recursos almacenados en un servidor o en una red de entrega de contenido.
Para utilizar una dirección URL estática, cambie el valor de configuración.
Sin embargo, si se incluyen direcciones URL de medios dinámicos en el catálogo al deshabilitar la configuración, cada referencia del catálogo se convierte en un vínculo roto.
Los vínculos se pueden restaurar volviendo a habilitar las direcciones URL de medios dinámicos.
El uso de direcciones URL de medios dinámicos puede afectar al rendimiento de la búsqueda en el catálogo.

Formato de código: media url=&quot;path/to/image.jpg&quot;

_Atributos de término:_

* _Campo: programación_
* _Términos relacionados: red de distribución de contenido, url_

## E

### paquete ece-tools

_sustantivo_

Conjunto de scripts y herramientas diseñados para administrar e implementar la aplicación de Commerce. Este paquete simplifica muchos procesos de infraestructura en la nube de Adobe Commerce, incluida la implementación en un entorno Docker, la administración de crons, la verificación de la configuración del proyecto y la aplicación de parches de Adobe.

Más información: [paquete ece-tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)

_Atributos de término:_

* _Campo: cli, cloud, deploy_

### entidad

_sustantivo_

Una unidad u objeto único en programación.
Contiene atributos o parámetros que se pueden modificar.
Algunos ejemplos son el ensayo (en el que una actualización puede cambiar entidades como reglas de precios, productos o categorías) y los registros de base de datos (en el que los contratos de servicio incluyen estructuras de datos que se envían y reciben).

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: atributo, reglas del carro de compras, reglas del catálogo_

### valor de atributo de entidad

_sustantivo_

Para entidades de base de datos, un modelo de datos que codifica entidades de forma eficaz.
Almacena el ID de entidad, el nombre de atributo y el valor como un triple, lo que permite crear nuevos nombres de atributo de entidad en cualquier momento.
En la codificación, el número de atributos que se pueden utilizar para describir entidades se puede escalar ampliamente, pero el número que se aplica a una entidad determinada se minimiza.
Este modelo de datos es flexible, pero puede ser lento.

Más información: [EAV y extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Atributos de término:_

* _Campo: programación_
* _Sinónimos: eav_

### contenido permanente

_sustantivo_

Contenido que tiene una larga vida útil o contenido que se puede reutilizar.

_Atributos de término:_

* _Campo: empresarial_

### extensión

_sustantivo_

Código que amplía o personaliza el comportamiento de Adobe Commerce.
Si lo desea, puede empaquetar y distribuir una extensión en Commerce Marketplace u otro sistema de distribución de extensiones.
Una extensión de Commerce puede incluir módulos, temáticas y paquetes de idiomas.

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: componente, módulo, paquete_

### atributo de extensión

_sustantivo_

Amplíe la funcionalidad y, a menudo, utilice tipos de datos más complejos que los atributos personalizados. Estos atributos no aparecen en la GUI.

Más información: [Agregando atributos de extensión a la entidad](https://developer.adobe.com/commerce/php/development/components/add-attributes/)

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: attribute, entity attribute value_

## F

### flete a bordo

_sustantivo_

En el transporte marítimo internacional, este término significa que la parte receptora es responsable de los gastos de envío.
FOB puede basarse en el lugar de origen o de destino, y designarse como flete cobrado o flete pagado por adelantado.

_Atributos de término:_

* _Campo: negocio, pedido, precios_
* _Sinónimos: fob_

### frontend

_adjetivo_

En una aplicación cliente-servidor, están el back-end y el front-end.
El componente de front-end, o cliente, es una interfaz que permite a los usuarios manipular o interactuar con el código de back-end subyacente.
El código back-end se ejecuta en un servidor.
Un usuario no puede acceder directamente al código back-end.
Un usuario interactúa con la tienda, que a su vez utiliza el código que se ejecuta en el servidor de Commerce.

Nota: En el pasado, la tienda se conocía como &quot;front-end&quot; y el administrador como &quot;back-end&quot;. Ya no se admite este uso.

_Atributos de término:_

* _Campo: diseño, programación_
* _Sinónimos: lado del cliente_
* _Términos relacionados: backend, storefront, cache frontend_

### propiedades de front-end

_sustantivo_

Propiedades que determinan la presentación y el comportamiento de un atributo desde el punto de vista del cliente en su tienda.

_Atributos de término:_

* _Campo: diseño, programación_

### cumplimiento

_sustantivo_

Proceso de gestión de envíos de clientes.

_Atributos de término:_

* _Campo: empresarial_

## G

### tarjeta regalo

_sustantivo_

Tarjeta prepagada o certificado de regalo que se puede usar para hacer compras en la tienda.
A cada tarjeta regalo se le asigna un código único que se introduce en el momento del pago y envío.
El valor de la tarjeta regalo se refleja en el saldo de la cuenta de la tarjeta regalo.
Existen tres tipos de tarjetas de regalo:

* Las tarjetas de regalo &quot;físicas&quot; pueden ser producidas a partir de plástico o cartulina, enviadas al cliente.
* Las tarjetas de regalo &quot;virtuales&quot; se envían por correo electrónico.
* Las tarjetas regalo &quot;combinadas&quot; son una combinación de las dos, enviadas al destinatario como una tarjeta física y también entregadas por correo electrónico.
Se pueden configurar las tarjetas de regalo, incluidas las opciones para la idoneidad del producto y la selección de importes abiertos o fijos.

El administrador de la tienda también puede canjear una tarjeta regalo a petición del cliente cuando el pedido se crea en el backend.

Las tarjetas regalo también ayudan a las promociones, ya que los administradores de tiendas pueden crear manualmente las cuentas de tarjetas regalo en el backend y enviar los códigos de tarjetas regalo al segmento de clientes específico.
Las tarjetas regalo pueden servir como un programa de fidelización dirigido a los clientes más activos que realizan numerosas compras en la tienda web o una campaña promocional específica durante las vacaciones.

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: tipos de productos_

### margen bruto

_sustantivo_

La diferencia entre el coste y el precio de un producto.

_Atributos de término:_

* _Campo: empresarial_

### producto agrupado

_sustantivo_

Un tipo de producto con varios productos independientes similares agrupados en una sola página.
Se puede ofrecer con variaciones de un solo producto o agrupándolas por temporada o tema para crear un conjunto coordinado.
Cada producto se puede comprar por separado o como parte del grupo.

Por ejemplo, para un cuchillo disponible en cuatro tamaños, los cuatro cuchillos se pueden mostrar dentro de una página de producto agrupada.
Los clientes pueden seleccionar los tamaños que deseen y añadirlos al carro de compras desde esta página.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: producto simple, tipos de producto_

## H

### manipular

_sustantivo_

Por lo general, un controlador es una forma de hacer referencia a un objeto.
En Adobe Commerce, los controladores se utilizan en muchos lugares, generalmente para identificar una página.
Para los identificadores de página, el nombre del identificador se deriva de la dirección URL y se utiliza para localizar y cargar los archivos de diseño de la página a la que se hace referencia.
Por ejemplo, en el módulo Cliente, hay un archivo de diseño llamado &quot;view/frontend/layout/checkout_cart_index.xml&quot;.
Aquí &quot;frontend&quot; es el nombre del área y &quot;checkout_cart_index&quot; es el nombre del identificador, ambos derivados de la dirección URL.

_Atributos de término:_

* _Campo: programación_
* _Sinónimos: identificador de página_

### escala horizontal

_sustantivo_

El escalado horizontal (también conocido como escalado horizontal) es el proceso de añadir nodos o máquinas adicionales a su infraestructura para satisfacer la creciente demanda.

_Atributos de término:_

* _Campo: nube_

## I

### interceptación

_sustantivo_

Proceso de insertar código nuevo antes, después o alrededor de una función pública existente de una clase PHP.

Para interceptar una función, un complemento implementa el código adicional que se va a invocar.
Los complementos están asociados a puntos de interceptación mediante el archivo de configuración de inyección de dependencias (di.xml).
Si se definen varios complementos en la misma función, la configuración de inyección de dependencia define el orden en que se invocan los complementos, lo que permite utilizar varios complementos sin conflictos.

_Atributos de término:_

* _Campo: programación_
* _Términos relacionados: plug-in_

## L

### layout

_sustantivo_

En la construcción de una página de Commerce, un diseño es una serie de bloques reunidos en una jerarquía que representa la estructura de la página.

Los archivos de diseño de página se centran en el nivel más alto de estructura de la página (encabezado, pie de página, área de contenido principal, barra lateral izquierda, etc.).
A continuación, los archivos de diseño combinan contenido (bloques) en estas diferentes áreas de la página.

_Atributos de término:_

* _Campo: diseño, software de comercio_
* _Términos relacionados: instrucciones de diseño, bloque_

### instrucciones de diseño

_sustantivo_

Marcado en un archivo de diseño que describe los cambios que se aplicarán a un árbol de elementos estructurados de bloques, contenedores y componentes de la interfaz de usuario.
Un solo archivo de diseño puede contener varias instrucciones de diseño.
Las instrucciones de diseño se codifican en XML en los archivos de diseño.

_Atributos de término:_

* _Campo: diseño, programación_
* _Términos relacionados: layout, block, container, ui component_

### actualización del diseño

_sustantivo_

Se utiliza para fragmentos de código que se agregan para modificar el diseño XML o para importar las instrucciones de diseño desde otro archivo.

_Atributos de término:_

* _Campo: diseño, software de comercio_

### Propietario de licencia

_sustantivo_

El propietario de la licencia (también conocido como propietario de la cuenta) es la persona designada en una organización empresarial que administra pagos y otros problemas relacionados con la empresa para la cuenta de Adobe Commerce en la infraestructura de la nube.
Esta persona sirve como punto de contacto con el Adobe.
Después de que una empresa adquiera una suscripción a Adobe Commerce en la infraestructura en la nube, el acceso inicial al proyecto y al código solo estará disponible para la persona designada como Propietario de la licencia.

_Atributos de término:_

* _Campo: empresarial_

## M

### MAGEID

_sustantivo_

MAGEID suele ser el contacto de facturación de la cuenta de Adobe Commerce (y puede no ser el propietario del proyecto del proyecto de Adobe Commerce en la nube).
Para acceder a los derechos de Adobe Commerce y Adobe Commerce en paquetes de infraestructura en la nube, debe utilizar las claves de acceso asociadas con un MAGEID al que se haya concedido acceso a esos paquetes.

Más información: [Obtener las claves de autenticación](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html)

_Atributos de término:_

* _Campo: software de comercio_

### marcado

_sustantivo_

En marketing y venta minorista, un porcentaje añadido al coste de un artículo para determinar el precio de venta minorista.
[Configurar el marcado](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/settings/settings-advanced-custom-options.html), o markdown, de un producto a través de opciones personalizables de producto.

En el desarrollo, lenguaje informático que controla el procesamiento, la presentación y el formato del texto.
Además, las etiquetas de marcado son fragmentos de código que agregan funcionalidad o contenido a una página o bloque CMS.

_Atributos de término:_

* _Campo: empresa, programación_
* _Sinónimos: Markdown_

### entorno principal

_sustantivo_

En Adobe Commerce, en la infraestructura en la nube, los proyectos Pro utilizan un entorno activo de Platform as a Service (PaaS) denominado principal que incluye una copia de la base de datos del entorno de producción y del servidor web.

_Atributos de término:_

* _Campo: nube_

### cuenta comercial

_sustantivo_

Cuenta con un banco o institución financiera que permite aceptar transacciones con tarjeta de crédito.

_Atributos de término:_

* _Campo: empresarial_

### MFTF

_sustantivo_

MFTF es un [Marco de prueba funcional](https://developer.adobe.com/commerce/testing/functional-testing-framework/).
Proporciona un marco de pruebas para desarrolladores e ingenieros de software de Commerce, como especialistas en control de calidad, desarrolladores de PHP e integradores de sistemas.
Los desarrolladores y el control de calidad pueden escribir pruebas para intentar las interacciones del usuario con aplicaciones web, verificar la funcionalidad y automatizar las pruebas de regresión.

_Atributos de término:_

* _Campo: software de comercio, programación_
* _Términos relacionados: bloque cms, bloque estático, contenedor, diseño_

### módulo

_sustantivo_

Código que cambia o amplía las características proporcionadas por la aplicación Magento.
Un módulo está contenido en una estructura de directorio que contiene archivos PHP y XML (configuración, bloques, controladores, ayudantes, modelos, etc.) relacionados con una funcionalidad específica para ofrecer una colección distinta de características de producto.
El propósito de cada módulo es proporcionar funciones de producto específicas mediante la implementación de nuevas funciones o la ampliación de las funciones de otros módulos.
Cada módulo está diseñado para funcionar de forma independiente, por lo que la inclusión o exclusión de un módulo en particular no afecta a la funcionalidad de otros módulos.

Un módulo también puede implementar widgets, que son elementos de página que los usuarios empresariales pueden personalizar en el Admin.

Los módulos se pueden deshabilitar o quitar sin romper la coherencia de la aplicación del Magento.
Una excepción: Cuando el módulo depende de otros módulos, lo que requiere deshabilitar o quitar los módulos dependientes.

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: php, xml, block_

## O

### OMS

_sustantivo_

[OMS](https://omsdocs.magento.com) es la oferta del sistema Order Management de Adobe.

OMS es una solución flexible y asequible para administrar, vender y cumplir el inventario de cualquier canal de ventas.
OMS ofrece una experiencia de cliente perfecta, que aumenta las ventas al tiempo que reduce los costes y acelera el tiempo de comercialización.

Las funciones de OMS incluyen:

* Visibilidad global y administración de todo el inventario
* Capacidad de realizar envíos desde y hacia cualquier lugar
* Servicio al cliente más fácil y interactivo
* Mejor experiencia y lealtad del cliente

Más información: [Introducción a OMS](https://omsdocs.magento.com/en/getting-started/), [sitio de documentos de OMS](https://omsdocs.magento.com/en/)

_Atributos de término:_

* _Campo: característica, software de comercio, administración de pedidos_
* _Sinónimos: gestión de pedidos, MOM, sistema de gestión de pedidos, Magento Order Management_
* _Términos relacionados: administración de pedidos_

### encubrimiento origen

_sustantivo_

El encubrimiento de origen es una función de seguridad que permite a Adobe Commerce en la infraestructura de la nube bloquear cualquier tráfico que no sea de Fastly para evitar ataques DDoS, dirigiéndose a la infraestructura de la nube (origen).

Más información: [Ocultación de origen facial](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/fastly-origin-cloaking-enablement-faq.html)

_Atributos de término:_

* _Campo: seguridad_
* _Términos relacionados: firewall de aplicaciones web_

## P

### Page Builder

_sustantivo_

Page Builder es una extensión de Commerce para crear páginas con contenido enriquecido arrastrando y soltando controles creados previamente para definir diseños personalizados.
Estos controles también se conocen como &quot;tipos de contenido&quot;.
Los comerciantes pueden diseñar diseños y páginas sin experiencia de codificación.
Se proporciona compatibilidad con extensiones para que los desarrolladores amplíen Page Builder.

Más información: [Guía del usuario de Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html), [DevDocs de Page Builder](https://developer.adobe.com/commerce/frontend-core/page-builder/)

_Atributos de término:_

* _Campo: software de comercio, diseño_
* _Sinónimos: Administrador, Panel de administración, servidor, Interfaz de administración, IU de administración_
* _Términos relacionados: admin_

### pasarela de pago

_sustantivo_

Una pasarela de pago es un servicio de terceros que procesa sin problemas las transacciones con tarjetas de crédito sin que el cliente abandone el sitio del comerciante.

_Atributos de término:_

* _Campo: negocio, pedido, programación_

## R

### producto relacionado

_sustantivo_

Una selección de productos que se presenta como un incentivo para comprar artículos adicionales.
Por ejemplo, si el cliente está viendo la página de producto de una cámara, los productos relacionados podrían incluir otras cámaras comparables, una carcasa de cámara y un trípode.

_Atributos de término:_

* _Campo: software de comercio, producto_

## S

### reglas de ventas

_sustantivo_

Incluye las reglas del carro de compras y del catálogo, que se utilizan para asignar un precio a un producto para las promociones.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: reglas del carro de compras, reglas del catálogo_

### ámbito

_sustantivo_

En Adobe Commerce, el ámbito describe el alcance de la jerarquía de la tienda que puede afectar a una configuración.
El ámbito puede aplicarse a lo siguiente:

* Global: todos los sitios web, tiendas y vistas de tiendas
* Sitio web: el sitio web seleccionado y todas las tiendas y vistas de la tienda debajo de él
* Almacenar: la tienda seleccionada y todas las vistas de la tienda debajo de ella.
* Vista de tienda: la vista de tienda seleccionada.

Dentro de la jerarquía, la configuración aplicada en un nivel inferior puede anular algunas configuraciones de nivel superior.

_Atributos de término:_

* _Campo: software de comercio_

### contrato de servicio

_sustantivo_

Un conjunto de interfaces PHP definidas para un módulo.
Un contrato de servicio incluye interfaces de datos, que conservan la integridad de los datos, e interfaces de servicio, que ocultan detalles de lógica empresarial a los solicitantes de servicio, como controladores, servicios web y otros módulos.
Las API web se pueden enlazar a contratos de servicio a través de archivos de configuración.

_Atributos de término:_

* _Campo: programación_
* _Términos relacionados: php, web api_

### asentamiento

_sustantivo_

La liquidación tiene lugar cuando el banco adquirente y el emisor intercambian fondos y el producto se deposita en la cuenta de comerciante.

_Atributos de término:_

* _Campo: empresarial_

### Catálogo compartido

_sustantivo_

Característica que permite a los comerciantes crear un catálogo que puede servir como su catálogo completo o como un subconjunto de él y, a continuación, asignar precios personalizados para uno o más productos.
Los comerciantes pueden asignar este catálogo a una o varias empresas.

Por ejemplo, un comerciante B2B tiene tres clientes que han negociado tarifas específicas para el sitio de distribución de productos electrónicos del comerciante.
Al utilizar la función de catálogo compartido, el comerciante tiene:

* Un catálogo principal
* Un catálogo de cliente 1 (tal vez solo sean tres SKU con grandes descuentos en ellas desde el catálogo principal)
* Catálogo del cliente 2 (podría ser todo el catálogo con un 10 % de descuento)
* Catálogo del cliente 3 (algunas docenas de productos con descuentos del catálogo principal que van del 5% al 60%).

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: catalog, b2b_

### envío

_sustantivo_

Un envío contiene los productos que se van a enviar y genera un registro de los productos en un pedido que se han enviado.
Se puede asociar más de un envío con un único pedido.

_Atributos de término:_

* _Campo: negocio, pedido_

### documento de envío

_sustantivo_

Documento que acompaña a un envío. El documento enumera los productos y sus cantidades en el paquete de envío.

_Atributos de término:_

* _Campo: negocio, pedido_

### transportista

_sustantivo_

Una empresa que transporta paquetes. Los operadores comunes incluyen UPS, FedEx, DHL y USPS.

_Atributos de término:_

* _Campo: negocio, pedido_

### carro de compras

_sustantivo_

El conjunto de productos que un cliente ha seleccionado comprar, pero aún no ha comprado.
También hace referencia a un área de un sitio de comercio electrónico en la que se pueden encontrar estos productos para revisarlos y cerrarlos.

_Atributos de término:_

* _Campo: empresa, diseño, producto, programación_
* _Sinónimos: carrito, canasta_
* _Términos relacionados: reglas del carro de compras_

### producto simple

_sustantivo_

El tipo de producto más básico, un artículo físico con un solo SKU.
Los productos simples tienen varios controles de precios y de entrada que permiten vender variaciones del producto.
Se pueden utilizar productos simples en asociación con productos agrupados, agrupados y configurables.
Un producto simple con opciones personalizadas a veces se denomina producto compuesto.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: tipos de productos_

### SKU

_sustantivo_

Abreviatura de la unidad de stock.
Un número o código asignado a un producto para identificar el producto, las opciones, el precio y el fabricante.

_Atributos de término:_

* _Campo: negocios, precios, producto, programación_
* _Términos relacionados: catálogo compartido_

### página de bienvenida

_sustantivo_

Página promocional con un producto o anuncio; normalmente se muestra antes de la página principal.

_Atributos de término:_

* _Campo: diseño_

### bloque estático

_sustantivo_

Una unidad modular de contenido que un usuario puede colocar en el CMS de una página para mostrar texto e imágenes o ejecutar fragmentos de código.
Los bloques estáticos contienen contenido editable y pueden actuar como páginas de aterrizaje para categorías de productos.
Los widgets se pueden añadir a bloques estáticos para proporcionar funciones adicionales.

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: bloque cms, bloque_

### contenido estático

_sustantivo_

Contenido generado por el usuario (no generado por el código) que no cambia con frecuencia.

_Atributos de término:_

* _Campo: diseño_
* _Términos relacionados: contenido dinámico_

### archivos estáticos

_sustantivo_

Colección de recursos, como CSS, fuentes, imágenes y JavaScript, que utiliza una temática.

_Atributos de término:_

* _Campo: software de comercio_

### almacenar

_sustantivo_

El nivel de ámbito de Commerce de &quot;tienda&quot; es el segundo nivel de la jerarquía del sitio web, que es el siguiente: sitio web > tienda > vista de tienda.
Las tiendas se pueden organizar en una o varias. Cada tienda, potencialmente, tiene su propia categoría raíz y todos comparten datos de catálogo y de cliente.

Cada tienda puede tener varias vistas de la tienda, que normalmente se usan para presentar la tienda en una configuración regional y en un idioma diferentes.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: vista de tienda, sitio web_

### vista de tienda

_sustantivo_

El nivel de ámbito de Commerce de &quot;vista de tienda&quot; se refiere al tercer nivel en la jerarquía de sitios web, tiendas y vistas de tiendas.
Las vistas de tienda suelen presentar la tienda en una configuración regional y en un idioma diferentes.
Para cambiar las vistas de la tienda, use el selector de tiendas del encabezado.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: tienda, sitio web_

### escaparate

_sustantivo_

Tienda en línea que los clientes ven cuando visitan el sitio de Commerce.

_Atributos de término:_

* _Campo: software de comercio, producto_

## T

### regla fiscal

_sustantivo_

Una combinación de una clase de impuestos de producto, una clase de impuestos de cliente y un tipo impositivo. Esta regla define qué cálculo de impuestos se aplica.

_Atributos de término:_

* _Campo: empresarial_

### plantilla

_sustantivo_

Abreviatura de HTML template o PHTML template.
Un archivo PHTML contiene una mezcla de marcado de HTML y código PHP para insertar contenido dinámico en el HTML.
La mayoría de los bloques tienen al menos un archivo PHTML (template) que contiene el HTML estático generado por el bloque.
En el Administrador, las plantillas de correo electrónico y de newsletter combinan texto, imágenes y variables con marcado de HTML para producir contenido personalizado que envía el sistema.

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: block_

### tema

_sustantivo_

Contiene gráficos e información de apariencia.
Personaliza el aspecto de la tienda.
Adobe Commerce puede enviar temáticas en paquetes (Composer).
Pero los temas se pueden colocar en la aplicación / diseño, que no se envía en un paquete.
Los paquetes son la unidad de descarga de Composer y, a través del Commerce Marketplace, los usuarios de Commerce pueden descargar CE o EE como una serie de paquetes, donde los paquetes contienen módulos, temáticas o paquetes de idiomas.

_Atributos de término:_

* _Campo: software de comercio_

## U

### Componente de IU

_sustantivo_

Una etiqueta diseñada para el software de Adobe Commerce con el fin de permitir un procesamiento más sencillo y flexible de la interfaz de usuario (IU).
Los objetivos del sistema de componentes de la IU incluyen los siguientes:

* Simplificar los archivos XML de control de diseño
* Traslado de elementos de la interfaz de usuario de administración de HTML+JavaScript a un sistema de widgets personalizados de &quot;JavaScript puro&quot;
* Habilitar la creación de componentes de IU más complejos a partir de componentes más pequeños
* Procesamiento previo de datos para componentes de interfaz de usuario como JSON, estrechamente vinculados a objetos de datos back-end
* AJAX Uso de datos de componentes para actualizar la
* Introducción de una nueva DSL para crear los elementos anteriores

Más información: [Guía de componentes de la interfaz de usuario](https://developer.adobe.com/commerce/frontend-core/ui-components/), [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html)

_Atributos de término:_

* _Campo: programación_
* _Términos relacionados: JavaScript, diseño, componente, generador de páginas_

### ASCENDENTE

_sustantivo_

[PWA Studio](https://github.com/magento/pwa-studio) usa [UPWARD](https://developer.adobe.com/commerce/pwa-studio/guides/packages/upward/) en el desarrollo.
UPWARD es el acrónimo de Unified Progressive Web App Response Definition (Definición de respuesta de aplicación web progresiva unificada).
Un archivo de definición UPWARD describe cómo un servidor web ofrece y admite un Progressive Web Application.

Los archivos de definición UPWARD proporcionan detalles sobre el comportamiento del servidor utilizando un lenguaje declarativo independiente de la plataforma.
Esto permite que un Progressive Web Application se ejecute sobre un servidor compatible con UPWARD en cualquier idioma de cualquier pila de tecnología, ya que la aplicación solo está preocupada por el comportamiento del extremo HTTP desde el servidor UPWARD.

Un servidor UPWARD utiliza un archivo de definición para determinar el proceso o servicio apropiado para una solicitud de un shell de aplicación.
Describe cómo el servidor debe gestionar una solicitud y crear la respuesta para ella.

Un proyecto de PWA puede incluir un archivo de definición UPWARD para especificar sus dependencias de servicio.

_Atributos de término:_

* _Campo: diseño, software de comercio, programación_
* _Sinónimos: PWA Studio, Definición de respuesta de aplicación web progresiva unificada_
* _Términos relacionados: pwa_

## V

### Extensión agrupada de proveedor

_sustantivo_

El código producido por el proveedor que amplía o personaliza el comportamiento de Commerce y funciona como una extensión de terceros se considera una extensión agrupada por proveedor (VBE).
Los VBE se prueban exhaustivamente y se incluyen con cada versión compatible de Adobe Commerce.
Un VBE puede incluir módulos, temáticas y paquetes de idiomas.

Obtenga más información en el tema [Extensión de paquetes de proveedores](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html).

_Atributos de término:_

* _Campo: extensión de comercio, extensión agrupada de proveedor, extensión, VBE_
* _Sinónimos: extensión, VBE_
* _Términos relacionados: extensión, extensión agrupada_

### escala vertical

_sustantivo_

El escalado vertical (escalado) se refiere al aumento de la potencia de procesamiento de un solo servidor o clúster mediante la adición de E/S de disco o red, CPU o RAM.

_Atributos de término:_

* _Campo: entorno_

### producto virtual

_sustantivo_

Representa un producto no físico que se puede vender, como una suscripción, un servicio, una garantía o una suscripción.
Los productos virtuales se pueden vender por separado o incluir como parte de los siguientes tipos de productos: productos agrupados y paquetes de productos.
No requiere envío ni inventario.

El proceso de creación de un producto virtual y de un producto simple es casi el mismo.
Sin embargo, como un producto virtual no se envía, no hay ningún campo de Peso ni opción para incluir una tarjeta regalo.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: tipos de productos_

### tipo virtual

_sustantivo_

Los tipos virtuales son una forma de insertar diferentes dependencias en clases PHP existentes sin afectar a otras clases y sin tener que crear un archivo de clase.
Solo se puede hacer referencia a los tipos virtuales mediante invalidaciones de argumentos en un elemento `<type>` dentro de los archivos di.xml, nunca en el código fuente.
No se pueden extender y no pueden ser referencias como dependencias en un constructor de clases.

_Atributos de término:_

* _Campo: programación_
* _Términos relacionados: php_

## W

### sitio web

_sustantivo_

En el software de Adobe Commerce, el nivel más alto de una jerarquía de sitios web, por encima de la vista de tienda y tienda.
Puede tener varios sitios web, y cada sitio web puede tener un nombre de dominio diferente.
Los sitios web se pueden configurar para compartir datos de clientes o para no compartir datos.

_Atributos de término:_

* _Campo: software de comercio, diseño, producto_
* _Términos relacionados: tienda, vista de tienda_

### widget

_sustantivo_

Un [widget](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/widgets/widgets.html) es un fragmento de código preparado que se puede usar para colocar bloques, vínculos y contenido dinámico en ubicaciones específicas en páginas de tiendas.
Puede utilizar widgets para crear páginas de aterrizaje para campañas de marketing y mostrar contenido promocional en ubicaciones específicas de la tienda.
Los widgets también se pueden utilizar para agregar elementos interactivos y bloques de acción para sistemas de revisión externos, chats de vídeo, votaciones y formularios de suscripción, o para proporcionar elementos de navegación para nubes de etiquetas y reguladores de imagen.

_Atributos de término:_

* _Campo: empresa, software de comercio, diseño_
* _Términos relacionados: block_
