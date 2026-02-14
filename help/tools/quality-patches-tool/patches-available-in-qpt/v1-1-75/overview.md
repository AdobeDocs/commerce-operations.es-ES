---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.75'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.75.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: f230c5fe7a2678f091dfff559c21bdb0d349b062
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.75

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.75.

QPT v1.1.75 incluye los siguientes parches:
1. **ACSD-68289**: corrige un problema en el cual la búsqueda de texto completo ahora devuelve productos coincidentes si la condición de coincidencia mínima se cumple en todos los campos en los que se puede buscar colectivamente, en lugar de requerir que la condición se cumpla en un solo campo.
1. **ACSD-68359**: corrige el error *414* al seleccionar **[!UICONTROL Pick in Store]** con carros de compras grandes.
1. **ACSD-68451**: corrige un problema en varios sitios web donde el administrador de una compañía inicia sesión en un sitio web, crea una compañía no relacionada en otro sitio web pero está vinculada erróneamente a esa compañía no relacionada.
1. **ACSD-68517**: corrige un error de reenvío de formulario en **[!UICONTROL Catalog]** y **[!UICONTROL Catalog Search]** páginas.
1. **ACSD-68490**: **[!UICONTROL Add New Attribute]** botón visible para el administrador restringido durante la creación de productos configurables.
1. **ACSD-68573**: los permisos de categoría no se aplicaron a los elementos de la lista de deseos del cliente, lo que provocó una visualización y paginación incorrectas en la tienda web y en [!DNL GraphQL].
1. **ACSD-68615**: corrige el problema en el que la CLI de compensación de reserva de inventario mostraba una excepción si la combinación procesada tenía un identificador de pedido que faltaba.
1. **ACSD-68793**: corrige un problema en el cual los productos válidos se rechazaban incorrectamente al asignarlos a un catálogo compartido.
1. **ACSD-68925**: corrige un problema en el cual las respuestas para solicitudes de GraphQL ahora están alineadas con las especificaciones de GraphQL sobre HTTP. Se devuelve un código de respuesta 4XX cuando la solicitud no se puede analizar, no está autorizada o encuentra un problema general si se analiza la solicitud.

Utilice el menú de la izquierda para navegar a una página específica del parche.
