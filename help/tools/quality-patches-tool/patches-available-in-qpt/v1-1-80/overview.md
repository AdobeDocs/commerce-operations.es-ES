---
title: 'Información general:  [!DNL Quality Patches Tool] (QPT) v1.1.80'
description: Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en  [!DNL Quality Patches Tool] (QPT) v1.1.80.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
autotag-review: '2026-06-11T01:10:37.916Z'
TQID: 'https://experienceleague.adobe.com/q2sNWUJQCm4eRUP8RusytBAqQoscU4F9qDtDIeNmm6E'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: c1256247-af4b-46d8-9dca-0c654ecfa157
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 54099d0e9607799ea1ea17d8b5b0ea3c38c2d513
workflow-type: tm+mt
source-wordcount: 418
ht-degree: 0%

---

# Información general: [!DNL Quality Patches Tool] (QPT) v1.1.80

Esta subsección proporciona una descripción detallada de los problemas corregidos por los parches disponibles en [!DNL Quality Patches Tool] (QPT) v1.1.80.

QPT v1.1.80 incluye los siguientes parches:

1. **ACP2E-4239**: corrige el problema en el que los filtros de cuadrícula de administración que utilizan atributos de fecha devuelven resultados incorrectos debido a diferencias de zona horaria entre la fecha seleccionada, los valores UTC almacenados y la zona horaria de almacén configurada.
1. **[ACP2E-4472](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4472.md)**: corrige el problema por el que se crea un registro de comillas nulas en la tabla de base de datos `quote` durante el flujo **[!UICONTROL Login as Customer]**.
1. **ACP2E-4481**: corrige el problema en el cual la capacidad de venta de productos del paquete no se recalcula correctamente después de que se cancele un pedido.
1. **ACP2E-4488**: corrige el problema por el cual guardar o editar productos en [!UICONTROL Admin] es lento para productos con grandes conjuntos de atributos.
1. **ACP2E-4493**: corrige el problema en el que la cuadrícula Archivo de pedidos de ventas muestra un estado de pedido incorrecto cuando la indexación asincrónica está habilitada.
1. **ACP2E-4496**: corrige el problema en el que el trabajo cron de Analytics causa una degradación del rendimiento durante la ejecución, lo que da como resultado un rendimiento general del sistema mejorado.
1. **[ACP2E-4533](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4533.md)**: corrige el problema por el que las imágenes de marcador de posición no se cargan en la tienda cuando se incluye un código de tienda en la dirección URL.
1. **ACP2E-4552**: corrige el problema donde el estado de la compañía no se devuelve en la respuesta de GraphQL.
1. **ACP2E-4610**: Corrige el problema en el que el trabajo cron de `sales_clean_quotes` tiene problemas de rendimiento.
1. **ACP2E-4615**: corrige el problema en el que los reembolsos de pedidos en línea fallan con un error de PayPal que indica que *la puerta de enlace de PayPal rechaza la solicitud. Error interno.*.
1. **ACP2E-4626**: corrige el problema donde algunos archivos de Storefront JavaScript se solicitaron y ejecutaron dos veces, causando cargas duplicadas intermitentes y comportamiento inestable.
1. **[ACP2E-4653](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4653.md)**: corrige el problema en el que el ámbito del atributo de condición de regla de precio de carro de compras para **[!UICONTROL Category (Parent Only)]** y **[!UICONTROL Category (Children Only)]** no se expone al recuperar o actualizar reglas a través de la API [!DNL REST].
1. **[ACP2E-4808](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4808.md)**: corrige el problema por el que el atributo Weight de la página de productos de la tienda muestra únicamente un valor numérico sin procesar en la sección **[!UICONTROL Additional Information]** o **[!UICONTROL More Information]** sin la unidad de medida configurada (libras o kg).
1. **[ACP2E-4156](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-80/acp2e-4156.md)**: corrige el problema en el que la validación de la dirección de envío en la API [!DNL REST] no cumple la configuración de atributo definida en Administración.
1. **ACP2E-4813**: soluciona el problema en el que los métodos de envío de USPS no están disponibles al realizar el cierre de compra y las estimaciones de envío son incorrectas para determinados productos, incluidos los pedidos que se dividen en varios paquetes.
1. **ACSD-53502**: corrige el problema en el que **[!UICONTROL Add to Cart]** produce un error intermitente en la tienda de iOS [!DNL Safari] debido a llamadas recursivas al script de supervisión de New Relic, lo que provoca que la página se vuelva a cargar.

Utilice el menú de la izquierda para navegar a una página específica del parche.
