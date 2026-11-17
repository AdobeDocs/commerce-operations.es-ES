---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.85'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.85.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 59431a80af552bd266da55fb49e489453cc64e71
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%
---
# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.85

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.85.

QPT v1.1.85 incluye los siguientes parches:

1. **ACP2E-4929**: corrige el problema por el que las etiquetas de atributo de la página **[!UICONTROL Compare Products]** muestran traducciones desde una vista de tienda diferente en lugar de la vista de tienda actual.
1. **ACP2E-5075**: corrige el problema en el que una regla de precio de carro de compras de cantidad fija con una condición de categoría aplicaba incorrectamente un descuento a todos los elementos secundarios de un paquete de precio dinámico cuando la regla coincidía únicamente con el producto principal del paquete.
1. **ACP2E-5077**: corrige el problema en el cual `customerCart` consultas de GraphQL simultáneas o `POST /V1/carts/mine` solicitudes de REST crean carros activos duplicados para clientes que aún no tienen un carro de compras activo.
1. **ACP2E-5088**: corrige el problema en el que se borra el carro de compras persistente de un cliente cuando caduca su sesión.
1. **ACP2E-3991**: corrige el problema donde la dirección IP del cliente no se determina correctamente.
1. **ACP2E-5092**: corrige el problema en el que la página **[!UICONTROL Company Profile]** y la página Admin Customer Edit muestran un error cuando una dirección de empresa guardada sin una región más adelante tiene una región agregada a su país.
1. **ACP2E-5124**: corrige el problema por el que el botón **[!UICONTROL Import]** permanece disponible en los resultados de validación después de que la validación falle cuando **[!UICONTROL Validation Strategy]** está establecido en **[!UICONTROL Stop on Error]**.
1. **AC-17456**: corrige el problema en el cual al editar el ámbito **[!UICONTROL Global]** en la página **[!UICONTROL Design Configuration]** en el Panel de administración se devuelve un error *HTTP 500* en PHP 8.4 y 8.5.
1. **ACP2E-5212**: corrige el problema en el que **[!UICONTROL Quick Order]** acepta archivos que no son CSV y que tienen el nombre de una extensión `.csv`.
1. **ACP2E-5300**: Corrige el problema por el que las búsquedas por palabra clave de varios números de pedido separados por espacios o por comas en la cuadrícula del Panel de administración **[!UICONTROL Orders]** no devuelven pedidos coincidentes.
1. **ACP2E-5354**: corrige el problema en el que al actualizar un cliente a través de la API de REST, un cliente asociado a una cuenta de compañía aparece varias veces en la cuadrícula de la administración **[!UICONTROL Customers]**.
1. **ACP2E-5208**: corrige el problema por el que la sección **[!UICONTROL Requisition List]** se vuelve a cargar en cada navegación de página de Storefront, incluso cuando no se han realizado cambios.

Utilice el menú de la izquierda para navegar a una página específica del parche.
