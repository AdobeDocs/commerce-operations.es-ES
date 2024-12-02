---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.54'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.54.
feature: Tools and External Services
role: Admin, Developer
exl-id: 1496d15e-edf9-4be0-8e14-ebb2de6f12fe
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.54

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.54.

QPT v1.1.54 incluye los siguientes parches:

1. **ACSD-60267**: corrige el problema en el que el impuesto sobre productos fijos (FPT) se aplica correctamente al agregar productos simples con FPT directamente al carro de compras, pero falla al seleccionar estos productos mediante opciones de productos configurables.
1. **ACSD-61103**: corrige el problema en el cual el recuento de errores en la tabla `customer_entity` no se restablece a cero después de que un cliente inicie sesión correctamente a través de los extremos de API.
1. **ACSD-61134**: corrige el problema por el que el método de pago [!DNL Braintree Vault] se anula automáticamente de la selección en el flujo de trabajo de cierre de compra cuando un comprador actualiza su dirección de facturación anulando la selección de la casilla de verificación *[!UICONTROL My billing and shipping address are the same]*.
1. **ACSD-61199**: corrige el problema en el cual la pestaña de jerarquía de páginas de CMS no muestra una estructura de árbol adecuada al editar una página de CMS con una jerarquía existente.
1. **ACSD-61200**: corrige el problema en el que los cálculos de *[!UICONTROL Total Amount]* y *[!UICONTROL Total Amount Actual]* en ventas no contienen los valores *[!UICONTROL Discount Tax Compensation Amount]* y *[!UICONTROL Shipping Discount Tax Compensation Amount]*, lo que provoca discrepancias en los datos del pedido de ventas.
1. **ACSD-61522**: corrige el problema en el cual es posible ingresar direcciones de correo electrónico en los campos *[!UICONTROL First Name]* y *[!UICONTROL Last Name]* del cliente invitado y enviar correos electrónicos de confirmación de pedido no válidos.
1. **ACSD-61756**: mejora el rendimiento de `AdvancedSalesRule` filtros.
1. **ACSD-61799**: corrige el problema en el que el descuento total se calcula incorrectamente cuando se aplican varias reglas del carro de compras con descuentos fijos a la oferta.
1. **ACSD-61845**: corrige el error que se produce cuando se envía una solicitud con el encabezado de aceptación *text/html* solamente.
1. **ACSD-62056**: corrige el problema en el que la carga de imágenes para un producto configurable falla si MSI está instalado.
1. **ACSD-62485**: corrige el problema en el que el consumidor `async.operations.all` deja de funcionar cuando se crea una compañía.

Utilice el menú de la izquierda para navegar a una página específica del parche.
