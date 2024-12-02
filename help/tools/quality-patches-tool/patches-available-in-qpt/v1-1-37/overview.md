---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.37'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.37.
feature: Tools and External Services
role: Admin, Developer
exl-id: 92338019-d71c-4fe8-984f-879d551b418f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.37

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.37.

QPT v1.1.37 incluye los siguientes parches:

1. **ACSD-52613**: corrige el problema en el que las cachés y los índices se actualizan aunque la API de REST no haya realizado actualizaciones en `Inventory_source` elementos.
1. **ACSD-51884**: corrige el problema por el que la ruta de acceso a la caché de la imagen del producto se vuelve incorrecta después de ejecutar el comando de cambio de tamaño.
1. **ACSD-53628**: corrige el problema en el cual el informe de pedidos de ventas CSV muestra caracteres especiales incorrectos.
1. **ACSD-49843**: corrige el problema en el cual el vínculo de la descarga del producto no está disponible después de que el elemento pedido se factura automáticamente mediante el método de pago en línea con la configuración *[!UICONTROL Payment Action]* = *[!UICONTROL Sale]* habilitada.
1. **ACSD-53148**: corrige el problema en el cual dos solicitudes paralelas en GraphQL para agregar el mismo producto configurable al carro de compras generaban dos elementos independientes en el carro de compras con el mismo SKU de producto.
1. **ACSD-47054**: corrige el problema por el que el reíndice de vista previa ejecuta el reíndice de todas las tiendas, lo que provoca lentitud.
1. **ACSD-52606**: corrige el problema donde se muestra el mensaje de error *Su pedido no está listo para su recogida* cuando el usuario hace clic en **[!UICONTROL Notify Order is Ready for Pickup]**.
1. **ACSD-51574**: corrige el problema en el cual la imagen no se actualiza en el front-end después de reemplazarla con otra imagen con el mismo nombre.
1. **ACSD-53728**: corrige el problema por el que el indizador EAV del producto tarda más en completarse.
1. **ACSD-53979**: corrige el problema de JS que ocurre en la página principal si el mensaje de bienvenida contiene una comilla simple.
1. **ACSD-52143**: corrige el problema por el que las opciones personalizadas se eliminan después de importar el producto.
1. **ACSD-53750**: corrige el error *Conexión rota o conexión cerrada* durante el reíndice `catalog_product_price` de subprocesos múltiples.

Utilice el menú de la izquierda para navegar a una página específica del parche.
