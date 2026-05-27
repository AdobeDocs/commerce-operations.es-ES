---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.79'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.79.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: 09abc74b48c1ac07a3553aed37fcb0c80e3bbefe
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.79

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.79.

QPT v1.1.79 incluye los siguientes parches:
1. **ACP2E-4402**: corrige el problema por el cual los productos creados como deshabilitados no se volvieron a agregar a los resultados de [!UICONTROL Target Rule] relacionados después de habilitarse.
1. **ACP2E-4505**: soluciona el problema en el que era posible guardar una categoría con datos antiguos desde una ficha de explorador duplicada, creando una dependencia circular.
1. **ACP2E-4531**: corrige el problema que causaba que al cambiar la clave URL de una página CMS no se actualizara la dirección URL jerárquica de la página.
1. **[ACP2E-4603](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4603.md)**: corrige el problema que causaba que al ejecutar el reíndice de productos de [!UICONTROL Catalog Permissions] se dejaran sin cambios las filas de índice de permisos existentes, lo que causaba que las concesiones de permisos de categorías actualizadas no se reflejaran de forma fiable en los productos.
1. **[ACP2E-4601](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4601.md)**: soluciona el problema en el que el procesamiento de transacciones de pago podría comportarse de forma ineficiente en ciertas condiciones.
1. **ACP2E-4706**: corrige el problema por el que el indizador [!UICONTROL Target Rule] omitió los productos no habilitados en el ámbito [!UICONTROL Admin].
1. **ACP2E-4720**: corrige el problema por el cual el envío gratuito no se aplicaba correctamente ni se eliminaba para los productos agrupados con reglas de descuento en el carro de compras.
1. **[ACP2E-4411](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4411.md)**: corrige el problema por el que se muestra un precio incorrecto para un producto agrupado en la página del carro de compras y en el minicarrito para tiendas de múltiples monedas.
1. **ACP2E-4475**: corrige el problema por el que la página de listado de productos filtra y ordena incorrectamente los productos de paquetes agotados por precio cuando la opción **[!UICONTROL Display Out of Stock Products]** está habilitada.
1. **[ACP2E-4110](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/acp2e-4110.md)**: Corrige el problema por el que los productos agrupados con **[!UICONTROL Special Price]** muestran cantidades incorrectas en el PDP y el PLP en una moneda no predeterminada.
1. **AC-10698**: corrige el problema por el que el sistema envió la divisa en el nivel de todos los pedidos en lugar de asociarla con pedidos individuales. Los precios y totales de transacción ahora se envían por pedido a [!DNL Google Tag], lo que mejora la precisión del seguimiento de datos de comercio electrónico.
1. **[AC-10737](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-79/ac-10737.md)**: corrige un problema en el cual el comando `bin/magento setup:db:status` no reconoce el tipo de datos JSON.

Utilice el menú de la izquierda para navegar a una página específica del parche.
