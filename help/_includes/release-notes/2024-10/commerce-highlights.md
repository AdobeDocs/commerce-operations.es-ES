---
source-git-commit: b30fe4ed4d910ac3a99d3bcf4ff94103bcbd1369
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 0%

---
# Aspectos destacados de la versión beta de octubre de 2024 de Adobe Commerce 2.4.7

## Características destacadas

Esta versión de Adobe Commerce incluye varias correcciones esenciales de seguridad y mejoras de plataforma.

### Seguridad

Las siguientes mejoras de seguridad de esta versión mejoran el cumplimiento de las prácticas recomendadas de seguridad más recientes:

>[!NOTE]
>
>Para obtener la información más reciente sobre la corrección de errores de seguridad, consulte [Boletín de seguridad del Adobe APSB24-73](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

<table style="table-layout-auto">
    <tbody>
        <tr>
            <td><strong>Configuración</strong></td>
            <td>Esta versión incorpora las siguientes mejoras en la configuración de seguridad:
              <ul>
                <li><strong>Rotación de clave de cifrado</strong>: Ya está disponible un nuevo comando de CLI para cambiar la clave de cifrado. Consulte el artículo de la <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/troubleshooting-encryption-key-rotation-cve-2024-34102">Solución de problemas con la rotación de clave de cifrado: CVE-2024-34102</a> Knowledge Base para obtener más información.<!-- AC-12589 --></li>
                <li><strong>Configuración de contraseña de un solo uso (OTP)</strong>: esta actualización es necesaria para resolver un error introducido por un <a href="https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/#new-system-configuration-validation-for-two-factor-authentication-otp_window-value">cambio incompatible con versiones anteriores</a> en 2.4.7. La descripción del campo <strong>[!UICONTROL OTP Window]</strong> ahora proporciona una explicación precisa de la configuración y el valor predeterminado se ha cambiado de <code>1</code> a <code>29</code>.<!-- AC-11762 --></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Plataforma

Las siguientes actualizaciones de la plataforma para esta versión garantizan que Adobe Commerce siga siendo una plataforma sólida y fiable, preparada para satisfacer las demandas de los entornos comerciales modernos:

<table style="table-layout-auto">
    <tbody>
        <tr>
            <td><strong>Base de datos</strong></td>
            <td>En consonancia con nuestra <a href="/help/release/lifecycle-policy.md">política de ciclo de vida de soporte</a>, Adobe Commerce ahora es compatible con las siguientes versiones de soporte a largo plazo (LTS) de las siguientes tecnologías de bases de datos:
              <ul>
                <li><strong>MariaDB 11.4 LTS</strong> <em>_(compatible hasta 2029)_</em>: La versión anterior (MariaDB 10.6) llega al final de su vida útil en 2026, por lo que esta actualización es esencial para mantener la integridad y el rendimiento del sistema. MariaDB 10.6 sigue siendo compatible, pero Adobe recomienda actualizar a MariaDB 11.4 al actualizar a Adobe Commerce 2.4.8.</li>
                <li><strong>MySQL 8.4 LTS</strong> <em>_(compatible hasta 2032)_</em>: La versión anterior (MySQL 8.0) llega al final de su vida útil en 2026, por lo que esta actualización es esencial para mantener la integridad y el rendimiento del sistema. MySQL 8.0 sigue siendo compatible, pero Adobe recomienda actualizar a MySQL 8.4 al actualizar a Adobe Commerce 2.4.8</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>PHP</strong></td>
            <td>Esta versión incluye las siguientes mejoras de PHP:
            <ul>
              <li><strong>PHP 8.1</strong>: Esta versión elimina la compatibilidad con PHP 8.1 para Adobe Commerce 2.4.8. Debe actualizar a PHP 8.3 antes de actualizar a Adobe Commerce 2.4.8.</li>
              <li><strong>PHP 8.2</strong>: Uno de los cambios significativos en PHP 8.2 implica la obsolescencia de pasar parámetros de función interna nulos a no admisibles. Esta versión aborda las funciones obsoletas de PHP 8.1 en los componentes principales de la plataforma y garantiza la compatibilidad con PHP 8.2.</li>
              <li><strong>PHPUnit 10</strong>: Esta versión soluciona varios problemas importantes, mejora la compatibilidad y garantiza que el marco de pruebas de Adobe Commerce se ajuste a los estándares más recientes del sector. El Adobe recomienda que todos los proveedores y clientes de Commerce Marketplace con personalizaciones comprueben que sus pruebas de unidad e integración se ejecuten en PHPUnit 10 en lugar de 9.</li>
            </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Componentes</strong></td>
            <td>Los siguientes <a href="/help/release/packages/adobe-commerce.md">componentes y dependencias</a> de terceros se actualizaron a las últimas versiones estables para mejorar la estabilidad y el rendimiento de la plataforma:
              <ul>
                <li>jquery/validate 1.20.x</li>
                <li>moment.js 2.30.1</li>
                <li>monólogo/monólogo 3.x</li>
                <li>monolog/Require.js 2.3.7</li>
                <li>TinyMCE 7.x</li>
                <li>wikimedia/less.php 5.x</li>
              </ul>
            </td>
        </tr>
        <tr>
            <td><strong>Buscar</strong></td>
            <td>Adobe Commerce ahora está optimizado para OpenSearch 2.x y ya no es compatible con Elasticsearch. Todos los módulos y clases de Elasticsearch 7 y 8 ya no se utilizan en la base de código. Adobe recomienda encarecidamente realizar la transición a OpenSearch para implementaciones de infraestructura tanto locales como en la nube a fin de garantizar una compatibilidad y un soporte continuos. Ver <a href="/help/upgrade/prepare/opensearch-migration.md">Migrando a OpenSearch</a>.
              <ul>
                <li>Las opciones de Elasticsearch 7 y Elasticsearch 8 ahora están etiquetadas como "(obsoleto)" en la configuración de administración.</li>
                <li>Cuando un usuario selecciona el Elasticsearch como motor de búsqueda en la configuración de administración, Commerce muestra una notificación que indica <em>"Este Adobe ya no admite la opción de motor de búsqueda. Se recomienda usar OpenSearch como motor de búsqueda en su lugar."</em></li>
              </ul>
            </td>
        </tr>
    </tbody>
</table>

### Rendimiento

Esta versión incluye las siguientes mejoras de rendimiento:

<table style="table-layout-auto">
    <tbody>
        <tr>
            <td><strong>Indexadores</strong></td>
            <td>El <a href="/help/implementation-playbook/best-practices/maintenance/indexer-configuration.md#set-indexers-to-update-on-schedule">modo de indizador</a> predeterminado para todos los indizadores es ahora [!UICONTROL **Update by Schedule**] al instalar una nueva versión de Adobe Commerce o al actualizar desde una versión anterior. El nuevo valor predeterminado garantiza que los indexadores estén en la configuración recomendada, lo que mejora el rendimiento del sistema y reduce los posibles problemas.</td>
        </tr>
    </tbody>
</table>

### Calidad

Esta versión incluye las siguientes mejoras de calidad:

<table style="table-layout-auto">
    <tbody>
        <tr>
           <td><strong>Inventario</strong></td>
           <td>El sistema ahora funciona sin la dependencia anteriormente oculta del catálogo introducida por InventoryIndexer, lo que garantiza que la creación del producto, el interruptor de modo de visualización, el cambio de estado de las existencias y otras funcionalidades relacionadas funcionen según lo esperado. Anteriormente, esta dependencia oculta provocaba incoherencias, ya que diferentes entidades se sincronizaban y el indexador utilizaba diferentes entidades.</td>
        </tr>
        <tr>
            <td><strong>Pedidos</strong></td>
            <td>Para minimizar la confusión, la etiqueta del botón [!UICONTROL **Submit Comment**] cambió a [!UICONTROL **Update**] en la página <a href="https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-processing#notes-for-this-order">detalle del pedido</a>.</td>
        </tr>
    </tbody>
</table>

### GraphQL

Esta versión incluye las siguientes mejoras de GraphQL:

<table style="table-layout-auto">
    <tbody>
        <tr>
           <td><strong>Mejoras generales</strong></td>
           <td>Esta versión de incluye las siguientes mejoras generales de la API de GraphQL:
             <ul>
               <li><!--LYNX-401--><strong>StoreConfig</strong>: se agregaron los campos <code>grouped_product_image</code> y <code>configurable_product_image</code> al tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-StoreConfig"><code>StoreConfig</code></a>.</li>
              <li><!--LYNX-387--><strong>CartItemPrices</strong>: se agregaron los siguientes campos nuevos al tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> para admitir la presentación precisa de precios y cálculos de descuento:
                <ul>
                  <li><code>original_item_price</code></li>
                  <li><code>original_row_total</code></li>
                  <li><code>row_total_including_catalog_discounts_only</code></li>
                </ul>
              </li>
              <li><!--LYNX-451--><strong>Precios del carro de compras</strong>: se ha agregado el campo <code>grand_total_excluding_tax</code> al tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartPrices"><code>CartPrices</code></a>, lo que proporciona un precio claro con impuestos incluidos.</li>
              <li><!--LYNX-542--><strong>mutación de updateCartItems</strong>: se ha actualizado la mutación <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-updateCartItems"><code>updateCartItems</code></a> para que devuelva respuestas correctas con detalles de error en lugar de excepciones. Asignación de errores mejorada para mejorar la claridad de las notificaciones a los usuarios.</li>
              <li><!--LYNX-522--><strong>recaptchaV3Config query</strong>: Presentó un campo <code>theme</code> a la consulta <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-recaptchaV3Config"><code>recaptchaV3Config</code></a>. Este campo le permite especificar el nombre de la temática que se utilizará para procesar el reCaptcha.</li>
              <li><!--LYNX-540--><strong>ProductInterface</strong>: se ha introducido un campo <code>quantity</code> en <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-ProductInterface"><code>ProductInterface</code></a> para proporcionar detalles de nivel de existencias. Muestra las existencias disponibles o nulas en función de la configuración de la administración.</li>
               <li><!--LYNX-460--><strong>Productos agrupados</strong>: Se corrigió la visualización de precios de los productos agrupados, lo que garantiza información precisa sobre precios y monedas.</li>
               <li><!--LYNX-547--><strong>Cantidad</strong>: mensajes refinados para notificaciones de cantidad insuficiente y no disponible.</li>
               <li><!--LYNX-541--><strong>Tipo InsuficienteStockError</strong>: se ha agregado un nuevo tipo <code>InsufficientStockError</code> para controlar los casos en los que los niveles de existencias son insuficientes. Se ha ajustado el esquema para admitir nuevos tipos de error, lo que mejora las capacidades de creación de informes de errores.</li>
               <li><!--LYNX-476--><strong>Importe de inventario</strong>: mensajes de error mejorados para incluir importes de inventario disponibles. Proporciona a los usuarios una perspectiva más clara de los niveles de stock durante las actualizaciones de pedidos.</li>
               <li><!--LYNX-377--><strong>Cantidad solicitada</strong>: Se agregó <code>not_available_message</code> a <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemInterface"><code>CartItemInterface</code></a>.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Administración de clientes</strong></td>
           <td>Esta versión incluye las siguientes mejoras en la administración de clientes:
             <ul>
               <li><!--LYNX-391--><strong>mutación generateCustomerToken</strong>: se ha refinado el control de errores en la mutación <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-generateCustomerToken"><code>generateCustomerToken</code></a> para proporcionar mensajes específicos para correos electrónicos no confirmados. Admite una mejor guía del usuario y una mejor resolución de errores.</li>
               <li><!--LYNX-390--><strong>mutación de resendConfirmationEmail</strong>: Se ha agregado una nueva mutación <code>resendConfirmationEmail</code> para reenviar confirmaciones de correo electrónico.</li>
             </ul>
           </td>
        </tr>
        <tr>
           <td><strong>Order Management</strong></td>
           <td>Esta versión incluye las siguientes mejoras en la administración de pedidos de los usuarios:
             <ul>
              <li><!--LYNX-470--><strong>Fecha del primer pedido</strong>: se agregó un nuevo campo <code>date_of_first_order</code> al tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrders"><code>CustomerOrders</code></a>.</li>
              <li><!--LYNX-468--><strong>OrderAddress</strong>: se ha ampliado el tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderAddress"><code>OrderAddress</code></a> para incluir atributos personalizados, lo que mejora la visibilidad de los detalles del pedido. Admite la visualización de información adicional en las páginas de confirmación de pedido.</li>
              <li><!--LYNX-458--><strong>consultas de guestOrder e guestOrderByToken</strong>: se han actualizado las consultas <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrder"><code>guestOrder</code></a> y <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#query-guestOrderByToken"><code>guestOrderByToken</code></a> para incluir atributos de dirección personalizados, lo que garantiza la información completa de la dirección de las nuevas cuentas.</li>
              <li><!--LYNX-450--><strong>Tipo CustomerOrder</strong>: se agregó el campo <code>is_virtual</code> al tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>, que admite la identificación de productos virtuales. Mejora el procesamiento de pedidos al distinguir productos virtuales de físicos.</li>
              <li><!--LYNX-449--><strong>orderItemPrices</strong>: se agregó un tipo <code>OrderItemPrices</code> similar a <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CartItemPrices"><code>CartItemPrices</code></a> a <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-OrderItemInterface"><code>OrderItemInterface</code></a> con varios campos nuevos para el precio.</li>
              <li><!--LYNX-448--><strong>Combinar pedidos de invitado</strong>: Se ha mejorado la funcionalidad de la API para combinar pedidos de invitado con cuentas de cliente basadas en la coincidencia de correo electrónico. Optimiza la gestión de pedidos para los clientes que regresan.</li>
              <li><!-- LYNX-523: --><strong>campo available_actions</strong>: se ha ampliado el tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a> para incluir un campo <code>available_actions</code> con el fin de mejorar la administración de pedidos. El campo "available_actions" se asigna a una enumeración que enumera las posibles acciones que se pueden realizar en el pedido.</li>
              <li><!-- LYNX-524 --><strong>Tipo CustomerOrder</strong>: Se agregó el campo <code>customer_info</code> al tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CustomerOrder"><code>CustomerOrder</code></a>. Este campo requiere y <code>OrderCustomerInfo</code>, que define los detalles del nombre del cliente.</li>
              <li><!--LYNX-519--><strong>Códigos de error para la cancelación del pedido</strong>: se agregaron códigos de error detallados al tipo <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#definition-CancelOrderOutput"><code>CancelOrderOutput</code></a>. Se ha mejorado la gestión de errores y los comentarios del usuario sobre los procesos de cancelación de pedidos.</li>
              <li><!--LYNX-515--><strong>Se habilitó a los usuarios invitados para crear devoluciones para pedidos</strong>: se ajustó la mutación <a href="https://developer.adobe.com/commerce/webapi/graphql-api/index.html#mutation-requestReturn"><code>requestReturn</code></a> para admitir devoluciones de pedidos invitados.</li>
              <li><!--LYNX-505--><strong>confirmCancelOrder mutation</strong>: se ha agregado una nueva mutación <code>confirmCancelOrder</code> para facilitar la cancelación de pedidos a los usuarios invitados.</li>
             </ul>
           </td>
        </tr>
    </tbody>
</table>
