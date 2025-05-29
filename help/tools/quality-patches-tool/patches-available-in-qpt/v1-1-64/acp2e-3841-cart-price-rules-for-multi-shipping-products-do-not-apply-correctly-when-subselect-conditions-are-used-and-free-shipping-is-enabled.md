---
title: 'ACP2E-3841: Las reglas de precios de carrito para productos de envío múltiple no se aplican correctamente cuando se utilizan condiciones de subselección y el envío gratuito está habilitado'
description: Aplique el parche ACP2E-3841 para corregir el problema de Adobe Commerce en el que las reglas de precio del carro de compras para productos de envío múltiple no se aplican correctamente cuando se utilizan condiciones de subselección y el envío gratuito está habilitado.
feature: Shopping Cart, Price Rules
role: Admin, Developer
source-git-commit: 1abb32109d5ca4a90cdd1d210d1fae6a728699fd
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---


# ACP2E-3841: Las reglas de precios de carrito para productos de envío múltiple no se aplican correctamente cuando se utilizan condiciones de subselección y el envío gratuito está habilitado

El parche ACP2E-3841 corrige el problema en el que las reglas de precio del carro de compras para productos de envío múltiple no se aplican correctamente cuando se utilizan condiciones de subselección y el envío gratuito está habilitado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. El ID del parche es ACP2E-3841. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p9

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.7-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las reglas de precio del carro de compras para productos de envío múltiple no se aplican correctamente cuando se utilizan condiciones de subselección y el envío gratuito está habilitado.

<u>Requisitos previos</u>:

**Configuración:**
1. **[!UICONTROL Free Shipping]** = *Habilitado*
1. **[!UICONTROL Minimum Order Amount]** = *99999999*

**Categorías necesarias:**
1. Prueba de categoría 1
1. Prueba de categoría 2

**Productos necesarios:**
1. Prueba del producto 1:
   1. Categorías: Prueba de categoría 1
   1. Precio: $ 45
1. Prueba del producto 2:
   1. Categorías: Prueba de categoría 2
   1. Precio: $ 56,25 
      **(los precios deben ser los mismos que se muestran aquí para garantizar que la prueba funcione correctamente)**

**Regla de precio del carro de compras:**

Inicie sesión como administrador y vaya a **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add new rule]**. Utilice estos valores:

**[!UICONTROL Rule Information]:**
1. **[!UICONTROL Rule Name]**: Probar envío gratuito
1. **[!UICONTROL Active]**: *Sí*
1. **[!UICONTROL Websites]**: *Sitio web principal*
1. **[!UICONTROL Customer Groups]**: *NO SE HA INICIADO LA SESIÓN, General, Mayorista, Retailer*
1. **[!UICONTROL Coupon]**: *Sin Cupón*
1. **[!UICONTROL Uses per Customer]**: *0*
1. **[!UICONTROL Priority]**: *1*

**[!UICONTROL Conditions]:**

**[!UICONTROL If ALL of these conditions are TRUE:]**


**[!UICONTROL If total amount (incl. tax) equals or greater than 100 for a subselection of items in cart matching ALL of these conditions:]**


**[!UICONTROL Category is]** *5,12,13*

Acciones:

**[!UICONTROL Percent of product price discount]** = *10*

<u>Pasos a seguir</u>:

1. Inicie sesión en la tienda.
2. Agregar prueba de producto 1.
3. Añada dos cantidades de Prueba de producto 2.
4. Carro de visitas.
5. Seleccione **[!UICONTROL Check Out with Multiple Addresses]**.

<u>Resultados esperados</u>:

Sin errores.

<u>Resultados reales</u>:

*Error 500*

*Mensaje: Funcionalidad obsoleta: La conversión implícita de float 112.5 a int pierde precisión en /app/code/Magento/SalesRule/Model/Rule/Condition/Product/Subselect.php en la línea 214*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
