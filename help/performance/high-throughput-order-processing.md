---
title: Procesamiento de pedidos de alto rendimiento
description: Optimice la ubicación de los pedidos y la experiencia de cierre de compra para su implementación de Adobe Commerce o Magento Open Source.
source-git-commit: 0a902d7fe967bbcee5019fea83e5be66ce2aefd0
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 0%

---


# Procesamiento de pedidos de alto rendimiento

Puede optimizar la ubicación de pedidos y la experiencia de cierre de compra configurando el siguiente conjunto de módulos para **procesamiento de pedidos de alto rendimiento**:

- [AsyncOrder](#asynchronous-order-placement): procesa de forma asíncrona los pedidos mediante una cola.
- [NegociableCitaSincronizaciónPedido](#negotiable-quote-asyn-order)—Procesa asincrónicamente elementos de orden de guardado de cotizaciones.
- [Cálculo total diferido](#deferred-total-calculation): permite posponer los cálculos de totales de pedidos hasta que comienza el cierre de compra.

Todas las funciones funcionan de forma independiente. Puede usar todas las funciones simultáneamente o habilitar y deshabilitar las características en cualquier combinación.

Utilice la interfaz de la línea de comandos para habilitar estas funciones o edite la `app/etc/env.php` según los archivos README correspondientes definidos en el [_Guía de referencia de módulos_][mrg].

## Colocación de pedidos asincrónica

La variable _Orden asincrónico_ permite la colocación asincrónica de pedidos, que marca el orden como `received`, coloca el pedido en una cola y procesa los pedidos de la cola por primera vez. AsyncOrder es **disabled** de forma predeterminada.

Por ejemplo, un cliente agrega un producto al carro de compras y selecciona **[!UICONTROL Proceed to Checkout]**. Rellenan el **[!UICONTROL Shipping Address]** seleccione su **[!UICONTROL Shipping Method]**, seleccione un método de pago y realice el pedido. El carro de compras se borra, el pedido se marca como **[!UICONTROL Received]**, pero la cantidad del producto aún no se ha ajustado, ni se ha enviado un correo electrónico de ventas al cliente. El pedido se recibe, pero los detalles del pedido aún no están disponibles porque el pedido no se ha procesado por completo. Permanece en la cola hasta que `placeOrderProcess` el consumidor comienza, verifica el pedido con la variable [comprobación de inventario](#disable-inventory-check) (activada de forma predeterminada), y actualiza el orden de la siguiente manera:

- **Producto disponible**: el estado de pedido cambia a _Pendiente_, se ajusta la cantidad del producto, se envía un correo electrónico con los detalles del pedido al cliente y los detalles del pedido correctos quedan disponibles para su visualización en la **Pedidos y devoluciones** con opciones procesables, como reordenar.
- **Producto sin existencias o con poca oferta**: el estado de pedido cambia a _Rechazado_, la cantidad del producto no se ajusta, se envía un correo electrónico con los detalles del pedido sobre el problema al cliente y los detalles del pedido rechazado están disponibles en la **Pedidos y devoluciones** sin opciones procesables.

Para habilitar AsyncOrder:

Puede habilitar AsyncOrder mediante la interfaz de línea de comandos:

```bash
bin/magento setup:config:set --checkout-async 1
```

La variable `set` escribe lo siguiente en el `app/etc/env.php` archivo:

```conf
...
   'checkout' => [
       'async' => 1
   ]
```

Consulte [AsyncOrder] en el _Guía de referencia de módulos_.

Para desactivar AsyncOrder:

>[!WARNING]
>
>Antes de desactivar el módulo AsyncOrder, debe comprobar que _all_ se han completado los procesos de solicitud asincrónicos.

Puede deshabilitar AsyncOrder usando la interfaz de línea de comandos:

```bash
bin/magento setup:config:set --checkout-async 0
```

La variable `set` escribe lo siguiente en el `app/etc/env.php` archivo:

```conf
...
   'checkout' => [
       'async' => 0
   ]
```

### Compatibilidad con AsyncOrder

AsyncOrder admite un conjunto limitado de [!DNL Commerce] características.

| Categoría | Función compatible |
|---------------- | -----------------------|
| Tipos de cierre de compra | Cierre de compra de una página<br>Cierre de compra estándar<br>Oferta negociable B2B |
| Métodos de pago | Comprobación/Pedido de Dinero<br>Efectivo a la entrega<br>Braintree<br>PayPal PayFlow Pro |
| Métodos de envío | Se admiten todos los métodos de envío. |

Las siguientes funciones son **not** compatible con AsyncOrder, pero sigue funcionando sincrónicamente:

- Métodos de pago no incluidos en la lista de funciones admitidas
- Cierre de compra de varias direcciones
- Creación de orden de administración

#### Compatibilidad con API web

Cuando el módulo AsyncOrder está habilitado, los siguientes extremos REST y las mutaciones GraphQL se ejecutan de forma asíncrona:

**REST:**

- `POST /V1/carts/mine/payment-information`
- `POST /V1/guest-carts/:cartId/payment-information`
- `POST /V1/negotiable-carts/:cartId/payment-information`

**GraphQL:**

- [`placeOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/place-order.html)
- [`setPaymentMethodAndPlaceOrder`](https://devdocs.magento.com/guides/v2.4/graphql/mutations/set-payment-place-order.html)

>[!INFO]
>
>GraphQL no admite la colocación asíncrona de pedidos de cotización negociables.

#### Exclusión de los métodos de pago

Los desarrolladores pueden excluir explícitamente ciertos métodos de pago de la colocación de pedidos asincrónicos añadiéndolos al `Magento\AsyncOrder\Model\OrderManagement::paymentMethods` matriz. Los pedidos que utilizan métodos de pago excluidos se procesan sincrónicamente.

## Orden asincrónico de cotización negociable

La variable _Orden asincrónico de cotización negociable_ El módulo B2B le permite guardar los elementos de pedido asincrónicamente para el `NegotiableQuote` funcionalidad. Debe tener activados AsyncOrder y NegociableQuote.

## Cálculo total diferido

La variable _Cálculo total diferido_ optimiza el proceso de cierre de compra aplazando el cálculo total hasta que se solicite para el carro de compras o durante los pasos finales de cierre de compra. Cuando está habilitado, solo el subtotal se calcula a medida que un cliente agrega productos al carro de compras.

DeferredTotalCalculation es **disabled** de forma predeterminada.

Para habilitar DeferredTotalCalculation:

Puede habilitar DeferredTotalCalculation mediante la interfaz de línea de comandos:

```bash
bin/magento setup:config:set --deferred-total-calculating 1
```

La variable `set` escribe lo siguiente en el `app/etc/env.php` archivo:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 1
   ]
```

Para desactivar DeferredTotalCalculation:

Puede desactivar DeferredTotalCalculation mediante la interfaz de línea de comandos:

```bash
bin/magento setup:config:set --deferred-total-calculating 0
```

La variable `set` escribe lo siguiente en el `app/etc/env.php` archivo:

```conf
...
   'checkout' => [
       'deferred_total_calculating' => 0
   ]
```

Consulte [TotalDiferidoCalculando] en el _Guía de referencia de módulos_.

### Impuesto fijo del producto

Cuando se habilita DeferredTotalCalculation, el Impuesto fijo del producto (FPT) no se incluye en el subtotal del precio del producto y del carro de compras del minicarro después de agregar el producto al carro de compras. El cálculo de FPT se retrasa al agregar un producto al minicarro. El FTP se muestra correctamente en el carro de compras después de continuar con el cierre de compra final.

## Deshabilitar comprobación de inventario

La variable _Habilitar inventario al cargar el carro de compras_ la configuración global determina si se debe realizar una comprobación de inventario al cargar un producto en el carro de compras. Al desactivar el proceso de comprobación de inventario, mejora el rendimiento de todos los pasos de cierre de compra, especialmente cuando se trata de productos masivos en el carro de compras.

Cuando está desactivado, no se produce la comprobación de inventario al agregar un producto al carro de compras. Si se omite esta comprobación de inventario, algunos escenarios fuera de existencias podrían generar otros tipos de errores. Comprobación de inventario _always_ se produce en el paso de colocación del pedido, incluso cuando está desactivado.

Habilitar inventario al cargar el carro de compras es **enabled** de forma predeterminada.

Para desactivar la comprobación de inventario al cargar el carro de compras, establezca **[!UICONTROL Enable Inventory Check On Cart Load]** a `No` en la interfaz de usuario de administración. Consulte [Configurar opciones globales][global] y [Inventario de catálogo][inventory] en el _Guía del usuario_.

<!-- link definitions -->

[Apply patches]: https://devdocs.magento.com/cloud/project/project-patch.html
[global]: https://docs.magento.com/user-guide/catalog/inventory-options-global.html
[inventory]: https://docs.magento.com/user-guide/configuration/catalog/inventory.html
[Install extensions]: https://devdocs.magento.com/extensions/install/
[cloud-extensions]: https://devdocs.magento.com/cloud/howtos/install-components.html

[mrg]: https://devdocs.magento.com/guides/v2.4//mrg/intro.html
[AsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-async-order.html
[TotalDiferidoCalculando]: https://devdocs.magento.com/guides/v2.4/mrg/module-deferred-total-calculating.html
[NegotiableQuoteAsyncOrder]: https://devdocs.magento.com/guides/v2.4/mrg/module-negotiable-quote-async-order.html
