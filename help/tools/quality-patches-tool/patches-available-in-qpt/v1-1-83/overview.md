---
title: 'Información general: [!DNL Quality Patches Tool] (QPT) v1.1.83'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.83.
feature: Tools and External Services
role: Admin, Developer
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
source-git-commit: 758cab5d4002ddba607dadb3c4b44553adf8d8ba
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 0%
---
# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.83

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.83.

QPT v1.1.83 incluye los siguientes parches:

1. **AC-17975**: corrige varios problemas de compatibilidad con PHP 8.5 que afectan los flujos de trabajo de administración, la autenticación de cierre de compra, el procesamiento CAPTCHA, la administración de categorías, las páginas de configuración y las operaciones de línea de comandos en ciertos entornos PHP.
1. **AC-18128**: corrige el problema por el que las fechas de los pedidos y las marcas de tiempo de los comentarios de pedidos devueltas por GraphQL muestran fechas de calendario incorrectas en configuraciones regionales que no están en inglés.
1. **AC-18096**: corrige el problema en el que los campos de fecha de Sales GraphQL devuelven fechas en un formato diferente al de versiones anteriores al revertir el formato de fecha de separado por barras (`/`) a separado por guiones (`-`).
1. **ACP2E-4639**: corrige el problema por el que el tipo de elementos de la lista de solicitudes estaba mal escrito en el esquema de GraphQL, mientras que el campo de elementos antiguos y el tipo `RequistionListItems` siguen estando disponibles pero están obsoletos.
1. **ACP2E-4838**: corrige el problema en el cual un usuario administrador con permisos restringidos no puede eliminar clientes de la cuadrícula Clientes.
1. **ACP2E-4877**: corrige el problema por el que los pedidos realizados con **[!UICONTROL Payment on Account]** no se pudieron editar en el administrador mientras estaban en estado *Pendiente*.
1. **ACP2E-4908**: soluciona el problema de los catálogos grandes que causan un uso excesivo de memoria en Redis o Valkey porque se crearon entradas de caché de diseño independientes para cada producto en cada vista de tienda.
1. **[AC-12854](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/ac-12854.md)**: corrige el problema en el cual al reordenar un pedido en el administrador se crea un nuevo número de pedido con un sufijo `-1` en lugar de asignar el siguiente número de pedido secuencial.
1. **ACP2E-4977**: corrige el problema en el que los totales generales de facturas y notas de abono de los productos configurables no incluyen **[!UICONTROL Fixed Product Tax]** (FPT), lo que da como resultado totales inferiores al total del pedido.
1. **AC-16530**: corrige un problema en el cual el carro de compras no reflejaba de manera consistente las actualizaciones programadas en las reglas de precios del catálogo.
1. **AC-11389**: corrige el problema por el que los descuentos, impuestos y totales de pedidos se calculan incorrectamente en algunos casos de redondeo.
1. **ACP2E-4998**: corrige el problema en el que la solicitud de API de REST `POST /V1/products/tier-prices` falló para toda la solicitud cuando no existía un SKU en la carga útil, lo que impedía que se actualizaran los SKU válidos.
1. **ACP2E-5015**: corrige el problema en el cual al guardar un catálogo compartido en el administrador se pueden eliminar involuntariamente los productos y precios asignados cuando los datos de catálogo requeridos no están disponibles.
1. **AC-14940**: corrige el problema por el cual al hacer clic en **[!UICONTROL Reset Password]** para una cuenta de cliente en el administrador no se enviaba el correo electrónico de restablecimiento de contraseña en algunos casos relacionados con el almacén.
1. **[ACP2E-5101](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-5101.md)**: corrige el problema en el que se produjo un error al instalar el módulo B2B cuando los indizadores se establecieron en **[!UICONTROL Update by Schedule]**.
1. **ACP2E-5205**: corrige el problema que se produce cuando la carga de categorías tarda mucho tiempo o agota el tiempo de espera cuando hay un gran número de categorías y productos involucrados. Además, el recuento de productos ahora se muestra correctamente para cada hoja de categoría.
1. **ACP2E-3211**: soluciona el problema que causaba que, al agregar el mismo producto al carro de compras al mismo tiempo en la tienda, se crearan elementos independientes en el carro de compras para la misma SKU en lugar de combinarlos en un solo elemento.
1. **[ACP2E-5223](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-83/acp2e-5223.md)**: corrige el problema en el que el índice **[!UICONTROL Catalog Permissions]** incluye sitios web que se excluyen de un grupo de clientes.

Utilice el menú de la izquierda para navegar a una página específica del parche.
