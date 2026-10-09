---
title: 'ACSD-46520: Estado de pedido incorrecto al reembolsarlo mediante créditos de la tienda'
description: Este artículo proporciona una solución para el problema en el que los usuarios obtienen un estado de pedido incorrecto cuando se les reembolsa mediante créditos de la tienda.
feature: Orders, Returns
role: Admin
exl-id: 67740003-a71e-41bf-afda-ca3e32290115
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: ac07462c-732c-5c1c-947b-4ce533b4fcfb
    internal-label: Returns
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%
---
# ACSD-46520: Estado de pedido incorrecto al reembolsarlo mediante créditos de la tienda

El parche ACSD-46520 soluciona el problema en el que los usuarios obtienen un estado de pedido incorrecto cuando se les reembolsa mediante créditos de la tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.20. El ID del parche es ACSD-46520. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 y 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios obtienen un estado de pedido incorrecto cuando se les reembolsa mediante créditos de la tienda.

<u>Pasos a seguir</u>:

1. Cree una cuenta de cliente en la tienda e inicie sesión.
1. Asigne créditos de tienda al cliente desde el administrador. Los créditos de la tienda deben cubrir todo el pedido.
1. Realice un pedido utilizando los créditos de la tienda.
1. Facturar el pedido.
1. Cree una nota de abono para devolver el importe total del pedido.
Seleccione la casilla de verificación **[!UICONTROL Refund to store credit]**.
1. Compruebe el estado del pedido.

<u>Resultados esperados</u>:

El estado del pedido es *Cerrado*.

<u>Resultados reales</u>:

El estado del pedido es *Completo*, que no es el estado correcto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o [!DNL Magento Open Source] de forma local: [Herramientas de parches de calidad > Uso](/help/tools/quality-patches-tool/usage.md) en la guía Herramienta de parches de calidad.
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
