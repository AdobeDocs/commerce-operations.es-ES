---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.84'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.84.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%
---
# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.84

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.84.

QPT v1.1.84 incluye los siguientes parches:

1. **ACP2E-4913**: corrige el problema en el que las operaciones de envío y facturación fallan debido a un bloqueo.
1. **ACP2E-5005**: Corrige el problema en el que la cantidad de una opción de producto agrupado en una oferta negociable vuelve a su valor anterior cuando el producto agrupado se reconfigura en el Administrador y se edita la cantidad.
1. **ACP2E-5009**: corrige el problema en el cual la migración de datos de Magento Open Source a Adobe Commerce no migra correctamente los cambios de diseño programados de categoría y las actualizaciones programadas de producto **[!UICONTROL Special Price]**, lo que provoca que falten algunas actualizaciones programadas o se omitan durante la migración y mejora el rendimiento de la migración.
1. **ACP2E-5017**: corrige el problema en el cual al consultar el rol de cliente a través de GraphQL se devuelve un *error interno del servidor* cuando el cliente no está asignado a una compañía.
1. **ACP2E-5027**: corrige el problema en el que los indexadores permanecen atascados en un bucle y la reindexación no se completa cuando el bloqueo de archivos está habilitado.
1. **ACP2E-5029**: corrige el problema por el cual los cambios en las reglas de precios de catálogo no aparecen en **[!DNL Live Search]** hasta que se realice una resincronización manual.
1. **ACP2E-5041**: corrige el problema en el cual guardar un producto durante una actualización programada hace que la tienda muestre el precio normal en lugar de **[!UICONTROL Special Price]** después de que finalice la actualización.
1. **ACP2E-5059**: corrige el problema en el cual los clientes reciben correos electrónicos de confirmación de pedidos duplicados para el mismo pedido.
1. **ACP2E-5122**: corrige el problema en el que los errores administrados de las solicitudes de GraphQL para el carro de compras se registran incorrectamente en los registros de excepciones como errores de aplicación.
1. **ACP2E-5143**: corrige el problema en el que la consulta de ruta de GraphQL procesa contenido completo de páginas de CMS cuando solo se solicitan metadatos de enrutamiento, lo que aumenta las consultas de base de datos para páginas de CMS que contienen widgets de Page Builder.
1. **ACP2E-5183**: corrige el problema en el que la implementación de contenido estático falla en PHP 8.5 mientras compila un archivo `LESS` que usa la directiva `@magento_import`.
1. **ACP2E-5242**: corrige el problema en el cual al comprobar la disponibilidad del producto mientras se agregan elementos al carro de compras se muestra un error que indica que no se puede encontrar el sitio web.
1. **ACP2E-5263**: corrige el problema en el cual la exportación de productos a un archivo CSV puede detenerse antes de que se incluyan todos los productos, lo que da como resultado un archivo incompleto.
1. **ACP2E-5034**: corrige el problema en el que la administración de ofertas negociables restablece incorrectamente los totales a *cero* al recalcular una oferta después de seleccionar un método de envío, descarta las actualizaciones de las cantidades de opciones de productos agrupados realizadas mediante la acción **[!UICONTROL Configure]** en el administrador y no refleja correctamente los descuentos de nivel de artículo aplicados a los productos agrupados de precios dinámicos en los subtotales de ofertas.
1. **ACP2E-4741**: corrige el problema en el cual un producto desaparece de la tienda después de que se guarde un producto vinculado a él como [!UICONTROL Related Product], [!UICONTROL Up-Sell] o Venta cruzada mientras se están usando un origen y un stock no predeterminados.
1. **ACP2E-5079**: corrige el problema en el cual la evaluación de un segmento de clientes asignado a varios sitios web devuelve clientes coincidentes solo desde el primer sitio web cuando las cuentas de clientes se comparten globalmente.
1. **ACP2E-5127**: corrige el problema en el que al editar una cuenta de compañía en el panel de administración con una configuración regional no predeterminada, se restablece **[!UICONTROL Credit Limit]** a *cero*.
1. **AC-15494**: corrige el problema en el que la consulta de productos devuelve nombres de productos con caracteres especiales de escape de HTML en lugar de sus caracteres originales.

Utilice el menú de la izquierda para navegar a una página específica del parche.
