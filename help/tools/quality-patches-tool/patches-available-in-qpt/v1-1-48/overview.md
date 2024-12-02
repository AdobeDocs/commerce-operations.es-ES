---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.48'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.48.
feature: Tools and External Services
role: Admin, Developer
exl-id: 250c88e9-1422-4af5-a0f0-32b15d9ab078
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.48

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.48.

QPT v1.1.48 incluye los siguientes parches:

1. **ACSD-55566**: corrige el problema en el que *[!UICONTROL mergeCart mutation]* falla con un *error interno del servidor* en la respuesta de GraphQL al combinar los carros de compras de origen y destino que tienen los mismos elementos agrupados.
1. **ACSD-56546**: corrige el problema en el cual los productos configurables y agrupados se muestran como *[!UICONTROL Out of Stock]* en la tienda cuando la configuración de *[!UICONTROL Display Out of Stock Product]* está deshabilitada.
1. **ACSD-56635**: corrige el problema en el que el cliente importado se duplica con la misma dirección de correo electrónico cuando se usa la importación con [!UICONTROL Account Sharing] establecido en *[!UICONTROL Global]*.
1. **ACSD-56741**: corrige el mensaje de error *Intentando obtener acceso al desplazamiento de la matriz en un valor de tipo null* que se muestra durante `setup:upgrade` cuando la base de datos contiene un déclencheur MySQL personalizado no relacionado con el mecanismo de indexación y [!DNL MView].
1. **ACSD-57315**: corrige el problema en el que se crea una nueva transacción en [!DNL PayPal Payflow Pro] cada vez que se hace clic en el botón **[!UICONTROL Fetch]** en la pantalla Ver transacción en [!UICONTROL Admin].
1. **ACSD-57337**: corrige el problema en el que un usuario administrador con restricciones de acceso a sitios web específicos puede ver compañías de todos los sitios web en la cuadrícula *[!UICONTROL Companies]*.
1. **ACSD-57394**: corrige la ordenación incorrecta de productos por varios campos de ordenación en GraphQL.
1. **ACSD-57565**: corrige el problema en el que el panel *[!UICONTROL Order]* muestra información de pedido incorrecta hasta que se actualiza el período de tiempo. El panel ahora muestra las estadísticas de pedido correctas en la primera carga.
1. **ACSD-57854**: corrige el problema en el que las solicitudes de GraphQL de productos devuelven categorías deshabilitadas en las agregaciones de categorías.
1. **ACSD-58008**: corrige el problema por el cual al actualizar una actualización programada se elimina la versión anterior del elemento ensayado si no se especifica una fecha de finalización.

Utilice el menú de la izquierda para navegar a una página específica del parche.
