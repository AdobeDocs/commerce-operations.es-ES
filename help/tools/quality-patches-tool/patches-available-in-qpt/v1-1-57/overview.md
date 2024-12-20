---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.57'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.57.
feature: Tools and External Services
role: Admin, Developer
source-git-commit: 82b8d22438107680cdf47057e0db3e15bf819599
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.57

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.57.

QPT v1.1.57 incluye los siguientes parches:

1. **ACSD-57570**: corrige el problema en el cual un usuario administrador restringido con acceso a un almacén en particular no siempre puede ver todos los catálogos compartidos a los que están asignados los productos o puede ver clientes que no pueden guardar, lo que provoca incoherencias en el sistema.
1. **ACSD-58325**: corrige el problema en el que el botón [!UICONTROL Import] está disponible incluso después de un error de validación.
1. **ACSD-59083**: corrige el problema en el que algunas operaciones de actualización de la base de datos dan como resultado el error _No se encontró la tabla o vista base_ si la actualización [!DNL mview] se está ejecutando al mismo tiempo.
1. **ACSD-61622**: corrige el problema en el que faltan [!DNL FedEx] tasas específicas de cuenta en la respuesta. ACSD-61622 reemplaza la corrección documentada en [[!DNL FedEx] migración de la integración del método de envío de [!DNL SOAP] a [!DNL RESTful API]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/fedex-shipping-method-integration-migration-soap-restful-api).
1. **ACSD-61895**: corrige el problema en el que la consulta de categorías [!DNL GraphQL] devuelve categorías con el permiso *allow* aunque la categoría raíz no tenga el permiso *allow*.
1. **ACSD-62212**: corrige el problema en el cual el contenido del correo electrónico [!UICONTROL Forgot Password] no se traduce al idioma de la vista de tienda.
1. **ACSD-62481**: corrige el problema en el que el carro de compras del cliente queda vacío aunque [!UICONTROL Persistence] esté habilitado.
1. **ACSD-62629**: corrige el problema en el que una lista de productos usada en [!UICONTROL Widgets] no respeta la condición de categoría.
1. **ACSD-62635**: corrige el problema en el cual los productos relacionados con varias tiendas no se muestran correctamente en la consulta de productos de [!DNL GraphQL].
1. **ACSD-62671**: corrige el problema en el que la solicitud [!DNL GraphQL] no devuelve información de dirección actualizada en el primer intento.
1. **ACSD-62689**: corrige el problema en el cual el cliente no puede agregar categorías en [!UICONTROL Related Product Rules] y [!UICONTROL Widgets] después de la profundidad 4.
1. **ACSD-62708**: corrige el problema en el que [!DNL TinyMCE] 7 tamaño de fuente del editor en el administrador muestra [!UICONTROL px] y no [!UICONTROL pt] después de aplicar la corrección de [!UICONTROL ACP2E-3430]. Ahora, también puede establecer el tamaño de fuente en [!UICONTROL px] en lugar de [!UICONTROL pt].
1. **ACSD-62758**: corrige el problema por el que los vídeos de productos no se representan correctamente en la página de detalles de [!UICONTROL Configurable Product] si la dirección URL contiene opciones seleccionadas.
1. **ACSD-62951**: corrige el problema por el que se envía el correo electrónico [!UICONTROL Credit Memo] sin incluir los elementos ni los totales.
1. **ACSD-62965**: corrige el problema en el que un mensaje *LocalizedException* no se incluye en la ubicación de pedido [!DNL GraphQL response].
1. **ACSD-63286**: corrige el problema en el cual los productos asignados a un catálogo compartido a través de API no aparecen en la tienda hasta que se ejecute un reíndice manual.
1. **ACSD-63326**: corrige el problema por el cual el administrador es redirigido a una página rota después de realizar un pedido desde el servidor.


Utilice el menú de la izquierda para navegar a una página específica del parche.
