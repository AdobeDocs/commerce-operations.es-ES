---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.85'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.85.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-11-18T22:14:27.542Z'
TQID: 'https://experienceleague.adobe.com/OmF7Ctss9khE5ONHNnfea0dTaN-1-wGTH-EN-gx5jvo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
source-git-commit: a1cc81ee1a8d0bbcbea322558da75a31e65d66a4
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%
---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.85

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.85.

QPT v1.1.85 incluye los siguientes parches:

1. **[ACP2E-4929](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-85/acp2e-4929.md)**: corrige el problema por el que las etiquetas de atributos de la página Comparar productos muestran traducciones de una vista de tienda diferente en lugar de la vista de tienda actual.
1. **ACP2E-5075**: corrige el problema en el que una regla de precio de carro de compras de cantidad fija con una condición de categoría aplicaba incorrectamente un descuento a todos los elementos secundarios de un paquete de precio dinámico cuando la regla coincidía únicamente con el producto principal del paquete.
1. **ACP2E-5077**: corrige el problema en el cual `customerCart` consultas de GraphQL simultáneas o `POST /V1/carts/mine` solicitudes de REST crean carros activos duplicados para clientes que aún no tienen un carro de compras activo.
1. **ACP2E-5088**: corrige el problema en el que se borra el carro de compras persistente de un cliente cuando caduca su sesión.
1. **[ACP2E-3991](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-85/acp2e-3991.md)**: corrige el problema donde la dirección IP del cliente no se determina correctamente.
1. **ACP2E-5092**: corrige el problema en el que la página **[!UICONTROL Company Profile]** y la página Admin Customer Edit muestran un error cuando una dirección de empresa guardada sin una región más adelante tiene una región agregada a su país.
1. **ACP2E-5124**: corrige el problema por el que el botón **[!UICONTROL Import]** permanece disponible en los resultados de validación después de que la validación falle cuando **[!UICONTROL Validation Strategy]** está establecido en **[!UICONTROL Stop on Error]**.
1. **AC-17456**: corrige el problema en el cual al editar el ámbito **[!UICONTROL Global]** en la página **[!UICONTROL Design Configuration]** en el Panel de administración se devuelve un error *HTTP 500* en PHP 8.4 y 8.5.
1. **ACP2E-5212**: corrige el problema en el que **[!UICONTROL Quick Order]** acepta archivos que no son CSV y que tienen el nombre de una extensión `.csv`.
1. **ACP2E-5300**: Corrige el problema por el que las búsquedas por palabra clave de varios números de pedido separados por espacios o por comas en la cuadrícula del Panel de administración **[!UICONTROL Orders]** no devuelven pedidos coincidentes.
1. **ACP2E-5354**: corrige el problema en el que al actualizar un cliente a través de la API de REST, un cliente asociado a una cuenta de compañía aparece varias veces en la cuadrícula de la administración **[!UICONTROL Customers]**.
1. **ACP2E-5208**: corrige el problema por el que la sección **[!UICONTROL Requisition List]** se vuelve a cargar en cada navegación de página de Storefront, incluso cuando no se han realizado cambios.

Utilice el menú de la izquierda para navegar a una página específica del parche.
