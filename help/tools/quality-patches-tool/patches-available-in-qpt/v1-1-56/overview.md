---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.56'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.56.
feature: Tools and External Services
role: Admin, Developer
exl-id: 6433df73-b6df-4c88-93a4-12ac1e5080ea
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.56

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.56.

QPT v1.1.56 incluye los siguientes parches:

1. **ACSD-63244**: corrige los problemas en los que un error de JavaScript impide que [!DNL Google Maps] se represente correctamente y en los que hay muchos *TypeError no capturado: este._each no es un error de function* en la consola del panel [!UICONTROL Admin].
1. **ACSD-63242**: corrige el problema de la lentitud de la importación al agregar productos de catálogo con más de 10 000 entradas.
1. **ACSD-63062**: corrige el problema en el que se producen cálculos de descuento en el carro de compras incorrectos cuando se aplican varias reglas superpuestas.
1. **ACSD-62979**: corrige el problema en el cual el uso del [!UICONTROL Store ID] incorrecto en el encabezado de GraphQL causa un error grave de memoria.
1. **ACSD-62971**: corrige el problema en el que la importación de orígenes de existencias con valores no numéricos en la columna *[!UICONTROL Quantity]* da como resultado que *quantity* se establezca en *0*.
1. **ACSD-62872**: corrige el problema con la validación de atributos únicos en el que las actualizaciones de programación se validan incorrectamente.
1. **ACSD-62755**: corrige el problema en el que [!DNL TinyMCE] 7 requiere que el tamaño y la fuente se agreguen específicamente en la configuración de inicialización del editor.
1. **ACSD-62670**: corrige el problema por el que la exportación del informe [!UICONTROL Products Ordered] a CSV y XML devuelve un error.
1. **ACSD-62577**: corrige el problema con el rendimiento lento de las consultas de búsqueda de tienda al optimizar los índices de tabla y consulta.
1. **ACSD-62475**: corrige el problema por el que los productos [!UICONTROL Gift Card] se combinan incorrectamente en el carro de compras.
1. **ACSD-62428**: corrige el problema en el que `is_out_of_stock` se establece en un valor incorrecto en el índice de búsqueda en el catálogo cuando [!DNL SKU] no se establece como atributo en el que se puede buscar.
1. **ACSD-62355**: mejora el tiempo de carga de la página de edición de productos configurable cuando el producto configurable se basa en muchos atributos con muchos valores.
1. **ACSD-61805**: corrige el problema por el que los productos permanecen sin existencias en la tienda después de actualizar el estado de pedido pendiente a través de [!DNL REST API].
1. **ACSD-60811**: corrige el problema en el que la actualización del estado del pedido con un valor o comentario personalizado solo es posible si el estado actual es *[!UICONTROL Processing]* o *[!UICONTROL Fraud]*.
1. **ACSD-62952**: corrige el problema por el que la fecha [!UICONTROL Gift Registry] se muestra de forma inexacta en la tienda.
1. **ACSD-55339**: corrige el problema en el que un producto [!DNL SKU] que empieza por *0* (cero) quita *0*, lo que impide que se actualice la oferta.

Utilice el menú de la izquierda para navegar a una página específica del parche.
