---
title: "Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.40"
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.40.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.40

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.40.

QPT v1.1.40 incluye los siguientes parches:

1. **ACSD-54680**: corrige el problema en el cual no es posible procesar una cotización B2B enviada para un producto con varios orígenes asignados.
1. **ACSD-54040**: corrige el problema en el que el campo *[!UICONTROL Created]* está en blanco para obtener detalles del pedido cuando los módulos B2B están habilitados.
1. **ACSD-54319**: corrige el problema donde el precio del producto muestra cero en el informe *[!UICONTROL Product in Cart]*.
1. **ACSD-53378**: mejora el tiempo de carga de la página de cierre de compra para los clientes que tienen libretas de direcciones grandes.
1. **ACSD-52657**: corrige el problema por el que la minicart no se actualiza en la vista de tienda secundaria, que usa un subdominio.
1. **ACSD-53414**: corrige el problema en el cual un usuario administrador restringido puede ver páginas de CMS fuera de su ámbito de permisos.
1. **ACSD-54472**: corrige el problema en el que los clientes de una compañía rechazada pueden seguir autenticándose y los clientes de una compañía bloqueada y rechazada pueden seguir realizando pedidos. El parche agrega una validación adicional para los extremos de GraphQL.
1. **ACSD-52801**: Agrega la opción de hacer una coincidencia parcial al buscar productos en GraphQL.
1. **ACSD-55004**: corrige el problema en el que el validador se bloquea al cargar un archivo de importación mayor que el valor configurado en `php.ini`.
1. **ACSD-54989**: corrige el problema en el cual un administrador de una compañía no puede realizar un pedido cuando *[!UICONTROL Enable Purchase Orders]* está establecido en *[!UICONTROL Yes]* y *[!UICONTROL Purchase Order]* está establecido en *[!UICONTROL No]*.
1. **ACSD-54007**: corrige el error *&quot;Undefined array key &quot;_scope&quot;&quot;* en la importación de datos de clientes.
1. **ACSD-55031**: corrige el error *Type &quot;mixed&quot; no puede ser nullable* durante la compilación.
1. **ACSD-54961**: corrige el problema en el que un usuario administrador restringido no puede actualizar de forma masiva el estado de *Revisión del producto*.

Utilice el menú de la izquierda para navegar a una página específica del parche.
