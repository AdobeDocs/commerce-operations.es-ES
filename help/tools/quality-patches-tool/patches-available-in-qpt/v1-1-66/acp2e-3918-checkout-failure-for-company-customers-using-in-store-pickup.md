---
title: 'ACP2E-3918: Error de cierre de compra para clientes de la empresa que utilizan recogida en la tienda'
description: Aplique el parche ACP2E-3918 para corregir el problema de Adobe Commerce en el que el cierre de compra falla para los clientes de la empresa que iniciaron sesión y que utilizan recogida en la tienda sin una dirección de facturación predeterminada.
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
source-git-commit: 1295af44422ffbd67a3666f1a96a75af0a4e3c81
workflow-type: tm+mt
source-wordcount: '359'
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
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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

```
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
