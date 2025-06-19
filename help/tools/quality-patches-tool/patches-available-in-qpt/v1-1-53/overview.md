---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.53'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.53.
feature: Tools and External Services
role: Admin, Developer
exl-id: 4e7c8d45-dc0c-4182-8cd0-727b28294d58
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.53

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.53.

QPT v1.1.53 incluye los siguientes parches:

1. **ACSD-48318**: corrige el problema en el que no se permite anidar la emulación del entorno. Ahora, la emulación se inicia durante la llamada de `send()` una vez que la emulación se detiene durante la llamada de `getInfoBlockHtml()`.
1. **ACSD-59930**: mejora el rendimiento de los flujos *[!UICONTROL Create]*, *[!UICONTROL Save]* y *[!UICONTROL Delete]* de la compañía.
1. **ACSD-60584**: corrige el problema en el cual un token de acceso creado para el usuario en un sitio web puede acceder o cambiar la información del cliente en otros sitios web.
1. **ACSD-60804**: corrige el problema en el que al editar un cliente vinculado a una compañía eliminada se produce el error *Llamada a una función de miembro `getSuperUserId()` en null*.
1. **ACSD-61133**: corrige el problema en el que el cron de `sales_clean_quotes` elimina las ofertas de pedidos de compra no aprobados.
1. **ACSD-61528**: corrige el problema en el cual al recuperar roles de [!UICONTROL Admin] mediante GraphQL no se obtienen resultados.
1. **ACSD-61553**: corrige el problema por el que los descuentos de *[!UICONTROL Cart Price Rule]* se calculan incorrectamente cuando se aplican al producto varios descuentos con diferentes prioridades y *[!UICONTROL Maximum Qty Discount is Applied To]*.
1. **ACSD-61667**: mejora el rendimiento del inventario para crear envíos en el caso de muchos orígenes con *recogida en tienda*.
1. **ACSD-61969**: corrige el problema en el que el usuario debe escribir un código de cupón que distingue entre mayúsculas y minúsculas y que coincida exactamente con el código de cupón configurado.

Utilice el menú de la izquierda para navegar a una página específica del parche.
