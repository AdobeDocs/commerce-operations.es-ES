---
title: 'ACP2E-3918: Error de cierre de compra para clientes de la empresa que utilizan recogida en la tienda'
description: Aplique el parche ACP2E-3918 para corregir el problema de Adobe Commerce en el que el cierre de compra falla para los clientes de la empresa que iniciaron sesión y que utilizan recogida en la tienda sin una dirección de facturación predeterminada.
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
exl-id: b3a01d6d-4e25-4089-9f47-e898a8d7a76e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
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
source-wordcount: '384'
ht-degree: 0%
---
# ACP2E-3918: Error de cierre de compra para clientes de la empresa que utilizan recogida en la tienda

El parche ACP2E-3918 corrige el problema en el que falla el cierre de compra para los clientes de la empresa que iniciaron sesión y que utilizan recogida en la tienda sin una dirección de facturación predeterminada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. El ID del parche es ACP2E-3918. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El cierre de compra falla cuando un cliente de la empresa que ha iniciado sesión y no tiene una dirección predeterminada intenta realizar un pedido de compra mediante la recogida en la tienda.

<u>Pasos a seguir</u>:

1. Habilitar **[!UICONTROL Purchase Orders]**.
1. Cree un **[!UICONTROL Company]** y habilite **[!UICONTROL Purchase Orders]** para él.
1. Crear un(a) **[!UICONTROL Company User]** sin direcciones guardadas.
1. Habilitar el método de envío **[!UICONTROL In-Store Delivery]**.
1. Agregar un origen de inventario.
1. Agregar un inventario de existencias.
1. Asignar inventario a un producto.
1. En el front-end, inicie sesión como el usuario de la empresa.
1. Agregar productos a **[!UICONTROL Cart]**.
1. Continúe con el cierre de compra.
1. Seleccione **[!UICONTROL In-Store Pick Up]** en la etapa de envío.
1. Proceda al pago.

<u>Resultados esperados</u>:

El paso de pago se debe cargar correctamente durante el cierre de compra y no debería aparecer ningún error en la consola del explorador.

<u>Resultados reales</u>:

El paso de pago no se carga y la consola del explorador muestra el siguiente error de JavaScript:

```text
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
