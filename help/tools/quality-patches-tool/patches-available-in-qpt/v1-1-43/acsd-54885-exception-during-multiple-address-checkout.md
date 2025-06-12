---
title: 'ACSD-54885: excepción durante la desprotección de varias direcciones cuando el administrador inicia sesión como cliente'
description: Aplique el parche ACSD-54885 para corregir el problema de Adobe Commerce en el que se produce un error durante la desprotección de varias direcciones cuando el administrador utiliza la funcionalidad *[!UICONTROL Login as Customer]*.
feature: Checkout
role: Admin, Developer
exl-id: c146bc2a-2df1-4825-9cfc-69e04095b3c2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-54885: excepción durante la desprotección de varias direcciones cuando el administrador inicia sesión como cliente

La revisión ACSD-54885 corrige el problema en el que se produce un error durante la desprotección de varias direcciones cuando el administrador utiliza la funcionalidad *[!UICONTROL Login as Customer]*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43. El ID del parche es ACSD-54885. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error durante la desprotección de varias direcciones cuando el administrador utiliza la funcionalidad *[!UICONTROL Login as Customer]*.

<u>Pasos a seguir</u>:

1. Asegúrese de que *[!UICONTROL Login as Customer]* esté habilitado. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Advanced]** > **[!UICONTROL Admin]** > **[!UICONTROL Admin Actions]** > **[!UICONTROL Logging]** > **[!UICONTROL Login as Customer]**.
1. Cree un producto sencillo.
1. Cree una nueva cuenta de cliente con una dirección.
1. Vaya a la cuenta del cliente en el servidor:

   * Vaya a la ficha **[!UICONTROL Account Information]** y establezca *[!UICONTROL Allow remote shopping assistance]* = *Sí*.
   * Haga clic en **[!UICONTROL Login as Customer]**.

1. Agregar el producto al carro de compras y continuar con *[!UICONTROL Checkout with multiple addresses]*.
1. Actualice la cantidad del producto.
1. Intente volver al carro de compras.

<u>Resultados esperados</u>:

Puede actualizar el carro de compras y usar el cierre de compra de varias direcciones.

<u>Resultados reales</u>:

Recibe el siguiente error al volver al carro de compras.

```PHP
report.CRITICAL: Error: Call to a member function getCustomer() on null in magento2ee/app/code/Magento/LoginAsCustomerLogging/Observer/LogUpdateQtyObserver.php:88
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
