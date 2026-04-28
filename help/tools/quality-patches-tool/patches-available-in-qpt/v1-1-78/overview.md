---
title: 'Overview: [!DNL Quality Patches Tool] (QPT) v1.1.78'
description: This sub-section provides a detailed description of the issues fixed by the patches available in [!DNL Quality Patches Tool] (QPT) v1.1.78.
feature: Tools and External Services
role: Admin, Developer
type: Troubleshooting
source-git-commit: f0aa5266d54a205cba36d9015fe9ed5dca50b599
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 0%

---

# Overview: [!DNL Quality Patches Tool] (QPT) v1.1.78

This sub-section provides a detailed description of the issues fixed by the patches available in [!DNL Quality Patches Tool] (QPT) v1.1.78.

QPT v1.1.78 includes the following patches:
1. **ACP2E-4416**: Fixes the issue where customer reward points are not initialized when created in the Admin.
1. **[ACP2E-4419](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4419.md)**: Fixes the issue where gift cards are not applied correctly at checkout after successful reCAPTCHA v2 (&#39;I am not a robot&#39;) validation on the storefront.
1. **ACP2E-4431**: Fixes the issue where Related Products matched by the target rules are deleted during the reindex process.
1. **ACP2E-4448**: Fixes the issue where configuration changes made during Redis outages are not reflected after Redis recovers, causing stale values to persist.
1. **ACP2E-4452**: Fixes the issue where product prices on the Quick Order page include tax regardless of the tax display configuration.
1. **ACP2E-4456**: Fixes an issue where canceling an order using a GraphQL mutation does not transition an order paid entirely with gift cards to the Closed status.
1. **ACP2E-4507**: Fixes the issue where Password Options configuration is not applied for customer password reset requests made through GraphQL mutations.
1. **ACP2E-4513**: Fixes the issue where expired CAPTCHA images are not deleted from the system.
1. **[ACP2E-4522](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4522.md)**: Fixes the issue where an intermittent duplicate key error occurs on the quote_coupons table when multiple cart merge or quote save requests run at the same time.
1. **ACP2E-4528**: Fixes the issue with city validation in customer addresses, which now allows a forward slash (/) character and rejects invalid characters such as !, &quot;, #, and ?.
1. **ACP2E-4535**: Fixes an issue where submitting the forgot-password form causes the session to be destroyed or regenerated (PHPSESSID changes) and the guest cart is cleared.
1. **ACP2E-4540**: Fixes the issue where the Fotorama library was not loading correctly, causing only the first attached image to be visible.
1. **[ACP2E-4555](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4555.md)**: Fixes the issue where modern telephone numbers containing &quot;.&quot; or &quot;/&quot; aren&#39;t validated properly.
1. **[ACP2E-4565](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-78/acp2e-4565.md)**: Fixes the issue where the Company GraphQL query returns &quot;The current customer isn&#39;t authorized&quot; when the X-Adobe-Company header is used.
1. **ACP2E-4591**: Fixes the issue where customer segments based on order count, such as &quot;First-time buyers&quot;, did not update when orders were placed via the REST API.
1. **ACP2E-4609**: Fixes the issue where the My Quotes page shows no quotes when some quotes contain deleted products.
1. **ACP2E-4613**: Fixes the issue where large media directory structures caused slow gettree responses, leading to extended Media Gallery directory tree loading times.
1. **ACP2E-4628**: Fixes the issue where importing customers with uppercase email addresses results in the undefined array key error, when Account Sharing is set to Global.
1. **ACP2E-4665**: Fixes the issue where child products of configurable products containing videos in the product galleries are not listed when requested through REST API.
1. **ACP2E-4732**: corrige un problema en el cual se detuvo la indexación parcial para clientes con un gran número de actualizaciones cuando la columna version_id en la tabla changelog alcanzó su valor máximo.
1. **ACP2E-4763**: Corrige el problema por el que la consulta GraphQL customerOrders devuelve valores inflados original_price_included_tax y original_row_total_include_tax cuando los precios de catálogo se establecen en Incluyendo impuesto, debido a que el impuesto se aplica dos veces.
1. **ACSD-60989**: corrige el problema en el que la modificación de una columna con una clave externa a través de un esquema declarativo provoca errores en MariaDB.

Utilice el menú de la izquierda para navegar a una página específica del parche.
