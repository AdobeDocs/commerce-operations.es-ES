---
title: "Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.55"
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.55.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 97b52220f3b254ee17705a22137693abc6008c72
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.55

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.55.

QPT v1.1.55 incluye los siguientes parches:

1. **ACSD-58383**: corrige el problema en el cual emitir un reembolso a través de [!DNL REST API] con dos solicitudes idénticas que se ejecutan simultáneamente, crea notas de crédito duplicadas.
1. **ACSD-58471**: corrige el problema por el que el contenido dinámico no se puede cargar en la página de detalles del producto cuando se programan las reglas de precios de catálogo asociadas.
1. **ACSD-58566**: corrige el problema en el que [!DNL GraphQL] devuelve un error interno del servidor al consultar el campo `created_at` en la mutación `addPurchaseOrderComment`.
1. **ACSD-58685**: corrige el problema por el cual los correos electrónicos de ventas iniciados mientras la comunicación por correo electrónico está deshabilitada se siguen enviando una vez que se vuelve a habilitar la comunicación por correo electrónico.
1. **ACSD-58735**: corrige un problema en el cual un administrador restringido no puede ver los carros de compras abandonados en la página de la cuenta del cliente en [!UICONTROL Admin] de un sitio web asociado.
1. **ACSD-58828**: corrige el problema en el que el mensaje de validación del lado del servidor *address is required* aparece si algún campo requerido queda vacío, junto con el mensaje de validación del lado del cliente. La validación del lado del servidor no mostrará el mensaje de los campos obligatorios vacíos y la validación del lado del cliente gestionará la notificación de error, indicando *Este es un campo obligatorio.*
1. **ACSD-60344**: corrige el problema por el que se envían correos electrónicos de confirmación de pedidos duplicados al usar **[!UICONTROL Purchase Order]** con aprobación automática.
1. **ACSD-61348**: corrige el problema en el cual los elementos de la lista de deseos son visibles a través de [!DNL GraphQL], pero no en la tienda en un entorno de varios sitios web.
1. **ACSD-61534**: corrige el problema en el que la configuración de diseño no se puede establecer con el comando `bin/magento config:set` y los valores bloqueados se pueden modificar mediante la manipulación de formularios. Ahora los valores bloqueados establecidos desde [!DNL CLI] con `--lock-env` o `--lock-conf` no se pueden actualizar.
1. **ACSD-61785**: corrige el problema en el cual no es posible actualizar el atributo `reward_warning_notification` mediante la mutación [!DNL GraphQL] y las llamadas [!DNL REST API], alineando su comportamiento con `reward_update_notification`.
1. **ACSD-62591**: corrige el problema en el cual el tema no cambia correctamente cuando se configuran los **[!UICONTROL User Agent Rules]**.
1. **ACSD-62793**: corrige el problema en el cual los atributos `datetime` de los datos exportados no incluyen el componente de tiempo. Además, si *[!UICONTROL Fields Enclosure]* está *habilitado*, los valores de atributo de la columna `additional_attributes` se escriben entre comillas dobles.
1. **ACSD-62332**: corrige el problema en el que la consulta de la lista de productos [!DNL GraphQL] está limitada a `total_count` de 10 000 productos. Además, corrige el problema en el cual [!DNL Live Search] establece la página actual en *1* en lugar de la página *2* en los criterios de búsqueda cuando se consulta a través de [!DNL GraphQL].

Utilice el menú de la izquierda para navegar a una página específica del parche.
