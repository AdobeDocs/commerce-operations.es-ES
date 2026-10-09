---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.8'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.8.
feature: Tools and External Services
role: Admin
exl-id: bcc35189-bed7-4076-bd9e-3d4ca47b3215
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 0%
---
# Información general de [!DNL Quality Patches Tool] (QPT) v1.1.8

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.8.

QPT v1.1.8 incluye los siguientes parches:

1. **MDVA-38393**: corrige el problema en el cual las reglas de catálogo dejan de funcionar para un producto configurable si se cambia el nombre de su producto simple.
1. **MDVA-39153**: corrige el problema en el cual una cantidad de descuento se calcula incorrectamente durante el repedido en el administrador.
1. **MDVA-41139**: corrige el problema en el cual los productos configurables se quedan sin existencias después de la importación de productos cuando la cantidad=0 de un producto simple para uno de sus orígenes es.
1. **MDVA-41215**: corrige el problema por el que los usuarios reciben el error 500 después de configurar la cookie *mage-messages* si ya existe, pero no hay mensajes nuevos.
1. **MDVA-42326**: corrige el problema en el cual los clientes reciben un error al cerrar la compra después del tiempo de espera de sesión, incluso si el carro de compras persistente está habilitado.
1. **MDVA-42341**: corrige el problema en el cual la consulta de GraphQL `categoryList` no filtra los resultados si una solicitud tiene el encabezado de tienda.

Utilice el menú de la izquierda para navegar a una página específica del parche.
