---
title: 'ACSD-60632: Dirección guardada con cada intento de pedido'
description: Aplique el parche ACSD-60632 para corregir el problema de Adobe Commerce en el que se guarda una nueva dirección con cada intento de colocación de pedido, independientemente de si el pedido se crea correctamente o no.
feature: Orders, Products
role: Admin, Developer
exl-id: 9b623a1c-594f-47ed-82b4-d11ba20f3a58
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-60632: Dirección guardada con cada intento de pedido

El parche ACSD-60632 soluciona el problema de guardar una nueva dirección con cada intento de realización de un pedido, independientemente de si el pedido se ha creado correctamente o no. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51. El ID del parche es ACSD-60632. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p8 - 2.4.7-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cada vez que se intenta colocar un pedido, se guarda una nueva entrada de dirección en el sistema, independientemente de si el pedido se ha creado correctamente.

<u>Pasos a seguir</u>:

1. Habilitar método de pago **[!DNL PayPal Payflow Link]**:
   * En un equipo local, el sistema no puede recibir llamadas de API de [!DNL PayPal Payflow Link] sin una IP real.
1. Cree un producto sencillo.
1. Crear un cliente registrado sin dirección.
1. Añadir el producto al carro de compras.
1. Continúe con Cierre de compra.
1. Rellene la dirección. Asegúrese de que la primera dirección se crea en este paso.
1. En la página *[!UICONTROL Review and Payments]*, seleccione el botón de opción **[!UICONTROL Credit Card (Payflow Link)]**.
1. Haga clic **[!UICONTROL Continue]**:
   * La página de cierre de compra vuelve al paso *[!UICONTROL Review and Payments]* con la dirección previamente rellenada y el mensaje de error esperado.
1. Vuelva a seleccionar el botón de opción *[!UICONTROL Credit Card (Payflow Link)]*.
1. Haga clic en **[!UICONTROL Continue]**.

<u>Resultados esperados</u>:

No se crea una dirección nueva en el segundo intento de ubicación de pedido.

<u>Resultados reales</u>:

Se crea una nueva dirección después de cada intento de colocación de pedido.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
