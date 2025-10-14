---
title: 'ACSD-59865: [!UICONTROL Cart Price Rule] no puede cancelar las reglas anteriores debido a una cantidad de producto insuficiente'
description: Aplique el parche ACSD-59865 para corregir el problema de Adobe Commerce en el que el valor de *Paso de cantidad de descuento* en *Descuento de cantidad fija* *Porcentaje de descuento en el precio del producto* y *Comprar X obtener Y* [!UICONTROL Cart Price Rules] ya no cancela la acción de reglas anteriores.
feature: Price Rules
role: Admin, Developer
exl-id: 5838a740-018d-44c2-8135-54426ea08627
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-59865: [!UICONTROL Cart Price Rule] no puede cancelar las reglas anteriores debido a una cantidad de producto insuficiente

La revisión ACSD-59865 corrige el problema en el que el valor *[!UICONTROL Discount quantity step]* de *[!UICONTROL Fixed amount discount],* *[!UICONTROL Percent of product price discount],* y *[!UICONTROL Buy X get Y]* [!UICONTROL Cart Price Rules] ya no cancela la acción de las reglas anteriores. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52. El ID del parche es ACSD-59865. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!UICONTROL Cart Price Rule] no puede cancelar las reglas aplicadas anteriormente debido a una cantidad de producto insuficiente en el carro de compras.

<u>Pasos a seguir</u>:

1. Inicie sesión como administrador.
1. Vaya a **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** y haga clic en **[!UICONTROL Add New rule]**.
   * Establecer **[!UICONTROL Rule Name]** = *Prueba - 1*
   * Seleccionar todos los *sitios web* y *grupos de clientes*
   * Conjunto **[!UICONTROL Priority]** = *0*
   * Vaya a la sección **[!UICONTROL Actions]**:
      * Conjunto **[!UICONTROL Apply]** = *Porcentaje de descuento en el precio del producto*
      * Conjunto **[!UICONTROL Discount amount]** = *10*
      * Conjunto **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Conjunto **[!UICONTROL Discount Qty Step (Buy X)]** = *0*
      * Establecer **[!UICONTROL Discard subsequent rules]** en *No*
1. Borre la caché.
1. Vaya a la Tienda, agregue un elemento al carro y continúe con *cierre de compra/carro*.
1. Verifique que el descuento *10%* se aplique al carro de compras.
1. Vuelva a **[!UICONTROL Cart Price Rules]** y cree una regla nueva.
   * Establecer **[!UICONTROL Rule Name]** = *Prueba - 2*
   * Seleccionar todos **[!UICONTROL Websites]** y **[!UICONTROL Customer Groups]**
   * Conjunto **[!UICONTROL Priority]** = *2*
   * Vaya a la sección **[!UICONTROL Actions]**:
      * Conjunto **[!UICONTROL Apply]** = *Porcentaje de descuento en el precio del producto*
      * Conjunto **[!UICONTROL Discount amount]** = *20*
      * Conjunto **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Conjunto **[!UICONTROL Discount Qty Step (Buy X)]** = *3*
1. Borre la caché.
1. Vuelve a la Tienda otra vez.
1. Actualice el carro de compras para actualizar las reglas. Compruebe que el descuento *10%* ya no se aplique.
1. Agregue artículos al carro de compras hasta que la cantidad alcance el valor de *Step* necesario para la segunda regla.

<u>Resultados esperados</u>:

El primer [!UICONTROL Cart Price Rule] se aplica cuando se cumplen las condiciones de la segunda regla.

<u>Resultados reales</u>:

Las reglas de precios se aplican según lo configurado en el panel de administración.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
