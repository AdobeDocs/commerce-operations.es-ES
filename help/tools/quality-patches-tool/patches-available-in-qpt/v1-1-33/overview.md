---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.33'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.33.
feature: Tools and External Services
role: Admin
exl-id: 31812668-1d24-4da6-992f-981c259e00da
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.33

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.33.

QPT v1.1.33 incluye los siguientes parches:

1. **ACSD-50478**: corrige el comando de reversión de base de datos para un caso en el que el volcado de base de datos contiene déclencheur y un comando SQL delimitador.
1. **ACSD-50512**: corrige el error: *El vínculo descargable no está relacionado con el producto. Compruebe el vínculo e inténtelo de nuevo.* que sucede al actualizar la fecha de inicio de una actualización descargable del ensayo de un producto.
1. **ACSD-50949**: corrige el problema en el que el filtro de precio de [!UICONTROL Advanced Search] no devuelve los resultados correctos cuando se usa junto con el filtro SKU.
1. **ACSD-51645**: corrige el error producido al guardar un nuevo [!UICONTROL Cart Price Rule] si la extensión `Magento_OfflineShipping` está deshabilitada.
1. **ACSD-50895**: corrige el problema en el que [!DNL Google Analytics] 3 etiquetas GTM no se activan si [!DNL Google Analytics] 4 GTM no está configurada.
1. **ACSD-51102**: corrige el problema en el cual una regla de catálogo que se aplica a un gran número de productos no se indiza correctamente cuando una actualización programada habilita la regla.
1. **ACSD-50368**: corrige el problema en el cual `group_id` del cliente se omite cuando se crea un cliente mediante la API de REST asincrónica o la API de REST asincrónica en bloque.
1. **ACSD-51497**: corrige el problema en el cual un cliente no puede ordenar una página de catálogo por [!UICONTROL Custom Attribute] del tipo desplegable.
1. **ACSD-51408**: corrige el problema en el que el estado del elemento de pedido se establece incorrectamente en [!UICONTROL Backordered].
1. **ACSD-51735**: corrige el problema en el que el estado del elemento de pedido se establece incorrectamente en [!UICONTROL Ordered] cuando el stock del producto es *0*.
1. **ACSD-51792**: corrige el problema en el cual una página no tiene el evento de impresión cuando [!DNL Google Tag Manager] 4 está habilitado.
1. **ACSD-51471**: corrige el problema en el cual un usuario administrador no puede guardar una actualización programada para un producto agrupado que usa un producto simple que tiene una actualización programada.
1. **ACSD-51700**: corrige el error que se produce al cambiar de vista de tienda en una página de edición de producto descargable en el administrador.
1. **ACSD-51120**: corrige el problema en el cual la caché de las solicitudes de GET de GraphQL no se borra para las páginas de CMS que contienen bloques de CMS que se actualizan mediante una actualización de ensayo.
1. **ACSD-51240**: corrige el problema en el que falta el archivo cargado si el registro se realiza mediante el formulario de registro de empresa.
1. **ACSD-51907**: corrige el problema por el que un usuario administrador restringido no puede crear un abono con un reembolso sin conexión.
1. **ACSD-52148**: corrige el problema donde el inicio de sesión de [!UICONTROL Google V3 reCAPTCHA Admin] falla ocasionalmente.
1. **ACSD-51431**: corrige el problema en el que el estado de un indizador está funcionando aunque no haya nuevas entradas en el registro de cambios.
1. **ACSD-51892**: corrige el problema de rendimiento donde los archivos de configuración se cargan varias veces durante la implementación.

Utilice el menú de la izquierda para navegar a una página específica del parche.
