---
title: "Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.50"
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.50.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.50

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.50.

QPT v1.1.50 incluye los siguientes parches:

1. **ACSD-59280**: corrige el problema donde se produce el error *Call to undefined method ReflectionUnionType::getName()* al instalar versiones 2.4.4-pX.
1. **ACSD-45049**: corrige el problema en el cual la configuración de atributos del cliente *[!UICONTROL Is required]* no funciona correctamente según el ámbito del sitio web en Administración.
1. **ACSD-46938**: corrige el problema con el rendimiento de la recreación de déclencheur de base de datos durante `setup:upgrade`.
1. **ACSD-48210**: corrige el problema en el cual al actualizar el atributo *[!UICONTROL website scope]* en una vista de almacén específica se anulan los valores de atributo en el ámbito global.
1. **ACSD-54887**: corrige el problema por el que se borra el carro de compras del cliente después de que la sesión del cliente haya caducado con *[!UICONTROL Persistent Shopping Cart]* habilitado.
1. **ACSD-58141**: corrige el problema en el cual `PHPSESSID` se regenera en solicitudes de POST en el área de tienda para un cliente que ha iniciado sesión si [!UICONTROL L2 Redis cache] está habilitado y el cliente se actualiza desde el administrador.
1. **ACSD-58352**: corrige el problema en el cual se devuelven etiquetas de atributo de retorno para la vista de almacén predeterminada mediante la API de GraphQL cuando se especifica una vista de almacén no predeterminada en el encabezado de la solicitud.
1. **ACSD-58442**: corrige el problema en el que los dispositivos con una anchura de *768px* se tratan como móviles, lo que provoca que el menú y el encabezado se carguen en una vista móvil en lugar de en el escritorio.
1. **ACSD-58790**: corrige la funcionalidad de *pellizco para zoom* en las imágenes de la página de detalles del producto en la vista móvil en [!DNL Chrome].
1. **ACSD-59036**: corrige una excepción que se produce al cargar precios de productos con límites inferior y superior iguales a *$0*.
1. **ACSD-59229**: corrige el problema por el que la información relacionada con el grupo de clientes se guarda en el segmento incorrecto debido al valor antiguo de [!UICONTROL X-Magento-Vary] en la solicitud.
1. **ACSD-59378**: corrige el problema en el cual las reescrituras de URL en el nivel de tienda se actualizan incorrectamente durante la importación.
1. **ACSD-59514**: corrige el problema en el que los formularios del área de administración con [!DNL Page Builder] lanzaban *[!DNL Page Builder]se representaban durante 5 segundos sin liberar bloqueos.Error* en la consola del explorador después de enviar el formulario y no se pueden guardar los cambios.
1. **ACSD-60303**: corrige el problema en el cual no se puede realizar un pedido del administrador si la minificación del HTML está habilitada.
1. **ACSD-60441**: corrige el problema con la actualización de clientes a través del punto de conexión `V1/customers REST API` al usar el token de acceso de integración generado desde el servidor.

Utilice el menú de la izquierda para navegar a una página específica del parche.
