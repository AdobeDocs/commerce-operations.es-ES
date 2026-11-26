---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.86'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.86.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 22769f702de10db88f28a5d4218a4f4c5d91cf0a
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%
---
# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.86

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.86.

QPT v1.1.86 incluye los siguientes parches:


1. **[ACP2E-5046](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5046.md)**: corrige el problema por el cual al actualizar la página mientras se crea un pedido en el administrador se agrega el mismo SKU varias veces.
1. **[ACP2E-3094](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-3094.md)**: corrige el problema en el cual ver o editar **[!UICONTROL Category Permissions]** para una categoría con muchos permisos puede hacer que el explorador no responda.
1. **[ACP2E-5050](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5050.md)**: soluciona el problema que impide que ver o guardar una RMA en el administrador muestre el número de RMA en el informe **[!UICONTROL Action Logs]**.
1. **ACP2E-5057**: corrige el problema en el que [!DNL GraphQL] consultas de productos de paquetes devuelven precios de opciones de paquetes globales en lugar de precios específicos de sitios web cuando **[!UICONTROL Catalog Price Scope]** está establecido en **[!UICONTROL Website]**.
1. **[ACP2E-5061](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5061.md)**: corrige el problema en el que una regla de comercialización de categoría no puede combinar condiciones AND con una condición que coincida con cualquiera de varios valores.
1. **ACP2E-5071**: corrige el problema en el que el mensaje de no disponibilidad de existencias no siempre se muestra en la página del producto cuando el carro de compras ya contiene la cantidad disponible completa.
1. **ACP2E-5094**: corrige el problema por el que las cargas de página son considerablemente más lentas cuando se establece una variable de entorno `MAGENTO_DC_*`.
1. **[ACP2E-5134](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5134.md)**: corrige el problema que causa que al eliminar un producto incluido en un paquete del catálogo compartido de una compañía, se deje el producto del paquete en el carro de compras y se produzca un error en el carro y durante el cierre de compra.
1. **[ACP2E-5118](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5118.md)**: corrige el problema en el que la vista previa de [!DNL Page Builder] no se procesa cuando la caché de **[!UICONTROL Translations]** está deshabilitada.
1. **ACP2E-5146**: corrige el problema en el cual un usuario administrador restringido a sitios web específicos no puede eliminar clientes cuando un cliente en otro sitio web tiene el mismo ID que el usuario administrador.
1. **ACP2E-5176**: corrige el problema por el que los eventos de comercio electrónico enviados a [!DNL Google Analytics 4] a través de [!DNL Google Tag Manager] utilizan el formato [!DNL Universal Analytics] y omiten varios eventos de cierre de compra.
1. **ACP2E-5185**: soluciona el problema por el cual al mover una categoría en el árbol de categorías se muestra el error `There was a category move error` o se tarda varios minutos en completarse cuando el almacén tiene muchas reescrituras de URL.
1. **ACP2E-4191**: corrige el problema en el cual ciertas solicitudes de API de REST entran en un bucle infinito cuando la caché de **[!UICONTROL EAV types and attributes]** está deshabilitada.
1. **[ACP2E-4973](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-4973.md)**: corrige el problema en el cual cambiar de Entrega en tienda a otro método de entrega no borra la dirección de tienda asociada del carro de compras.
1. **ACP2E-5221**: corrige el problema en el que el indizador **[!UICONTROL Catalog Product Permissions]** tarda mucho más cuando **[!UICONTROL Quick Order]** está habilitado en instalaciones con muchos almacenes y grupos de clientes.
1. **[ACP2E-5245](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-5245.md)**: soluciona el problema en el que un cliente recién registrado que usa la misma dirección para el envío y la facturación en su primer pedido ve esa dirección dos veces en la lista durante su siguiente cierre de compra.
1. **ACP2E-5248**: corrige el problema en el cual los usuarios administradores sin el permiso **[!UICONTROL Edit Product Status]** ven el error de obsolescencia `null as array offset` al abrir la página **[!UICONTROL Add Product]** en [!DNL PHP] 8.5.
1. **ACP2E-5254**: soluciona el problema en el que los productos agregados a una lista de solicitudes no aparecen cuando un cliente abre la lista hasta que se borra la caché.
1. **ACP2E-5268**: corrige el problema en el que se produce un error al crear un producto configurable cuando **[!UICONTROL Enable Frontend Resize]** está establecido en **[!UICONTROL No]**.
1. **[ACP2E-3752](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-86/acp2e-3752.md)**: corrige el problema por el que el procesamiento de importación de productos genera el error *Advertencia: clave de matriz indefinida &quot;apply_to&quot;* cuando se crean muchas operaciones de importación de productos.
1. **ACP2E-5280**: corrige el problema en el que los clientes encuentran un error al iniciar sesión mientras **[!UICONTROL Category Permissions]** está habilitado.
1. **ACP2E-5295**: corrige el problema en el que la reindexación de precios de productos paralelos falla con el error `Fail in child process` cuando se ejecuta después del indexador **[!UICONTROL Inventory]** en el mismo proceso.
1. **ACP2E-5298**: corrige el problema en el cual los usuarios administradores con acceso de solo vista a las reglas de precios del carro de compras pueden generar o eliminar códigos de cupones.
1. **ACP2E-5333**: corrige el problema que se produce cuando se actualiza un segmento de cliente con una condición **[!UICONTROL Total Number of Orders]** que usa el operador **[!UICONTROL is not]** y un valor de uno o más falla con el error `Unknown operator specified`.
1. **ACP2E-5425**: corrige el problema en el cual los clientes reciben correos electrónicos de confirmación de pedidos duplicados para el mismo pedido.

Utilice el menú de la izquierda para navegar a una página específica del parche.
