---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.41'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.41.
feature: Tools and External Services
role: Admin, Developer
exl-id: 10e1f4f9-8c6b-45b2-b6ed-0758c8019c8c
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
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%
---
# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.41

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.41.

QPT v1.1.41 incluye los siguientes parches:

1. **ACSD-54376**: corrige el problema que se produce en el carro de compras cuando un producto se elimina del catálogo compartido después de que ya se haya agregado al carro de compras.
1. **ACSD-53722**: corrige el problema en el que el precio de las opciones de productos agrupados cambia a 0 $ cuando se activan actualizaciones programadas para diferentes ámbitos.
1. **ACSD-53643**: corrige el problema en el que el pedido tiene un total incorrecto al realizar un pedido de compra con productos deshabilitados o sin existencias. Se corrigió ocultando el botón *[!UICONTROL Place Order]* para dichos pedidos de compra.
1. **ACSD-54067**: corrige el problema por el que el vídeo de un producto no se reproduce en un dispositivo móvil.
1. **ACSD-55414**: mejora el rendimiento cuando MariaDB intenta convertir el entity_id de EAV de cadena a entero.
1. **ACSD-51819**: corrige el problema en el cual se pueden realizar varios pedidos con el mismo identificador de presupuesto.
1. **ACSD-53118**: corrige el problema en el que *[!UICONTROL Cart Price Rule]* se aplica usando código de cupón mientras el producto tiene un atributo vacío.
1. **ACSD-54324**: corrige el problema en el que la solicitud de GraphQL request_lists no tiene en cuenta la configuración de paginación y devuelve todos los resultados.

Utilice el menú de la izquierda para navegar a una página específica del parche.
