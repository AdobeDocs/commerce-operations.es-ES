---
title: "ACSD-55241: **Utilizado** y **Tiempos utilizado** muestran valores incorrectos para los cupones generados"
description: Aplique el parche ACSD-55241 para solucionar el problema de Adobe Commerce donde los atributos **Utilizado** y **Tiempos utilizado** muestran valores incorrectos para los cupones generados
feature: Price Rules
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 0%

---

# ACSD-55241: los atributos **Used** y **Times Used** muestran valores incorrectos para los cupones generados

El parche ACSD-55241 corrige el problema en el que los atributos **Used** y **Times Used** muestran valores incorrectos para los cupones generados. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.47. El ID del parche es ACSD-55241. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los atributos **Usados** y **Veces usados** muestran valores incorrectos para los cupones generados.

<u>Pasos a seguir</u>:

1. Cree **[!UICONTROL Cart Price Rules]** a partir de **[!UICONTROL Admin]** > **[!UICONTROL Marketing]** > **[!UICONTROL Promotion]** y agregue cualquier condición que coincida al realizar un pedido (Ejemplo: subtotal mayor que *5$*)

   * Aplicar cualquier descuento.
   * Seleccione **[!UICONTROL Auto Coupon]**.
   * Generará algunos Códigos de cupón a partir de **Administrar Códigos de cupón**.
   * Reindexe y limpie la caché.

1. Cree un **[!UICONTROL customer account]** e inicie sesión en el front-end.
1. Agregue un producto con más de *2* cantidades en el carro y aplique un cupón.
1. Haga clic en **[!UICONTROL Check Out with Multiple Addresses]**.
1. Seleccione una dirección distinta para cada cantidad, realice el pedido y complete el proceso de cierre de compra.
1. Observe el total del pedido del administrador y vea el descuento aplicado.
1. Realice otro pedido con otro cupón.
1. Ejecute el comando `php81 bin/Magento queue:consumers: start sales.rule.update.coupon.usage &` para actualizar el uso del código de cupón.

<u>Resultados esperados</u>:

El recuento correcto debería mostrarse en las columnas **Time used** y **Used** con el valor **Yes** para **[!UICONTROL manage coupon]** en **[!UICONTROL cart price rule]** en el administrador.

<u>Resultados reales</u>:

El recuento de código de cupón utilizado no se actualiza en la columna **Tiempo utilizado** de la cuadrícula de cupones, y la columna **Utilizado** muestra el valor *No* si realiza un pedido con varias direcciones de envío.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
