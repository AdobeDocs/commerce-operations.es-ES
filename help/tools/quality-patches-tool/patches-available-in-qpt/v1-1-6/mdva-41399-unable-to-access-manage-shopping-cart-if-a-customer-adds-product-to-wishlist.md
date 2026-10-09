---
title: 'MDVA-41399: No se puede acceder a Administrar carro de compras si un cliente agrega un producto a la lista de deseos'
description: El parche MDVA-41399 resuelve el problema en el que los usuarios administradores no pueden acceder a la página Administrar carro de compras si un cliente agrega un producto a la lista de deseos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6. El ID del parche es MDVA-41399. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: 81a128b5-0c38-4f8f-b297-1f264952d431
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%
---
# MDVA-41399: No se puede acceder a Administrar carro de compras si un cliente agrega un producto a la lista de deseos

El parche MDVA-41399 resuelve el problema en el que los usuarios administradores no pueden acceder a la página Administrar carro de compras si un cliente agrega un producto a la lista de deseos. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.6. El ID del parche es MDVA-41399. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios administradores no pueden acceder a la página Administrar carro de compras si un cliente añade un producto a la lista de deseos.

<u>Requisitos previos</u>:

1. Cree dos o más productos.
1. Crear un cliente.
1. Active el modo de desarrollador.

<u>Pasos a seguir</u>:

1. Vaya a Storefront e inicie sesión como cliente desde las condiciones previas.
1. Añadir un producto a la lista de deseos.
1. Vaya al panel de administración, navegue hasta la página de edición del cliente creada y haga clic en el botón **Administrar carro de compras**.

<u>Resultados esperados</u>:

El usuario administrador puede administrar el carro de compras.

<u>Resultados reales</u>:

El usuario administrador recibe un mensaje de error: *Se produjo un error. Consulte el registro de errores para obtener detalles.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
