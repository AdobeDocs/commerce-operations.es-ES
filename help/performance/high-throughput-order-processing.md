---
title: Prácticas recomendadas de rendimiento de Checkout
description: Obtenga información sobre cómo optimizar el rendimiento de las experiencias de cierre de compra en el sitio de Adobe Commerce.
feature: Best Practices, Orders
exl-id: dc2d0399-0d7f-42d8-a6cf-ce126e0b052d
source-git-commit: e4c1832076bb81cd3e70ff279a6921ffb29ea631
workflow-type: tm+mt
source-wordcount: '1132'
ht-degree: 0%

---


# Prácticas recomendadas de rendimiento de Checkout

El [pago y envío](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/point-of-purchase/checkout/checkout-process) El proceso de en Adobe Commerce es un aspecto crítico de la experiencia de la tienda. Se basa en el integrado [carrito](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#shopping-cart) y [pago y envío](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront#checkout-page) funciones.

El rendimiento es clave para mantener una buena experiencia de usuario. Revise la [resumen de evaluación de rendimiento](../implementation-playbook/infrastructure/performance/benchmarks.md) para obtener más información sobre las expectativas de rendimiento. Puede optimizar el rendimiento del cierre de compra configurando las siguientes opciones para **procesamiento de pedidos de alto rendimiento**:

- [AsyncOrder](#asynchronous-order-placement): permite procesar pedidos de forma asíncrona mediante una cola.
- [Cálculo de total diferido](#deferred-total-calculation): permite aplazar los cálculos de totales de pedidos hasta que comience el cierre de compra.
- [Comprobación de inventario al cargar el carro](#disable-inventory-check): permite omitir la validación de inventario de los artículos del carro de compras.
- [Equilibrio de carga](#load-balancing): permite activar conexiones secundarias para la base de datos MySQL y la instancia de Redis.

Las opciones de configuración AsyncOrder, Cálculo de totales diferidos y Comprobación de inventario de carga de carro de compras funcionan de forma independiente. Puede utilizar las tres funciones simultáneamente o habilitar y deshabilitar las funciones en cualquier combinación.

>[!NOTE]
>
>No utilice código PHP personalizado para personalizar las capacidades integradas de carrito y pago. Además de los posibles problemas de rendimiento, el uso de código PHP personalizado puede resultar en actualizaciones complejas y desafíos de mantenimiento. Estos problemas aumentan el coste total de propiedad. Si la personalización del carrito y del checkout basada en PHP es inevitable, utilice [Adobe Commerce Marketplace](https://commercemarketplace.adobe.com/)Solo extensiones aprobadas por. Todas las extensiones de Marketplace están sujetas a [amplia revisión](https://developer.adobe.com/commerce/marketplace/guides/sellers/extension-quality-program/) para comprobar que cumplen los estándares de codificación y las prácticas recomendadas de Adobe Commerce.

## Colocación de pedido asincrónica

El _Orden asíncrono_ : este módulo habilita la colocación asincrónica de pedidos, que marca el pedido como `received`, coloca el pedido en cola y procesa los pedidos de la cola según el primer ingreso y el primer envío. AsyncOrder está **inhabilitado** de forma predeterminada.

Por ejemplo, un cliente agrega un producto al carro de compras y selecciona **[!UICONTROL Proceed to Checkout]**. Rellenan el **[!UICONTROL Shipping Address]** formulario, seleccione su preferido **[!UICONTROL Shipping Method]**, seleccione una forma de pago y realice el pedido. El carro de compras se borra, el pedido se marca como **[!UICONTROL Received]**, pero la cantidad del producto aún no se ha ajustado, ni se ha enviado un correo electrónico de ventas al cliente. El pedido se recibe, pero los detalles del pedido aún no están disponibles porque el pedido no se ha procesado completamente. Permanece en la cola hasta que `placeOrderProcess` El consumidor comienza, comprueba el pedido con la variable [comprobación de inventario](#disable-inventory-check) (activada de forma predeterminada) y actualiza el orden de la siguiente manera:

- **Producto disponible**: el estado del pedido cambia a _Pendiente_, se ajusta la cantidad del producto, se envía un correo electrónico con los detalles del pedido al cliente y los detalles del pedido correctos están disponibles para su visualización en la **Pedidos y devoluciones** lista con opciones procesables, como reordenar.
- **Producto agotado o con bajo suministro**: el estado del pedido cambia a _Rechazado_, la cantidad del producto no se ajusta, se envía un correo electrónico con detalles del pedido sobre el problema al cliente y los detalles del pedido rechazado están disponibles en la **Pedidos y devoluciones** lista sin opciones procesables.

Utilice la interfaz de la línea de comandos para habilitar estas funciones o editar la variable `app/etc/env.php` archivo según los archivos README correspondientes definidos en la variable [_Guía de referencia del módulo_](https://developer.adobe.com/commerce/php/module-reference/).

**Para habilitar AsyncOrder**:

Puede habilitar AsyncOrder mediante la interfaz de línea de comandos:

```bash
bin/magento setup:config:set --checkout-async 1
```

El `set` El comando escribe lo siguiente en `app/etc/env.php` archivo:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Consulte [AsyncOrder](https://developer.adobe.com/commerce/php/module-reference/module-async-order/) en el _Guía de referencia del módulo_.

**Para deshabilitar AsyncOrder**:

>[!WARNING]
>
>Antes de deshabilitar el módulo AsyncOrder, debe comprobar que _todo_ se han completado los procesos de pedido asincrónico.

Puede deshabilitar AsyncOrder mediante la interfaz de línea de comandos:

```bash
bin/magento setup:config:set --checkout-async 0
```

El `set` El comando escribe lo siguiente en `app/etc/env.php` archivo:

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### Compatibilidad con AsyncOrder

AsyncOrder admite un conjunto limitado de características de Adobe Commerce.

| Categoría | Función admitida |
|------------------|--------------------------------------------------------------------------|
| Tipos de desprotección | Cierre de compra de OnePage<br>Cierre de compra estándar<br>Cotización negociable B2B |
| Métodos de pago | Cheque/giro postal<br>Pago contra reembolso<br>Braintree<br>PayPal PayFlow Pro |
| Métodos de envío | Se admiten todos los métodos de envío. |

Las siguientes funciones son **no** compatible con AsyncOrder, pero sigue funcionando sincrónicamente:

- Métodos de pago no incluidos en la lista de funciones admitidas
- Cierre de compra de varias direcciones
- Creación de órdenes de administración

#### Compatibilidad con API web

Cuando el módulo AsyncOrder está habilitado, los siguientes extremos REST y mutaciones de GraphQL se ejecutan de forma asíncrona:

**REST:**

- [`POST /V1/carts/mine/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/cartsminepayment-information#operation/PostV1CartsMinePaymentinformation)
- [`POST /V1/guest-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/guest-cartscartIdpayment-information#operation/PostV1GuestcartsCartIdPaymentinformation)
- [`POST /V1/negotiable-carts/{cartId}/payment-information`](https://adobe-commerce.redoc.ly/2.4.7-admin/tag/negotiable-cartscartIdpayment-information#operation/PostV1NegotiablecartsCartIdPaymentinformation)

**GraphQL:**

- [`placeOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/place-order/)
- [`setPaymentMethodAndPlaceOrder`](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/set-payment-place-order/)

>[!INFO]
>
>GraphQL no admite la colocación asincrónica de pedidos de presupuesto negociables.

#### Exclusión de métodos de pago

Los desarrolladores pueden excluir explícitamente ciertos métodos de pago de la colocación asincrónica de pedidos añadiéndolos al `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` matriz. Los pedidos que utilizan métodos de pago excluidos se procesan sincrónicamente.

### Pedido asíncrono de oferta negociable

El _Pedido asíncrono de oferta negociable_ El módulo B2B permite guardar elementos de pedido de forma asíncrona para `NegotiableQuote` funcionalidad. Debe tener habilitados AsyncOrder y NegotiableQuote.

## Cálculo de total diferido

El _Cálculo de total diferido_ El módulo optimiza el proceso de cierre de compra al aplazar el cálculo total hasta que se solicite para el carro de compras o durante los pasos finales de cierre de compra. Cuando está habilitado, solo el subtotal se calcula cuando un cliente agrega productos al carro de compras.

El cálculo total diferido es **inhabilitado** de forma predeterminada. Utilice la interfaz de la línea de comandos para habilitar estas funciones o editar la variable `app/etc/env.php` archivo según los archivos README correspondientes definidos en la variable [_Guía de referencia del módulo_](https://developer.adobe.com/commerce/php/module-reference/).

**Para habilitar DeferredTotalCalculation**:

Puede habilitar DeferredTotalCalculation mediante la interfaz de línea de comandos:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

El `set` El comando escribe lo siguiente en `app/etc/env.php` archivo:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

**Para deshabilitar DeferredTotalCalculation**:

Puede deshabilitar DeferredTotalCalculation mediante la interfaz de línea de comandos:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

El `set` El comando escribe lo siguiente en `app/etc/env.php` archivo:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Consulte [DeferredTotalCalculating](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/) en el _Guía de referencia del módulo_.

### Impuesto de producto fijo

Cuando el cálculo del total diferido está habilitado, el impuesto sobre el producto fijo (FPT) no se incluye en el precio del producto y en el subtotal del carro de compras después de agregar el producto al carro de compras. El cálculo de FTP se difiere al agregar un producto al minicarrito. El FTP se muestra correctamente en el carro de compras después de pasar al cierre de compra final.

## Desactivar comprobación de inventario

El _Habilitar inventario al cargar el carro_ la configuración global determina si se debe realizar una comprobación de inventario al cargar un producto en el carro de compras. La desactivación del proceso de comprobación de inventario mejora el rendimiento de todos los pasos de cierre de compra, especialmente cuando se tratan productos a granel en el carro de compras.

Cuando está desactivada, la comprobación de inventario no se produce al añadir un producto al carro de compras. Si se omite esta comprobación de inventario, algunos escenarios sin existencias podrían generar otros tipos de errores. Una comprobación de inventario _siempre_ se produce en el paso de colocación del pedido, incluso cuando está desactivado.

**Habilitar comprobación de inventario al cargar el carro** está habilitado (establecido en Sí) de forma predeterminada. Para desactivar la comprobación de inventario al cargar el carro, establezca **[!UICONTROL Enable Inventory Check On Cart Load]** hasta `No` en la IU de administración **Tiendas** > **Configuración** > **Catálogo** > **Inventario** > **Opciones de Stock** sección. Consulte [Configurar opciones globales](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/configuration/global-options) y [Inventario de catálogo](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/guide-overview) en el _Guía del usuario_.

## Equilibrio de carga

Puede ayudar a equilibrar la carga entre los distintos nodos activando conexiones secundarias para la base de datos MySQL y la instancia de Redis.

Adobe Commerce puede leer varias bases de datos o instancias de Redis de forma asincrónica. Si utiliza Commerce en la infraestructura de la nube, puede configurar las conexiones secundarias editando el [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#mysql_use_slave_connection) y [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) valores en la `.magento.env.yaml` archivo. Solo un nodo debe gestionar el tráfico de lectura-escritura, por lo que las variables se deben configurar como `true` da como resultado la creación de una conexión secundaria para el tráfico de solo lectura. Establezca los valores en `false` para quitar cualquier matriz de conexión de solo lectura existente de `env.php` archivo.

Ejemplo de `.magento.env.yaml` archivo:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true
```
