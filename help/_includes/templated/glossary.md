---
source-git-commit: 405c1d7073e5936aefc7fb3c6eb1d5dd4d69a066
workflow-type: tm+mt
source-wordcount: '6574'
ht-degree: 0%

---
# Glosario de Adobe Commerce

## A

### encima del pliegue

_adjetivo_

En una ventana del explorador, el contenido que es visible inmediatamente después de cargar una página web y antes de que un usuario se desplace hacia abajo en la página.
Al diseñar el diseño, utilice formatos flexibles para mostrar de la mejor manera los productos, las funciones, las ventas, las notificaciones, las opciones, etc. de mayor prioridad en esta área.

Con móviles y tabletas, el área de arriba del pliegue difiere considerablemente, especialmente en el tamaño y las dimensiones de la pantalla y la orientación al ver (vertical frente a horizontal).
El uso de temas interactivos y las pruebas pueden ayudar a encontrar la combinación correcta de contenido y diseño.

_Atributos de término:_

* _Campo: diseño_

### rama activa

_noun_

Una rama o entorno activo es uno que está conectado a una instancia implementada o en ejecución con acceso a los servicios.
Cuando se desactiva, se elimina la conexión a los servicios y a la instancia en ejecución, pero se conserva el código.
Se convierte en una rama de git normal.

_Atributos de término:_

* _Campo: nube_

### adaptador

_noun_

Una clase que permite que dos sistemas incompatibles funcionen juntos sin modificar el código fuente del sistema.
Algunos ejemplos son adaptadores de base de datos, adaptadores de caché, adaptadores de filesystem, adaptadores de bibliotecas posteriores al procesador y otros tipos de adaptadores informáticos.

_Atributos de término:_

* _Campo: programación_

### admin

_noun_

En software, una función de usuario con privilegios de administrador completos para administrar toda la funcionalidad.
En Adobe Commerce, los usuarios administradores tienen permisos completos y acceso a todas las funciones, opciones y funcionalidades del administrador.
También pueden crear usuarios y funciones.

Más información: [Adición de usuarios](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html)

_Atributos de término:_

* _Campo: software de comercio_
* _Sinónimos: administrador, superusuario_
* _Términos relacionados: administrador de comercio_

### Área de administración

_noun_

El back office protegido por contraseña de su tienda donde se administran los pedidos, el catálogo, el contenido y las configuraciones.
Los usuarios acceden al área de administración para administrar la tienda, que incluye productos, pedidos, envíos, contenido de CMS, diseño de la tienda, información del cliente, etc.
Los usuarios administradores tienen una función asociada con permisos que controlan el acceso a las funciones, opciones y capacidades.

Más información: [Guía del usuario de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Atributos de término:_

* _Campo: software de comercio_
* _Sinónimos: Administrador, panel de administración, back-end, interfaz de administración, interfaz de administración_
* _Términos relacionados: admin_

### Variables ADMIN

_noun_

Las variables ADMIN son variables de entorno de proyecto para anular los ajustes de configuración de la cuenta de usuario de administración para acceder a la IU de administración.

Más información: [Variables ADMIN](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-admin.html)

_Atributos de término:_

* _Campo: administrador, nube_

### adminhtml

_noun_

El nombre del área interna asignada al administrador.

Más información: [Guía del usuario de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html)

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: área, administración de comercio_

### area

_noun_

Área es un término abstracto para un ámbito de aplicación de Magento.
Las áreas son componentes lógicos que organizan el código para optimizar el procesamiento de solicitudes.
Las áreas reducen las exigencias de memoria de los objetos de configuración a los que se accede desde la tienda, y optimizan las llamadas de servicio web cargando solo el código dependiente requerido.
Cada área puede contener código completamente diferente para procesar direcciones URL y solicitudes.

Las áreas de Adobe Commerce incluyen:

* Administración (adminhtml)
* Tienda
* API web REST (webapi_rest)

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: componente de comercio, tienda_

### attribute

_noun_

Característica o propiedad de un producto que describe algún aspecto del producto.
Los usuarios de Adobe Commerce o Magento Open Source pueden crear atributos personalizados para agregarlos al conjunto de atributos predeterminado o a un conjunto de atributos personalizados.
Cree estos atributos mediante el Administrador o mediante programación.
Ejemplos: color, tamaño, peso, precio, edad, sexo, etc.

Los atributos personalizados son un tipo de atributo Entity-Attribute-Value (EAV).

Para integraciones como Canal de anuncios de Google Shopping y Sales Channel de Amazon, puede asignar atributos de comercio a atributos de terceros para mostrar y vender correctamente productos y anuncios en pantalla.

Más información: [EAV y extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Sinónimos: atributo de producto, atributo personalizado_
* _Términos relacionados: atributo de extensión_

### grupo de atributos

_noun_

Agrupación lógica de atributos dentro de un conjunto de atributos.

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: attribute_

### conjunto de atributos

_noun_

Colección de grupos de atributos, personalizada para un producto específico.
Ejemplo: Un conjunto de atributos de camiseta puede incluir color, tamaño, sexo y marca.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: attribute_

### coste de inventario promedio

_noun_

Precio del producto, menos cupones o descuentos, más flete e impuestos aplicables.
El promedio se determina añadiendo el costo inicial del inventario cada mes, más el costo final del inventario para el último mes del período.

_Atributos de término:_

* _Campo: producto, precio, inventario_

## B

### moneda base

_noun_

La moneda principal que se utiliza por vista de tienda para todos los pagos en línea.
Las tiendas pueden aceptar monedas de más de 200 países en todo el mundo.
El frente de la tienda proporciona un selector de moneda para varias monedas aceptadas para un país o configuración regional específicos.
Los símbolos monetarios aparecen en los documentos de precios y ventas de productos, como pedidos y facturas.
Puede personalizar los símbolos de moneda según sea necesario y establecer la visualización del precio por separado para cada tienda o vista.

Más información: [Moneda](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency.html)

_Atributos de término:_

* _Campo: precio_

### procesamiento por lotes

_noun_

Para realizar una tarea o cambiar varios elementos a la vez, sin repetición manual.

_Atributos de término:_

* _Campo: programación_
* _Sinónimos: operaciones masivas_

### block

_noun_

Unidad de salida de página que representa cierto contenido distintivo -un fragmento de información, un elemento de interfaz de usuario- todo visualmente tangible para el usuario final.
[Bloques](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) se implementan y proporcionan mediante módulos.
Los bloques utilizan plantillas para generar un HTML.
Algunos ejemplos de bloques son una lista de categorías, un minicarrito, etiquetas de productos y listas de productos.

[Bloques dinámicos](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/dynamic-blocks/dynamic-blocks.html) proporciona contenido basado en la lógica, como las reglas de precios.

El Creador de páginas amplía la interactividad y la creación de [bloques](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/block.html) y [bloques dinámicos](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/dynamic-block.html).

_Atributos de término:_

* _Campo: software de comercio_
* _Sinónimos: Bloques dinámicos_
* _Términos relacionados: bloque cms, bloque estático, contenedor, diseño_

### marca

_sustantivo, verbo_

Una identidad única que define un producto o grupo de productos determinado por el fabricante o Designer.
Estas incluyen marcas de nombre para ropa, electrodomésticos, artículos de lujo, etc.
Su empresa también puede ser la marca, vendiendo productos bajo varias marcas en función de la unidad comercial, la audiencia de destino, etc.

Utilice atributos personalizados para guardar la información de marca de los productos.

Algunas extensiones e integraciones pueden utilizar o requerir una marca para sus productos, como Google Shopping ads Channel y Amazon Sales Channel.

_Atributos de término:_

* _Campo: negocio_

### ladrillo y mortero

_adjetivo_

Un negocio minorista con una ubicación física permanente, a diferencia de los negocios que funcionan virtual o exclusivamente a través de Internet.

Para [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) y [Administración de pedidos](https://omsdocs.magento.com/getting-started/terminology/), esta tienda es una fuente para realizar el seguimiento de las cantidades de productos, los pedidos de envío y la compatibilidad con la recogida en la tienda.

_Atributos de término:_

* _Campo: negocio, inventario_

### operaciones masivas

_noun_

Las operaciones masivas son acciones que se realizan a gran escala.
Las tareas de operaciones masivas de ejemplo incluyen importar o exportar artículos, cambiar precios en una escala masiva y asignar productos a un almacén.

Más información: [Operaciones masivas de DevDocs](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)

_Atributos de término:_

* _Campo: programación_

### paquete de producto

_noun_

Permite a los clientes ensamblar un producto personalizable &quot;propio&quot; a partir de diversas opciones y configuraciones.
Cada elemento del paquete es un producto simple o virtual independiente.

Más información: [Productos configurables](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: producto simple, producto virtual, tipos de producto_

### extensión agrupada

_noun_

El código que amplía o personaliza el comportamiento de Adobe Commerce se considera una extensión agrupada.
Puede incluir módulos, temas y paquetes de idiomas.

_Atributos de término:_

* _Campo: extensión agrupada, extensión_
* _Sinónimos: Extensión_
* _Términos relacionados: extensión, extensión agrupada de proveedor_

## C

### back-end de caché

_noun_

Almacena registros de caché en un sistema back-end de dos niveles dentro del marco predeterminado de Zend.
Una caché de primer nivel es rápida (por ejemplo, un back-end APC o Memcached), pero es limitada y no admite el etiquetado y la agrupación de entradas de caché.
La caché de segundo nivel, por ejemplo, un sistema de archivos o un servidor de Redis, es más lenta, pero admite el etiquetado y la agrupación.

_Atributos de término:_

* _Campo: programación_
* _Términos relacionados: backend_

### front-end de caché

_noun_

Especifica qué tipo de datos se almacena en el servidor de caché.

_Atributos de término:_

* _Campo: programación_
* _Términos relacionados: front-end_

### tipo de caché

_noun_

Una caché almacena datos para que las llamadas futuras a esos datos se carguen más rápido.

Adobe Commerce incluye estos tipos:
* Configuración
* Diseños
* Salida del HTML de bloque
* Datos de colecciones
* Datos de reflejo
* Operaciones DDL de la base de datos
* Configuración compilada
* Tipos y atributos de EAV
* Notificación al cliente
* Configuración de integraciones
* Configuración de la API de integraciones
* Caché de página (la más conocida)
* Configuración de servicios web
* Traducciones
* Regla de Target
* Caché de producto de Google
* Vértice

Se pueden crear y definir otros tipos.

_Atributos de término:_

* _Campo: programación_

### captura

_verbo_

Proceso de convertir un importe de pedido autorizado en una transacción facturable.
Las transacciones no pueden capturarse hasta que se autoricen y las autorizaciones no pueden capturarse hasta que se hayan enviado los bienes o servicios.

_Atributos de término:_

* _Campo: negocio_
* _Términos relacionados: autorización, estado de pedido_

### titular de la tarjeta

_noun_

Una persona autorizada por una institución financiera para realizar compras en una cuenta de tarjeta de crédito.

_Atributos de término:_

* _Campo: negocio, pedido_

### reglas del carro de compras

_noun_

Las reglas de precios que se aplican al carro de compras y a los déclencheur de una acción en respuesta a un conjunto de condiciones.
Se utiliza para crear promociones.

_Atributos de término:_

* _Campo: software de comercio, precios, producto_
* _Términos relacionados: reglas de catálogo, carro de compras_

### catálogo

_noun_

Para los comerciantes, el catálogo representa su inventario de productos.
Dentro de la arquitectura de Adobe Commerce, el catálogo consta de categorías, productos y atributos de producto.

Cada tienda de comercio solo tiene un catálogo de productos, que se comparte en todas las vistas de la tienda.
En una instalación de varias tiendas, cada tienda puede tener un catálogo independiente o compartir el catálogo.
El catálogo de la tienda actual está determinado por la categoría raíz predeterminada, visible para el usuario en la barra de navegación superior (menú principal) de la tienda.
(El término &quot;categoría raíz&quot; puede resultar confuso, ya que la &quot;categoría raíz&quot; no es en realidad una categoría, sino un contenedor para el menú, que consta de categorías y subcategorías).

Puede crear tantas categorías raíz como desee, pero solo se puede usar una (la predeterminada) a la vez.

_Atributos de término:_

* _Campo: software de comercio, precios, producto_
* _Términos relacionados: catálogo compartido, regla de catálogo_

### reglas de catálogo

_noun_

Las reglas de precios que se aplican a productos específicos y generan el déclencheur de una acción en respuesta a un conjunto de condiciones.
Se utiliza para crear promociones.

_Atributos de término:_

* _Campo: software de comercio, precios, producto_
* _Términos relacionados: reglas del carro de compras, catálogo_

### categoría

_noun_

Grupo de productos que tienen algo en común.
El menú principal de la tienda está organizado en categorías y subcategorías de productos.

_Atributos de término:_

* _Campo: software de comercio, producto_

### cierre de compra

_noun_

Proceso de recopilación de la información de pago y envío necesaria para completar la compra de artículos en el carro de compras.
Una vez que el cliente revisa la información y envía el pedido, se envía una confirmación por correo electrónico al cliente.

El cierre de compra tiene muchas opciones y configuración listas para usar y por extensión.

Más información: [Tutorial de cierre de compra](https://developer.adobe.com/commerce/php/tutorials/frontend/custom-checkout/)

_Atributos de término:_

* _Campo: negocio, diseño, pedido, producto, programación_

### variables de nube

_noun_

Las variables de nube son variables de entorno específicas de Adobe Commerce en la infraestructura de nube y utilizan la variable **`MAGENTO_CLOUD`** prefijo .

Más información: [Variables de nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud.html)

_Atributos de término:_

* _Campo: nube_

### Bloque CMS

_noun_

Una variante especial de [block](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/blocks/blocks.html) que solo se puede crear en el administrador y no se puede hacer referencia a él a través de archivos de diseño.

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: bloque, bloque estático_

### datos complejos

_noun_

Datos asociados con varias opciones de producto.

_Atributos de término:_

* _Campo: programación_

### componente

_noun_

Se utiliza para hacer referencia a un módulo, tema o paquete de idioma en Adobe Commerce.

_Atributos de término:_

* _Campo: software de comercio_
* _Sinónimos: componente_
* _Términos relacionados: componente ui_

### producto configurable

_noun_

Un producto configurable se parece a un único producto con listas desplegables de opciones para cada variación.
Cada opción es en realidad un producto simple independiente con un SKU único, lo que permite rastrear el inventario para cada variación de producto.
Para lograr un efecto similar, se puede utilizar un producto simple con opciones personalizadas, pero sin la capacidad de realizar un seguimiento del inventario para cada variación.
Los productos con varias opciones a veces se denominan productos compuestos.

Aunque un producto configurable utiliza más SKU y puede tardar un poco más en configurarse, al final puede ahorrarle tiempo.
Si planea ampliar su negocio, el tipo de producto configurable podría ser una mejor opción para un producto con múltiples opciones.

Ejemplo: Camisetas disponibles en dos colores y tres tamaños.
Se deben crear seis variantes como productos individuales (cada una con su propio SKU).
A continuación, todas las variantes se añaden a un producto configurable donde los clientes pueden elegir el tamaño y el color y luego agregarlo al carro de compras.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: tipos de producto_

### tasa de conversión

_noun_

El porcentaje de visitantes que se convierten en compradores.

_Atributos de término:_

* _Campo: negocio, pedido_

### escalado de nivel principal

_noun_

El escalado del nivel principal consiste en tres nodos de servicio para almacenamiento de datos, caché y servicios como OpenSearch, Elasticsearch, MariaDB y Redis.

_Atributos de término:_

* _Campo: nube_

### nota de crédito

_noun_

Documento emitido por el comerciante a un cliente para que cancele un saldo pendiente debido a recargo, reembolso o devolución de bienes.
La nota restaura los fondos en la cuenta del cliente.

_Atributos de término:_

* _Campo: negocio, pedido_

### comentario de nota de crédito

_noun_

Detalles por los cuales se abonó al cliente un importe de nota de abono.

_Atributos de término:_

* _Campo: negocio, pedido_

### artículo nota de abono

_noun_

Artículo facturado para el cual un comerciante crea una nota de crédito.

_Atributos de término:_

* _Campo: negocio, pedido_

### venta cruzada

_sustantivo, adjetivo, verbo_

Producto que aparece junto al carro de compras.
Cuando un cliente navega a la página del carro de compras, estos productos se muestran como ventas cruzadas a los artículos que ya están en el carro de compras.
Son similares a las compras por impulso, como revistas y dulces en las cajas registradoras de las tiendas de comestibles.

_Atributos de término:_

* _Campo: negocio, producto_
* _Términos relacionados: impulsar ventas_

### CVM

_noun_

Una abreviatura de &quot;Método de Verificación de Titulares de Tarjetas&quot;.
Una forma de verificar la identidad del cliente confirmando un código de seguridad de tarjeta de crédito de 3 o 4 dígitos con el procesador de pagos.

_Atributos de término:_

* _Campo: negocio, pedido_
* _Sinónimos: Método de verificación de los titulares de tarjetas_
* _Términos relacionados: código de seguridad_

## D

### esquema de base de datos

_noun_

Estructura de los datos de una base de datos.
Define cómo se organizan los datos y cómo se rigen las relaciones de datos, incluidas todas las restricciones aplicadas a los datos.
Un módulo puede contener fragmentos del esquema de base de datos si dicho módulo tiene datos que deben almacenarse en la base de datos.

_Atributos de término:_

* _Campo: programación_
* _Sinónimos: esquema_

### inyección de dependencia

_noun_

Un patrón de diseño de software que permite a una clase especificar sus dependencias sin tener que construirlas.
Esta clase delega la responsabilidad de inyectar la dependencia a la clase que realiza la llamada.
Se utiliza para facilitar las pruebas.
Para definir dependencias para clases, edite el archivo de configuración di.xml .

_Atributos de término:_

* _Campo: programación_

### implementar clave

_noun_

Una clave de implementación es la clave pública SSH del proyecto y permite el acceso de solo lectura o lectura-escritura (si está habilitada) a un repositorio Git.

Más información: [Conexiones seguras](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html)

_Atributos de término:_

* _Campo: nube_

### inclusión doble

_sustantivo, verbo_

Un proceso de verificación de correo electrónico que requiere que los suscriptores potenciales completen un segundo paso que confirme su intención de suscribirse.

_Atributos de término:_

* _Campo: negocio_

### producto descargable

_noun_

Producto descargable digitalmente que consta de uno o más archivos descargados, como un eBook, música, vídeo, aplicación de software o una actualización.
Puedes ofrecer un álbum a la venta y vender cada canción individualmente.
Un producto descargable puede entregar una versión electrónica de su catálogo de productos.

Los archivos descargables pueden residir en el servidor o proporcionarse como direcciones URL a cualquier otro servidor o red de entrega de contenido.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: tipos de producto_

### contenido dinámico

_noun_

Contenido generado por código en lugar de leerse desde una plantilla estática.
Después de que el contenido dinámico se procese inicialmente cuando un usuario visita una página, a veces el contenido se puede almacenar en caché y reutilizar sin requerir otra llamada dinámica al volver a visitar.

_Atributos de término:_

* _Campo: diseño_
* _Términos relacionados: php_

### URL de dynamic media

_noun_

Dirección URL que el sistema genera dinámicamente para hacer referencia a una imagen u otro medio.
La dirección se vincula directamente a los recursos almacenados en un servidor o en una red de entrega de contenido.
Para usar una dirección URL estática, cambie la configuración.
Sin embargo, si las direcciones URL de Dynamic Media se incluyen en el catálogo al deshabilitar la configuración, cada referencia del catálogo se convierte en un vínculo roto.
Los vínculos se pueden restaurar habilitando de nuevo las direcciones URL de Dynamic Media.
El uso de direcciones URL de medios dinámicos puede afectar al rendimiento de la búsqueda en el catálogo.

Formato de código: media url=&quot;path/to/image.jpg&quot;

_Atributos de término:_

* _Campo: programación_
* _Términos relacionados: red de entrega de contenido, url_

## E

### paquete ece-tools

_noun_

Conjunto de secuencias de comandos y herramientas diseñadas para administrar e implementar la aplicación Commerce. Este paquete simplifica muchos Adobe Commerce en procesos de infraestructura en la nube, incluida la implementación en un entorno Docker, la administración de crons, la verificación de la configuración del proyecto y la aplicación de parches de Adobe.

Más información: [paquete ece-tools](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/package-overview.html)

_Atributos de término:_

* _Campo: cli, cloud, implementar_

### entity

_noun_

Una unidad u objeto únicos en la programación.
Contiene atributos o parámetros que se pueden modificar.
Algunos ejemplos son el ensayo (donde una actualización puede cambiar entidades como reglas de precios, productos o categorías) y los registros de base de datos (donde los contratos de servicio incluyen estructuras de datos que se envían y reciben).

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: atributo, reglas del carro de compras, reglas de catálogo_

### valor de atributo de entidad

_noun_

Para entidades de base de datos, un modelo de datos que codifica entidades de forma eficaz.
Almacena el id de entidad, el nombre de atributo y el valor como tres, lo que permite crear nuevos nombres de atributo de entidad en cualquier momento.
En la codificación, el número de atributos que se puede utilizar para describir entidades puede escalar ampliamente, pero el número que se aplica a una entidad determinada se minimiza.
Este modelo de datos es flexible, pero puede ser lento.

Más información: [EAV y extension_attributes](https://developer.adobe.com/commerce/php/development/components/attributes/)

_Atributos de término:_

* _Campo: programación_
* _Sinónimos: eav_

### contenido permanente

_noun_

Contenido que tiene una larga vida útil o contenido que se puede reutilizar.

_Atributos de término:_

* _Campo: negocio_

### Extensión

_noun_

Código que amplía o personaliza el comportamiento de Adobe Commerce.
Opcionalmente, puede empaquetar y distribuir una extensión en el Commerce Marketplace u otro sistema de distribución de extensiones.
Una extensión de comercio puede incluir módulos, temas y paquetes de idiomas.

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: componente, módulo, paquete_

### atributo de extensión

_noun_

Amplíe la funcionalidad y utilice a menudo tipos de datos más complejos que los atributos personalizados. Estos atributos no aparecen en la GUI.

Más información: [Añadir atributos de extensión a la entidad](https://developer.adobe.com/commerce/php/development/components/add-attributes/)

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: atributo, valor de atributo de entidad_

## F

### carga a bordo

_noun_

En el transporte marítimo internacional, este término significa que la parte receptora es responsable de los gastos de envío.
FOB puede basarse en el lugar de origen o de destino y ser designado como fletes recaudados o fletes prepagados.

_Atributos de término:_

* _Campo: negocio, pedido, precio_
* _Sinónimos: fob_

### front-end

_adjetivo_

En una aplicación cliente-servidor, está el back-end y el front-end.
El componente front-end, o cliente, es una interfaz que permite a los usuarios manipular o interactuar con el código backend subyacente.
El código back-end se ejecuta en un servidor.
Un usuario no puede acceder directamente al código back-end.
Un usuario interactúa con la tienda, que a su vez utiliza código que se ejecuta en el servidor de comercio.

Nota: En el pasado, la tienda ha sido referida como el &quot;front-end&quot;, y el administrador ha sido referido como el &quot;backend&quot;. Este uso ya no es compatible.

_Atributos de término:_

* _Campo: diseño, programación_
* _Sinónimos: lado del cliente_
* _Términos relacionados: back-end, tienda, front-end de caché_

### propiedades frontend

_noun_

Propiedades que determinan la presentación y el comportamiento de un atributo desde el punto de vista del cliente en su tienda.

_Atributos de término:_

* _Campo: diseño, programación_

### cumplimiento

_noun_

Proceso de administración de envíos de clientes.

_Atributos de término:_

* _Campo: negocio_

## G

### tarjeta regalo

_noun_

Tarjeta de prepago o certificado de regalo que se puede usar para realizar compras en la tienda.
A cada tarjeta regalo se le asigna un código único que se introduce durante el cierre de compra.
El valor de la tarjeta regalo se refleja en el saldo de la cuenta de la tarjeta de regalo.
Hay tres tipos de tarjetas de regalo:

* Las tarjetas de regalo &quot;físicas&quot; pueden ser producidas a partir de material plástico o de tarjeta, enviadas al cliente.
* Las tarjetas de regalo &quot;virtuales&quot; se envían por correo electrónico.
* Las tarjetas de regalo &quot;combinadas&quot; son una combinación de las dos, enviadas al destinatario como una tarjeta física y también entregadas por correo electrónico.
Las tarjetas de regalo se pueden configurar, incluidas las opciones para la idoneidad del producto y la selección de cantidades abiertas o fijas.

El administrador de la tienda también puede canjear una tarjeta de regalo a solicitud del cliente cuando el pedido se está creando en el servidor.

Las tarjetas de regalo también ayudan a las promociones, ya que los administradores de las tiendas pueden crear manualmente las cuentas de tarjetas de regalo en el servidor y enviar los códigos de tarjetas de regalo al segmento de clientes específico.
Las tarjetas de regalo pueden servir como un programa de fidelidad dirigido a los clientes más activos que realizan numerosas compras en la tienda web o una campaña promocional específica durante las vacaciones.

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: tipos de producto_

### margen bruto

_noun_

La diferencia entre el coste y el precio de un producto.

_Atributos de término:_

* _Campo: negocio_

### producto agrupado

_noun_

Tipo de producto con varios productos independientes similares agrupados en una sola página.
Se puede ofrecer con variaciones de un solo producto o agrupándolas por temporada o tema para crear un conjunto coordinado.
Cada producto se puede adquirir por separado o como parte del grupo.

Por ejemplo, para un cuchillo disponible en cuatro tamaños, los cuatro cuchillos se pueden mostrar dentro de una página de producto agrupada.
Los clientes pueden seleccionar los tamaños que deseen y agregarlos al carro de compras desde esta página.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: producto simple, tipos de producto_

## H

### handle

_noun_

Generalmente, un control es una forma de hacer referencia a un objeto.
En Adobe Commerce, los identificadores se utilizan en muchos lugares, normalmente para identificar una página.
En el caso de los controles de página, el nombre del identificador se deriva de la dirección URL y se utiliza para localizar y cargar los archivos de diseño de la página a la que se hace referencia.
Por ejemplo, en el módulo Cliente, hay un archivo de diseño llamado &quot;view/frontend/layout/checkout_cart_index.xml&quot;.
Aquí &quot;frontend&quot; es el nombre de área y &quot;checkout_cart_index&quot; es el nombre de controlador, ambos derivados de la dirección URL.

_Atributos de término:_

* _Campo: programación_
* _Sinónimos: identificador de página_

### escala horizontal

_noun_

El escalado horizontal (también conocido como escalado) es el proceso de agregar nodos o equipos adicionales a su infraestructura para satisfacer la creciente demanda.

_Atributos de término:_

* _Campo: nube_

## I

### interceptación

_noun_

Proceso de inyección de nuevo código antes, después o alrededor de una función pública existente de una clase PHP.

Para interceptar una función, un complemento implementa el código adicional que se va a invocar.
Los complementos están asociados a puntos de intercepción por el archivo de configuración de inyección de dependencias (di.xml).
Si se definen varios complementos en la misma función, la configuración de inyección de dependencias define el orden en que se invocan los complementos, lo que permite utilizar varios complementos sin conflictos.

_Atributos de término:_

* _Campo: programación_
* _Términos relacionados: plug-in_

## L

### layout

_noun_

En la construcción de una página de comercio, un diseño es una serie de bloques ensamblados en una jerarquía que representa la estructura de la página.

Los archivos de diseño de página se centran en el nivel más alto de estructura de la página (encabezado, pie de página, área de contenido principal, barra lateral izquierda, etc.).
A continuación, los archivos de diseño ensamblan el contenido (bloques) en estas áreas diferentes de la página.

_Atributos de término:_

* _Campo: software de diseño, comercio_
* _Términos relacionados: instrucciones de diseño, bloque_

### instrucciones de diseño

_noun_

Marcado en un archivo de diseño que describe los cambios que se aplicarán a un árbol de elementos estructurado de bloques, contenedores y componentes de la interfaz de usuario.
Un solo archivo de diseño puede contener varias instrucciones de diseño.
Las instrucciones de diseño se codifican en XML en los archivos de diseño.

_Atributos de término:_

* _Campo: diseño, programación_
* _Términos relacionados: diseño, bloque, contenedor, componente ui_

### actualización de diseño

_noun_

Se utiliza para fragmentos de código que se agregan para modificar el diseño XML o para importar las instrucciones de diseño de otro archivo.

_Atributos de término:_

* _Campo: software de diseño, comercio_

### Propietario de la licencia

_noun_

El propietario de la licencia (también conocido como propietario de cuenta) es la persona designada en una organización empresarial que gestiona los pagos y otros problemas relacionados con el negocio para Adobe Commerce en la cuenta de infraestructura de nube.
Esta persona sirve de punto de contacto con el Adobe.
Una vez que una empresa compra una Adobe Commerce al suscribirse a la infraestructura de nube, el acceso inicial al proyecto y al código solo está disponible para la persona designada como Propietario de la licencia.

_Atributos de término:_

* _Campo: negocio_

## M

### MAGEID

_noun_

MAGEID suele ser el contacto de facturación de la cuenta de Adobe Commerce (y puede que no sea el propietario del proyecto de Adobe Commerce en el proyecto de infraestructura de nube).
Para tener acceso a Adobe Commerce y Adobe Commerce en paquetes de infraestructura de nube, debe utilizar claves de acceso asociadas con un MAGEID al que se le haya concedido acceso a esos paquetes.

Más información: [Obtener las claves de autenticación](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html)

_Atributos de término:_

* _Campo: software de comercio_

### markup

_noun_

En marketing y venta minorista, un porcentaje agregado al coste de un artículo para determinar el precio de venta minorista.
[Configuración del marcado](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/settings/settings-advanced-custom-options.html), o markdown, de un producto a través de opciones personalizables del producto.

En desarrollo, un idioma de equipo que controla el procesamiento, la presentación y el formato del texto.
Además, las etiquetas de marcado son fragmentos de código que añaden funcionalidad o contenido a una página o bloque de CMS.

_Atributos de término:_

* _Campo: negocio, programación_
* _Sinónimos: Markdown_

### entorno maestro

_noun_

En Adobe Commerce en la infraestructura de la nube, los proyectos Pro utilizan un entorno Platform as a Service (PaaS) activo denominado master que incluye una copia de la base de datos del entorno de producción y del servidor web.

_Atributos de término:_

* _Campo: nube_

### cuenta de comerciante

_noun_

Cuenta con un banco o institución financiera que permite aceptar transacciones con tarjeta de crédito.

_Atributos de término:_

* _Campo: negocio_

### MFTF

_noun_

MFTF es un [Marco de pruebas funcionales](https://developer.adobe.com/commerce/testing/functional-testing-framework/).
Proporciona un marco de pruebas para desarrolladores de comercio e ingenieros de software, como especialistas en control de calidad, desarrolladores de PHP e integradores de sistemas.
Los desarrolladores y el control de calidad pueden escribir pruebas para intentar interacciones del usuario con aplicaciones web, comprobar la funcionalidad y automatizar las pruebas de regresión.

_Atributos de término:_

* _Campo: software de comercio, programación_
* _Términos relacionados: bloque cms, bloque estático, contenedor, diseño_

### módulo

_noun_

Código que cambia o amplía las funciones proporcionadas por la aplicación Magento.
Un módulo está contenido en una estructura de directorios que contiene archivos PHP y XML (configuración, bloques, controladores, ayudantes, modelos, etc.) relacionados con una funcionalidad específica para ofrecer una colección distinta de funciones de producto.
El propósito de cada módulo es proporcionar características específicas del producto mediante la implementación de nuevas funciones o la ampliación de la funcionalidad de otros módulos.
Cada módulo está diseñado para funcionar de forma independiente, por lo que la inclusión o exclusión de un módulo en particular no afecta a la funcionalidad de otros módulos.

Un módulo también puede implementar widgets, que son elementos de página que los usuarios empresariales pueden personalizar en el Administrador.

Los módulos se pueden desactivar o eliminar sin romper la coherencia de la aplicación Magento.
Una excepción: Cuando el módulo depende de otros módulos, lo que requiere deshabilitar o quitar los módulos dependientes.

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: php, xml, block_

## O

### OMS

_noun_

[OMS](https://omsdocs.magento.com) es la oferta del sistema de gestión de pedidos de Adobe.

OMS es una solución flexible y asequible para administrar, vender y cumplir el inventario de cualquier canal de ventas.
OMS proporciona una experiencia perfecta para el cliente, lo que aumenta las ventas al tiempo que reduce los costos y acelera el tiempo de comercialización.

Las capacidades de OMS incluyen:

* Visibilidad y administración globales de todo el inventario
* Capacidad de envío desde y hacia cualquier lugar
* Servicio al cliente más fácil y con mayor capacidad de respuesta
* Mejor experiencia y lealtad del cliente

Más información: [Introducción a OMS](https://omsdocs.magento.com/en/getting-started/), [Sitio de OMS Docs](https://omsdocs.magento.com/en/)

_Atributos de término:_

* _Campo: función, software de comercio, gestión de pedidos_
* _Sinónimos: gestión de pedidos, MOM, sistema de gestión de pedidos, Magento Order Management_
* _Términos relacionados: gestión de pedidos_

### encubrimiento de origen

_noun_

La ocultación del origen es una función de seguridad que permite a Adobe Commerce en la infraestructura de la nube bloquear cualquier tráfico que no sea FAdministración para evitar ataques DDoS, yendo a la infraestructura de la nube (origen).

Más información: [Trazado de origen rápido](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/fastly-origin-cloaking-enablement-faq.html)

_Atributos de término:_

* _Campo: seguridad_
* _Términos relacionados: servidor de seguridad de aplicaciones web_

## P

### Page Builder

_noun_

Page Builder es una extensión de comercio para crear páginas con contenido enriquecido arrastrando y soltando controles pregenerados para definir diseños personalizados.
Estos controles también se conocen como &quot;tipos de contenido&quot;.
Los comerciantes pueden diseñar diseños y páginas sin tener que codificar la experiencia.
Los desarrolladores pueden ampliar el Page Builder con soporte de extensión.

Más información: [Guía del usuario del Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html), [Documentos de desarrollo del creador de páginas](https://developer.adobe.com/commerce/frontend-core/page-builder/)

_Atributos de término:_

* _Campo: software de comercio, diseño_
* _Sinónimos: Administrador, panel de administración, back-end, interfaz de administración, interfaz de administración_
* _Términos relacionados: admin_

### puerta de enlace de pago

_noun_

Una puerta de enlace de pago es un servicio de terceros que procesa sin problemas las transacciones con tarjetas de crédito sin que el cliente abandone el sitio del comerciante.

_Atributos de término:_

* _Campo: negocio, pedido, programación_

## R

### producto relacionado

_noun_

Una selección de productos que se presenta como un incentivo para comprar artículos adicionales.
Por ejemplo, si el cliente está viendo la página de producto de una cámara, los productos relacionados podrían incluir otras cámaras comparables, un caso de cámara y un trípode.

_Atributos de término:_

* _Campo: software de comercio, producto_

## S

### reglas de ventas

_noun_

Incluye reglas de catálogo y carro de compras, que se utilizan para cotizar un producto para promociones.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: reglas del carro de compras, reglas de catálogo_

### scope

_noun_

En Adobe Commerce, scope describe el alcance de la jerarquía de almacenamiento a la que puede afectar una configuración.
El ámbito puede aplicarse a lo siguiente:

* Global: todos los sitios web, tiendas y vistas de tiendas
* Sitio web: el sitio web seleccionado y todas las tiendas y vistas de tienda que hay debajo de él.
* Tienda: la tienda seleccionada y todas las vistas de la tienda debajo de ella.
* Vista de tienda: la vista de tienda seleccionada.

Dentro de la jerarquía, la configuración aplicada en un nivel inferior puede anular algunos ajustes de nivel superior.

_Atributos de término:_

* _Campo: software de comercio_

### contrato de servicio

_noun_

Conjunto de interfaces PHP definidas para un módulo.
Un contrato de servicio incluye interfaces de datos, que conservan la integridad de los datos, e interfaces de servicio, que ocultan los detalles de la lógica empresarial de los solicitantes de servicios, como controladores, servicios web y otros módulos.
Las API web se pueden enlazar a contratos de servicio a través de archivos de configuración.

_Atributos de término:_

* _Campo: programación_
* _Términos relacionados: php, api web_

### liquidación

_noun_

La liquidación se produce cuando el banco adquirente y el emisor intercambian fondos y el producto se depositan en la cuenta del comerciante.

_Atributos de término:_

* _Campo: negocio_

### Catálogo compartido

_noun_

Característica que permite a los comerciantes crear un catálogo que pueda servir como catálogo completo o subconjunto de él y luego asignar precios personalizados para uno o más productos.
Los comerciantes pueden asignar este catálogo a una o más empresas.

Por ejemplo, un comerciante B2B tiene tres clientes que han negociado tarifas específicas para el sitio de distribución electrónica del comerciante.
Con la función de catálogo compartido, el comerciante tiene:

* Un catálogo principal
* Un catálogo cliente 1 (quizás son solo tres SKU con grandes descuentos en ellos del catálogo principal)
* Catálogo de Customer 2 (podría ser todo el catálogo con un 10% de descuento)
* Catálogo cliente 3 (unas decenas de productos con descuentos en el catálogo principal que van del 5% al 60%).

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: catálogo, b2b_

### envío

_noun_

Un envío contiene los productos que se van a entregar y genera un registro de los productos en un pedido que se han enviado.
Más de un envío se puede asociar a un único pedido.

_Atributos de término:_

* _Campo: negocio, pedido_

### documento de envío

_noun_

Documento que acompaña a un envío. El documento enumera los productos y sus cantidades en el paquete de entrega.

_Atributos de término:_

* _Campo: negocio, pedido_

### transportista marítimo

_noun_

Empresa que transporta paquetes. Los portadores comunes incluyen UPS, FedEx, DHL y USPS.

_Atributos de término:_

* _Campo: negocio, pedido_

### carro de compras

_noun_

Conjunto de productos que un cliente ha seleccionado adquirir, pero que aún no ha comprado.
También se refiere a un área de un sitio de comercio electrónico donde se puede encontrar estos productos para revisar y cerrar la compra.

_Atributos de término:_

* _Campo: negocio, diseño, producto, programación_
* _Sinónimos: carro de compras, cesta_
* _Términos relacionados: reglas del carro de compras_

### producto simple

_noun_

El tipo de producto más básico, un elemento físico con un único SKU.
Los productos simples tienen diversos controles de precios y de entrada que permiten vender variaciones del producto.
Los productos simples se pueden usar en asociación con productos agrupados, agrupados y configurables.
Un producto simple con opciones personalizadas a veces se denomina producto compuesto.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: tipos de producto_

### SKU

_noun_

Abreviación de la unidad de mantenimiento de existencias.
Número o código asignado a un producto para identificar el producto, las opciones, el precio y el fabricante.

_Atributos de término:_

* _Campo: negocio, precio, producto, programación_
* _Términos relacionados: catálogo compartido_

### página de inicio

_noun_

una página promocional con un producto o anuncio; normalmente se muestra antes de la página principal.

_Atributos de término:_

* _Campo: diseño_

### bloque estático

_noun_

Unidad modular de contenido que un usuario puede colocar en el CMS en una página para mostrar texto e imágenes, o ejecutar fragmentos de código.
Los bloques estáticos contienen contenido editable y pueden actuar como páginas de aterrizaje para categorías de productos.
Los widgets se pueden agregar a bloques estáticos para proporcionar funcionalidad adicional.

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: bloque cms, bloque_

### contenido estático

_noun_

Contenido generado por el usuario (no generado por código) que no cambia con frecuencia.

_Atributos de término:_

* _Campo: diseño_
* _Términos relacionados: contenido dinámico_

### archivos estáticos

_noun_

La colección de recursos, como CSS, fuentes, imágenes y JavaScript que utiliza un tema.

_Atributos de término:_

* _Campo: software de comercio_

### almacenar

_noun_

El nivel de ámbito de comercio de &quot;tienda&quot; es el segundo nivel de la jerarquía de su sitio web, que es el siguiente: sitio web > tienda > vista de tienda.
Las tiendas se pueden organizar en una o varias. Cada tienda, potencialmente, tiene su propia categoría raíz y todos comparten catálogo y datos de clientes.

Cada tienda puede tener varias vistas de la tienda, que normalmente se utilizan para presentar la tienda en una configuración regional y un idioma diferentes.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: vista de tienda, sitio web_

### vista de tienda

_noun_

El nivel de ámbito de comercio de la &quot;vista de tienda&quot; se refiere al tercer nivel de la jerarquía de sitios web, tiendas y vistas de tiendas.
Las vistas de la tienda suelen presentar la tienda en una configuración regional y un idioma diferentes.
Para cambiar las vistas de la tienda, utilice el selector de tiendas del encabezado.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: tienda, sitio web_

### storefront

_noun_

La tienda en línea que los clientes experimentan cuando visitan su sitio de comercio.

_Atributos de término:_

* _Campo: software de comercio, producto_

## T

### regla fiscal

_noun_

Combinación de una clase de impuesto del producto, clase de impuesto del cliente y tasa de impuesto. Esta regla define qué cálculo de impuestos se aplica.

_Atributos de término:_

* _Campo: negocio_

### plantilla

_noun_

Abreviatura para plantilla de HTML o plantilla PHTML.
Un archivo PHTML contiene una mezcla de código HTML y código PHP para insertar contenido dinámico en el HTML.
La mayoría de los bloques tienen al menos un archivo PHTML (plantilla) que contiene el HTML estático generado por el bloque .
En las plantillas de administración, correo electrónico y newsletter, se combinan texto, imágenes y variables con el marcado del HTML para producir contenido personalizado que envía el sistema.

_Atributos de término:_

* _Campo: software de comercio_
* _Términos relacionados: block_

### tema

_noun_

Contiene gráficos e información de aspecto.
Personaliza el aspecto de la tienda.
Adobe Commerce puede enviar temas en paquetes (Compositor).
Sin embargo, los temas pueden colocarse en la aplicación/diseño, que no se envía en un paquete.
Los paquetes son la unidad de descarga para Composer y, a través de Commerce Marketplace, los usuarios de comercio pueden descargar CE o EE como una serie de paquetes, donde los paquetes contienen módulos, temas o paquetes de idiomas.

_Atributos de término:_

* _Campo: software de comercio_

## U

### Componente de la interfaz de usuario

_noun_

Etiqueta diseñada para el software de Adobe Commerce que permite un procesamiento de interfaz de usuario (IU) más sencillo y flexible.
Los objetivos del sistema de componentes de la interfaz de usuario incluyen los siguientes:

* Simplificación de los archivos XML del controlador de diseño
* Mover los elementos de la interfaz de usuario del administrador de HTML+JavaScript a un sistema de widgets personalizado &quot;JavaScript puro&quot;
* Habilitar la creación de componentes de interfaz de usuario más complejos a partir de componentes más pequeños
* Procesamiento previo de datos para componentes de interfaz de usuario como JSON, enlace estrecho a objetos de datos del servidor
* Uso de AJAX para actualizar datos de componentes
* Presentación de un nuevo DSL para crear los elementos anteriores

Más información: [Guía de componentes de interfaz de usuario](https://developer.adobe.com/commerce/frontend-core/ui-components/), [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/introduction.html)

_Atributos de término:_

* _Campo: programación_
* _Términos relacionados: JavaScript, diseño, componente, creador de páginas_

### HACIA ARRIBA

_noun_

[PWA Studio](https://github.com/magento/pwa-studio) uses [HACIA ARRIBA](https://developer.adobe.com/commerce/pwa-studio/guides/packages/upward/) en desarrollo.
UPWARD es un acrónimo para la definición de respuesta progresiva de aplicaciones web unificadas.
Un archivo de definición UPWARD describe cómo un servidor web ofrece y admite un Progressive Web Application.

Los archivos de definición UPWARD proporcionan detalles sobre el comportamiento del servidor utilizando un lenguaje declarativo independiente de la plataforma.
Esto permite que un Progressive Web Application se ejecute sobre un servidor compatible con UPWARD en cualquier idioma en cualquier pila tecnológica porque la aplicación solo está preocupada por el comportamiento del extremo HTTP del servidor UPWARD.

Un servidor UPWARD utiliza un archivo de definición para determinar el proceso o servicio apropiado para una solicitud desde un shell de aplicación.
Describe cómo el servidor debe gestionar una solicitud y crear la respuesta para ella.

Un proyecto de PWA puede incluir un archivo de definición UPWARD para especificar sus dependencias de servicio.

_Atributos de término:_

* _Campo: diseño, software de comercio, programación_
* _Sinónimos: PWA Studio, definición de respuesta de aplicación web progresiva unificada_
* _Términos relacionados: pwa_

## V

### Extensión agrupada de proveedor

_noun_

El código producido por el proveedor que amplía o personaliza el comportamiento del comercio y funciona como una extensión de terceros se considera una extensión agrupada de proveedores (VBE).
Los VBE se prueban exhaustivamente y se incluyen en cada versión compatible de Magento Open Source y Adobe Commerce.
Un VBE puede incluir módulos, temas y paquetes de idiomas.

Obtenga más información en la [Tema de extensión agrupada de proveedor](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/modules/upgrade.html).

_Atributos de término:_

* _Campo: extensión de comercio, extensión agrupada de proveedor, extensión, VBE_
* _Sinónimos: extensión, VBE_
* _Términos relacionados: extensión, extensión agrupada_

### escala vertical

_noun_

El escalado vertical (escalado) se refiere al aumento de la potencia de procesamiento de un solo servidor o clúster mediante la adición de E/S de disco o red, CPUs o RAM.

_Atributos de término:_

* _Campo: entorno_

### producto virtual

_noun_

Representa un producto no físico que se puede vender, como un abono, un servicio, una garantía o una suscripción.
Los productos virtuales se pueden vender individualmente o incluir como parte de los siguientes tipos de productos: producto agrupado y producto agrupado.
No requiere envío ni inventario.

El proceso de crear un producto virtual y un producto simple es casi el mismo.
Sin embargo, como no se envía un producto virtual, no hay ningún campo de peso ni opción para incluir una tarjeta de regalo.

_Atributos de término:_

* _Campo: software de comercio, producto_
* _Términos relacionados: tipos de producto_

### tipo virtual

_noun_

Los tipos virtuales son una forma de insertar diferentes dependencias en clases PHP existentes sin afectar a otras clases y sin tener que crear un archivo de clase.
Solo se puede hacer referencia a los tipos virtuales mediante anulaciones de argumentos en una `<type>` dentro de archivos di.xml, nunca en código fuente.
No se pueden ampliar y no pueden ser referencias como dependencias en un constructor de clases.

_Atributos de término:_

* _Campo: programación_
* _Términos relacionados: php_

## W

### sitio web

_noun_

En el software Adobe Commerce, el nivel más alto de una jerarquía de sitios web, encima de la vista de tiendas y tiendas.
Puede tener varios sitios web, y cada sitio web puede tener un nombre de dominio diferente.
Los sitios web se pueden configurar para compartir datos de clientes o para no compartir datos.

_Atributos de término:_

* _Campo: software de comercio, diseño, producto_
* _Términos relacionados: almacenar, vista de tienda_

### widget

_noun_

A [widget](https://experienceleague.adobe.com/docs/commerce-admin/content-design/elements/widgets/widgets.html) es un fragmento de código preparado que se puede utilizar para colocar bloques, vínculos y contenido dinámico en ubicaciones específicas de las páginas de tienda.
Puede usar utilidades para crear páginas de aterrizaje para campañas de marketing y mostrar contenido promocional en ubicaciones específicas de toda la tienda.
Las utilidades también se pueden utilizar para agregar elementos interactivos y bloques de acción para sistemas de revisión externos, chats de vídeo, formularios de votación y suscripción, o para proporcionar elementos de navegación para nubes de etiquetas y controles deslizantes de imágenes.

_Atributos de término:_

* _Campo: negocio, software de comercio, diseño_
* _Términos relacionados: block_
