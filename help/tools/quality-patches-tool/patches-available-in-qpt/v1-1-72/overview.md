---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.72'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.72.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 87f2d57e60ca74e2c90107a0d38517049802c89e
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.72

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.72.

QPT v1.1.72 incluye los siguientes parches:
1. **ACSD-68040**: la página de búsqueda de front-end ralentiza [!DNL MariaDB] 10.6 con un historial grande.
1. **ACSD-67941**: Las solicitudes de GraphQL con nombres de filtro desconocidos provocan registros de excepciones de PHP.
1. **ACSD-68064**: al crear actualizaciones programadas, se generan entradas duplicadas en entornos con un número elevado de categorías anidadas.
1. **ACSD-66807**: la tabla `report_viewed_product_index` muestra un recuento incorrecto de vistas de página de productos.
1. **ACSD-67383**: el inicio de sesión como cliente con dos cuentas de administrador de empresa en la misma sesión provoca un error de *No existe esa entidad con cartId*.
1. **ACSD-67518**: los informes avanzados generan filas de encabezado duplicadas cuando el recuento de filas supera el tamaño del lote.
1. **ACSD-67639**: Error al crear un abono para productos agrupados con **[!UICONTROL Dynamic Price]** establecido en *No*.
1. **ACSD-67946**: la actualización del carro de compras muestra titulares de error duplicados.
1. **[ACSD-67696](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-72/acsd-67696.md)**: `media_gallery` entradas no se devuelven en el nodo de producto Cart GraphQL después de vaciar la caché.
1. **ACSD-67946**: las actualizaciones del carro de compras muestran titulares de error duplicados.
1. **ACSD-68011**: SKU no existentes asignadas al catálogo compartido mediante la API /V1/sharedCatalog/:id/assignProducts.
1. **ACSD-68118**: la consulta `customerCart` [!DNL GraphQL] devuelve valores de atributo de producto incorrectos para la vista de tienda.
1. **ACSD-68092**: Las opciones de paquete de productos se pierden después de varios guardados debido a una sincronización incorrecta entre las actualizaciones programadas y los datos de productos base.
1. **ACSD-67424**: el valor `updated_at` en la respuesta de la API `GET /carts/search` [!DNL REST] no coincide con el valor mostrado en **[!UICONTROL Admin panel]** al usar Ofertas negociables.
1. **ACSD-67187**: Los usuarios administradores restringidos a sitios web no predeterminados ven el error, *&quot;*Cree al menos un catálogo compartido público para continuar* y no puede acceder al botón **[!UICONTROL Add New Company]** en la cuadrícula de la compañía.

Utilice el menú de la izquierda para navegar a una página específica del parche.
