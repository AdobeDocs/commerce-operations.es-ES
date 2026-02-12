---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.76'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.76.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: aeda6ddd9bac7e5f81329d9bd05ab8957ef2fb76
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.76

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.76.

QPT v1.1.76 incluye los siguientes parches:
1. **ACSD-67091**: corrige el error de tamaño máximo del conjunto de escritura para garantizar la limpieza del índice de productos de la regla de catálogo mediante la implementación de dos estrategias de eliminación basadas en el volumen de datos.
1. **ACSD-67370**: corrige varios problemas en los que se mostraban precios incorrectos para productos en paquete en PDP/PLP y la página de carro de compras para tiendas en múltiples monedas.
1. **ACSD-68410**: corrige un problema en el cual al realizar un pedido de una oferta negociable se agregan o combinan incorrectamente líneas de carro de compras adicionales a la oferta. Los productos ahora se añaden correctamente al carro de compras después de dejar el último paso de cierre de compra de presupuesto negociable.
1. **ACSD-69086**: corrige el problema en el que el trabajo cron no borra las tablas changelog, lo que provoca [!DNL Galera Cluster] bloqueos al administrar grandes cantidades de datos.
1. **ACSD-69115**: corrige un problema en el cual los errores del carro de compras no se mostraban al usuario administrador al administrar el carro de compras para un cliente asignado a un sitio web no predeterminado.
1. **ACSD-69129**: corrige un problema en el cual al eliminar el sitio web base predeterminado y usar el sitio web secundario como predeterminado se produce un error al intentar actualizar el precio de nivel del sitio web secundario mediante la API [!DNL REST].
1. **ACSD-69203**: corrige un problema por el que el widget **[!UICONTROL Products List]** devuelve resultados incorrectos cuando se enumeraron varias categorías en la condición de categoría.
1. **ACSD-69261**: corrige un problema en el cual un cupón de regla de precio de carro de compras configurado para un solo uso por cliente se reutilizó varias veces debido a un manejo incorrecto del atributo `times_used` en los escenarios de cancelación de factura parcial y cantidad restante.
1. **ACSD-69308**: corrige un problema en el cual las reglas de precios de catálogo no se aplicaban cuando `special_price` se establecía solamente en el nivel de sitio web (no en **[!UICONTROL All Store Views]**). Después de la corrección, las reglas de precios de catálogo se aplican correctamente al comprobar primero la tienda predeterminada del sitio web.
1. **ACSD-69319**: corrige un problema en el que los precios de los paquetes no se indizaron correctamente cuando los productos secundarios tenían existencias de fuentes personalizadas.
1. **ACSD-69325**: corrige un problema en el cual al modificar el caso del SKU, el producto aparece sin existencias en la tienda.
1. **ACSD-69331**: corrige un problema en el cual los creadores de contenido de la galería de medios no podían crear carpetas con el permiso `create_folder` solamente. Después de la corrección, pueden crear carpetas según lo esperado.
1. **ACSD-69333**: corrige un problema en el cual se permitían cambios de SKU para productos con una actualización programada activa. Después de la corrección, los cambios de SKU están prohibidos durante las actualizaciones activas; los guardados fallan con un error de borrado y el campo SKU del administrador está desactivado. Esto evita MSI.
1. **ACSD-69541**: corrige un problema en el cual reducir la cantidad de un producto en el administrador a menos de lo que ya existe en un carro de compras hacía imposible editar la cantidad de productos en ese carro de compras a través de GraphQL.

Utilice el menú de la izquierda para navegar a una página específica del parche.
