---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.72'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.72.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: a6a18a4cbab9d2e5a0c4824fc5ad9463f9e61c1c
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.72

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.72.

QPT v1.1.72 incluye los siguientes parches:
1. **ACSD-68040**: La página de búsqueda de front-end experimenta una degradación del rendimiento en [!DNL MariaDB] 10.6 y 11.4 con muchas solicitudes de búsqueda históricas.
1. **ACSD-67941**: Las solicitudes de GraphQL con nombres de filtro desconocidos provocan registros de excepciones de PHP.
1. **ACSD-68064**: al crear actualizaciones programadas, se generan entradas duplicadas en entornos con un número elevado de categorías anidadas.
1. **ACSD-66807**: la tabla `report_viewed_product_index` muestra un recuento incorrecto de vistas de página de productos.
1. **ACSD-67383**: el inicio de sesión como cliente con dos cuentas de administrador de empresa en la misma sesión provoca un error de *No existe esa entidad con cartId*.
1. **ACSD-67518**: los informes avanzados generan filas de encabezado duplicadas cuando el recuento de filas supera el tamaño del lote.
1. **ACSD-67639**: Error al crear un abono para productos agrupados con **[!UICONTROL Dynamic Price]** establecido en *No*.
1. **[ACSD-67696](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-72/acsd-67696.md)**: `media_gallery` entradas no se devuelven en el nodo de producto Cart GraphQL después de vaciar la caché.
1. **ACSD-67946**: las actualizaciones del carro de compras muestran titulares de error duplicados.
1. **ACSD-68011**: las SKU inexistentes se pueden asignar a un catálogo compartido mediante la API `/V1/sharedCatalog/:id/assignProducts` [!DNL REST].
1. **ACSD-68118**: `customerCart` La consulta de GraphQL devuelve valores de atributo de producto que no reflejan el encabezado del almacén, lo que provoca una localización incoherente.
1. **ACSD-68092**: Las opciones de paquete de productos se pierden después de varios guardados debido a una sincronización incorrecta entre las actualizaciones programadas y los datos de productos base.
1. **ACSD-67424**: el valor `updated_at` en la respuesta de la API `GET /carts/search` [!DNL REST] no coincide con el valor mostrado en **[!UICONTROL Admin panel]** al usar Ofertas negociables.
1. **ACSD-67187**: Los usuarios administradores restringidos a sitios web no predeterminados ven el error, *&quot;*Cree al menos un catálogo compartido público para continuar* y no puede acceder al botón **[!UICONTROL Add New Company]** en la cuadrícula de la compañía.

Utilice el menú de la izquierda para navegar a una página específica del parche.
