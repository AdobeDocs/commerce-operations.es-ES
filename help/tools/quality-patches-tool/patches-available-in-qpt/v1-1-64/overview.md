---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.64'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.64.
feature: Tools and External Services
role: Admin, Developer
exl-id: e86b8557-a14a-40e2-a181-56efa4383a1c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.64

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.64.

QPT v1.1.64 incluye los siguientes parches:

1. **ACP2E-3838**: corrige el problema en el que [!DNL Page Builder] errores CORS impiden guardar cambios en el panel de administración en el modo de producción.
1. **ACP2E-3841**: corrige el problema en el cual las reglas de precios de carrito para productos de envío múltiple no se aplican correctamente cuando se utilizan las condiciones `subselect` y **[!UICONTROL Free Shipping]** está habilitado.
1. **ACSD-63139**: corrige el problema en el que la exportación del producto falla cuando los atributos del producto contienen miles de valores de opción.
1. **ACSD-65100**: corrige el problema en el cual al eliminar los valores de **[!UICONTROL Maximum Width]** y **[!UICONTROL Maximum Height]** en la configuración de **[!UICONTROL Media Gallery Image Optimization]** se produce un error durante el proceso de optimización de imágenes.
1. **ACSD-65127**: corrige el problema en el cual al habilitar la minificación de JavaScript en el modo de producción, [!DNL TinyMCE] 6 genera errores en la consola del explorador, lo que afecta a la funcionalidad y la experiencia del usuario.
1. **ACSD-65787**: corrige el problema en el que la clase `SchemaBuilder` se bloquea durante la creación o las actualizaciones de esquemas debido a una clave de matriz no definida *column* al procesar los datos de tabla.
1. **ACSD-65223**: corrige el problema en el cual los términos y acuerdos seleccionados manualmente para [!DNL B2B] pedidos de compra generan un error.
1. **ACSD-65540**: corrige el problema en el que se produce un error de sintaxis SQL debido a la ausencia de la función `REGEXP_LIKE` al actualizar la tabla `company_structure`.
1. **ACSD-65684**: corrige el problema de rendimiento por el que la actualización del módulo `Magento_Company` después de actualizar a [!DNL B2B] 1.5.2 tardó demasiado tiempo al procesar un gran número de registros (~100.000+) en la tabla `company_structure`.

Utilice el menú de la izquierda para navegar a una página específica del parche.
