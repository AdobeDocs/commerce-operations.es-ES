---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.61'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.61.
feature: Tools and External Services
role: Admin, Developer
exl-id: 065235fb-12e3-448b-bc37-51efdf95393a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.61

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.61.

QPT v1.1.61 incluye los siguientes parches:

1. **ACP2E-3689**: corrige varios problemas con la visualización del árbol de categorías en niveles más profundos y reflejando relaciones de anclaje/no anclaje.
1. **ACP2E-3705**: corrige un problema en el que la ejecución de cron de `indexer_update_all_views` falla cuando se establece `MAGE_INDEXER_THREADS_COUNT`.
1. **ACSD-63883**: corrige el problema donde [!UICONTROL Requisition List] devuelve un `items_count` incorrecto en la respuesta [!DNL GraphQL].
1. **ACSD-63974**: corrige el problema en el que la página [!UICONTROL Requisition List] tarda demasiado en cargarse cuando hay demasiados elementos, al agregar una característica de paginación a la cuadrícula [!UICONTROL Requisition List] en la tienda, que muestra únicamente partes de registros que están limitados al número de registros por página, en lugar de todos los registros a la vez.
1. **ACSD-64178**: corrige el problema en el que la página de edición de [!UICONTROL Attribute Set] se carga lentamente si hay miles de atributos de producto.
1. **ACSD-64209**: corrige el problema en el que el programador cron recupera todas las ofertas negociables sin excluir las que tienen el estado **[!UICONTROL ordered]**, lo que provoca que se active un correo electrónico o correos electrónicos.
1. **ACSD-64431**: la mutación `placeOrder` que contiene la información del código de cupón en la solicitud ya no genera un error interno, sino que muestra que el pedido se realizó correctamente.
1. **ACSD-64467**: corrige el problema por el que el editor de WYSIWYG aparece vacío después de guardar una descripción de categoría en el nivel de vista de tienda.
1. **ACSD-64546**: corrige el problema en el que se produce un mensaje de error genérico en la interfaz de usuario y se almacena una excepción *Array to string conversion* en los registros durante la creación de etiquetas de envío UPS, lo que garantiza que el error real se muestre en la interfaz de usuario y que el mensaje de error correcto se almacene en los registros.
1. **ACSD-64684**: corrige el problema en el que se produce un error de validación al editar y guardar una tarjeta regalo con un valor mayor que *999* debido a la coma (separador de miles) en el número *mil (1,000)*.

Utilice el menú de la izquierda para navegar a una página específica del parche.
