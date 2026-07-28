---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.82'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.82.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-07-24T20:44:59.025Z'
TQID: 'https://experienceleague.adobe.com/Qoz-3w1ddXeHyDsyfsM0gD1kwi-Z6dc-C6P9Q-nYrUo'
product_v2: id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2: id: bd989d82-1e15-4534-88db-f1f51dd77ffaid: c1256247-af4b-46d8-9dca-0c654ecfa157id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4358eb2865fbd8a66716ffc6b7a7b133a7e10e5d
workflow-type: tm+mt
source-wordcount: 485
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.82

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.82.

QPT v1.1.82 incluye los siguientes parches:

1. **ACP2E-4815**: corrige varios problemas de GraphQL que causaban excepciones de PHP en los registros, asociación correcta de pedidos con cuentas de clientes creadas después de pedidos a través de GraphQL y alineación de respuestas con GraphQL a través de especificaciones HTTP.
1. **ACP2E-4194**: corrige el problema en el que las respuestas de GraphQL devuelven códigos de estado HTTP incorrectos para solicitudes no válidas, no autorizadas o con formato incorrecto.
1. **ACP2E-4547**: corrige el problema en el cual un usuario administrador no puede usar **[!UICONTROL Add Products by SKU]** en el administrador para agregar productos del catálogo estándar a una oferta negociable para una compañía asignada a un grupo de clientes que no está vinculado a un catálogo compartido.
1. **ACP2E-4593**: corrige el problema en el que la página de CMS que se muestra para las restricciones de sitios web es incorrecta en sitios web secundarios en implementaciones de varios sitios web.
1. **ACP2E-4682**: corrige el problema que se produce cuando al visitar una página de Storefront que comprueba el estado de la cotización `isActive` se crean registros de cotización vacíos cada vez que se carga la página.
1. **ACP2E-4695**: corrige el problema por el que el indizador de reglas de catálogo consume memoria excesiva y no se puede completar, lo que provoca inestabilidad y errores de memoria insuficiente.
1. **ACP2E-4698**: corrige el problema por el que al volver a editar una imagen en el contenido de texto del Page Builder se guarda una URL de medios absoluta en lugar de conservar una directiva de medios portátil.
1. **[ACP2E-4748](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4748.md)**: soluciona el problema por el que la caducidad de los puntos de recompensa se ejecuta lentamente en las tiendas con un historial de puntos de recompensa grande, lo que causa retrasos en los puntos de recompensa que caducan.
1. **ACP2E-4797**: soluciona el problema que causaba que la introducción de caracteres Unicode de 4 bytes en el editor de WYSIWYG o en el contenido de Page Builder en el administrador se bloqueara incorrectamente incluso cuando la base de datos está configurada para admitir `utf8mb4`.
1. **ACP2E-4799**: corrige el problema en el que la consulta de GraphQL `requisition_lists` devuelve un valor de `total_count` que refleja únicamente el número de elementos de la página actual en lugar del número total de listas de solicitudes que coinciden con los criterios de la consulta.
1. **ACP2E-4805**: corrige el problema en el que las solicitudes de API de cierre de compra se vuelven significativamente más lentas para los productos configurables con muchos productos secundarios cuando el primer producto secundario comercializable aparece tarde en la lista.
1. **ACP2E-4840**: corrige el problema en el que el valor de cantidad solicitado en la consulta de GraphQL `products` devuelve *null*.
1. **ACP2E-4870**: corrige el problema en el que **[!UICONTROL Product Alerts]** notificaciones por correo electrónico omiten la configuración de correo electrónico de vista de tienda.
1. **[ACP2E-4875](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-82/acp2e-4875.md)**: corrige el problema en el que al ver cuentas de clientes con libretas de direcciones grandes en el administrador se cierra la sesión de los usuarios administradores de forma inesperada.
1. **ACP2E-4894**: Corrige el problema por el que los nuevos pedidos se retrasan en aparecer en las cuadrículas de administración de pedidos cuando **[!UICONTROL Asynchronous Indexing]** está habilitado en tiendas de gran volumen.
1. **ACP2E-4981**: corrige el problema en el que los carruseles de productos de Page Builder muestran productos en un orden que no refleja la posición establecida en el Administrador e incluyen productos configurables cuando se encuentran productos secundarios que coinciden y que son visibles individualmente.

Utilice el menú de la izquierda para navegar a una página específica del parche.
