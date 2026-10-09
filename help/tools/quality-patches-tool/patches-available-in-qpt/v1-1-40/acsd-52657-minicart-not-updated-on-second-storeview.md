---
title: 'ACSD-52657: Minicart no se actualiza en la segunda vista de tienda que utiliza un subdominio'
description: Aplique el parche ACSD-52657 para corregir el problema de Adobe Commerce en el que la minicart no se actualiza en la segunda vista de tienda que utiliza un subdominio.
feature: Shopping Cart
role: Admin, Developer
exl-id: feec9dde-5532-481b-9410-7f6be9df4be7
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
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
source-wordcount: '411'
ht-degree: 0%
---
# ACSD-52657: Minicart no se actualiza en la segunda vista de tienda que utiliza un subdominio

El parche ACSD-52657 corrige el problema en el que la minicart no se actualiza en la segunda vista de tienda que utiliza un subdominio. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.40. El ID del parche es ACSD-52657. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Minicart no se actualiza en la vista de tienda secundaria que utiliza un subdominio.

<u>Pasos a seguir</u>:

1. Cree una segunda vista de tienda y configure un subdominio para la dirección URL base.
1. Actualice el dominio de la cookie para que tenga el dominio común.
1. En la tienda principal, agregue un producto al carro de compras.
1. Actualice la segunda vista de tienda y, a continuación, vaya a la página del carro de compras.

<u>Resultados esperados</u>:

El carro de compras y las miniaturas se actualizan en el subdominio.

<u>Resultados reales</u>:

Minicart no se actualiza cuando se actualiza el almacén secundario, pero la página del carro muestra el producto agregado y puede realizar un pedido en esa sesión (la cookie `PHPSESSID` se comparte).

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
