---
title: "Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.25"
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.25.
feature: Tools and External Services
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Información general de [!DNL Quality Patches Tool] (QPT) v1.1.25

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.25.

QPT v1.1.25 incluye los siguientes parches:

1. **ACSD-47292**: corrige el problema en el cual los productos agrupados sin existencias no están disponibles en la respuesta de GraphQL si *mostrar productos sin existencias* está establecido en *Sí*.
1. **ACSD-47520**: corrige el problema en el cual los clientes pierden puntos de recompensa cuando se crea un abono.
1. **ACSD-47910**: corrige la emisión de pedidos, facturas, envíos y notas de abono que faltan en las cuadrículas de entidades respectivas.
1. **ACSD-48044**: soluciona el problema de que al aplicar varias tarjetas regalo a un único pedido con envío múltiple se impiden los pedidos.
1. **ACSD-48058**: corrige el problema en el que el reíndice de precios del producto no funciona si el producto del paquete no está asignado a ningún sitio web.
1. **ACSD-48234**: corrige el problema en el que el resultado de la búsqueda en el catálogo muestra un recuento incorrecto de elementos de categoría cuando la opción *mostrar sin existencias* está habilitada.
1. **ACSD-48262**: corrige el problema en el que los productos no son visibles en el front-end cuando la configuración de *[!UICONTROL Allow All Products Per Page]* está establecida en *Sí*.
1. **ACSD-48293**: corrige el problema por el que los productos compuestos se quedan sin existencias cuando los productos secundarios que se agotaron vuelven a estar en existencias.
1. **ACSD-48300**: corrige el problema en el que no se puede crear una devolución si se quita el producto configurable.
1. **ACSD-48313**: corrige el problema en el que la columna *configurable_variaciones* no se analiza si el valor del atributo contiene una coma. Se usa el mismo algoritmo de análisis para *additional_attributes*.
1. **ACSD-48627**: corrige el problema por el cual el producto configurable sin existencias causa un error al enviar una solicitud de GraphQL para obtener los detalles del carro de compras.

Utilice el menú de la izquierda para navegar a una página específica del parche.
