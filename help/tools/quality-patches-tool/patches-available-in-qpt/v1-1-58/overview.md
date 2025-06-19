---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.58'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.58.
feature: Tools and External Services
role: Admin, Developer
exl-id: 61bf8b82-f897-41f6-8524-5aa74c6440f1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.58

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.58.

QPT v1.1.58 incluye los siguientes parches:

1. **ACSD-48570**: corrige el problema en el que no se podía acceder a la página de restablecimiento de contraseña haciendo clic en el vínculo de restablecimiento de contraseña de [!UICONTROL Admin] cuando **Agregar código de tienda a las direcciones URL** estaba *habilitado*, lo que anteriormente provocaba que se mostrara la página de inicio de sesión o una página 404.
1. **ACSD-62118**: corrige el problema en el que la tabla `sales_order_tax_item` no se actualiza completamente cuando se realizan [!DNL B2B] pedidos mediante el método de orden de compra.
1. **ACSD-63067**: corrige el problema en el que todas las cantidades de productos se resaltan incorrectamente y se muestra el mensaje *[!DNL Please specify the quantity of product(s).]* para todos los productos de un producto agrupado cuando solo una cantidad es incorrecta.
1. **ACSD-63090**: corrige el problema por el que los elementos del carro de compras se eliminan cuando se elimina un producto, después de agregarlo al carro de compras.
1. **ACSD-63182**: corrige el problema en el que se produce un error al guardar un producto de paquete duplicado con **[!DNL MSI]** *habilitado*.
1. **ACSD-63283**: corrige el problema que causa una excepción al ordenar elementos del registro de regalos y en el que las actualizaciones del registro de regalos incluyen elementos que no pertenecen al registro.
1. **ACSD-63299**: corrige el problema por el que el precio especial de un producto configurable no se muestra en la tienda.
1. **ACSD-63325**: corrige el problema en el que se produce un error `Syntax Error: Unexpected <EOF>` al enviar una solicitud [!DNL GraphQL] vacía.
1. **ACSD-63329**: corrige el problema en el que los valores predeterminados de los atributos con **[!UICONTROL Date]** o **[!UICONTROL Date and Time]** tipos de entrada no se establecen al crear productos mediante [!DNL REST API].
1. **ACSD-63572**: corrige el problema en el que las tablas temporales del indizador `CatalogRule` no se limpian si finaliza el proceso del indizador.
1. **ACSD-63578**: corrige el problema en el cual al hacer clic en el botón **[!UICONTROL Delete]** en **[!UICONTROL Add to Order by SKU]** en [!UICONTROL Admin] no se quita [!DNL SKU].

Utilice el menú de la izquierda para navegar a una página específica del parche.
