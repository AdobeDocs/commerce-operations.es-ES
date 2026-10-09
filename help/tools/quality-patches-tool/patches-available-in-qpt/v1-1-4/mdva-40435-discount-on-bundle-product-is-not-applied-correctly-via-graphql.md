---
title: 'MDVA-40435: El descuento en el paquete no se aplica correctamente a través de GraphQL'
description: El parche MDVA-40435 soluciona el problema de que el descuento en un producto empaquetado no se aplique correctamente a través de GraphQL. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4. El ID del parche es MDVA-40435. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: GraphQL, Orders, Personalization, Products
role: Admin
exl-id: 001be138-5d09-455d-a597-57115cd21a25
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%
---
# MDVA-40435: El descuento en el paquete no se aplica correctamente a través de GraphQL

El parche MDVA-40435 soluciona el problema de que el descuento en un producto empaquetado no se aplique correctamente a través de GraphQL. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.4. El ID del parche es MDVA-40435. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El descuento en un producto empaquetado no se aplica correctamente a través de GraphQL.

<u>Pasos a seguir</u>:

1. Cree una regla de precio de carro de compras con un código de cupón para un descuento fijo de 5 $.
1. Cree un carro vacío a través de GraphQL.
1. Añadir un producto agrupado al carro de compras mediante GraphQL.
1. Aplique el código de cupón en la cantidad fija (5$) a través de GraphQL.
1. Obtenga la información del carro de compras mediante GraphQL.

<u>Resultados esperados</u>:

&quot;descuentos&quot; es de $5.

<u>Resultados reales</u>:

&quot;descuentos&quot; es NULL.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
