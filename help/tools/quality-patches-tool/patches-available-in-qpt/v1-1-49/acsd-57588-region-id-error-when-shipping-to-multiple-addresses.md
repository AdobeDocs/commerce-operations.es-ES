---
title: 'ACSD-57588: Error en el procesamiento del ID de región al realizar envíos a varias direcciones'
description: Aplique el parche ACSD-57588 para corregir el problema de Adobe Commerce en el que el envío de un pedido a varias direcciones déclencheur un error durante el procesamiento del ID de región.
feature: Orders, Shipping/Delivery
role: Admin, Developer
exl-id: 9a455d32-47d3-4d29-b12e-068bbee98f89
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-57588: Error en el procesamiento del ID de región al realizar envíos a varias direcciones

El parche ACSD-57588 soluciona el problema de que el envío de un pedido a varias direcciones déclencheur un error durante el procesamiento del ID de región. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49. El ID del parche es ACSD-57588. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se ha producido un error durante el procesamiento del ID de región al realizar envíos a varias direcciones.

<u>Pasos a seguir</u>:

1. Configurar el método de pago [!DNL Braintree].
1. Inicie sesión como cliente en la tienda.
1. Añadir un producto al carro de compras y continuar para ver y editar el carro de compras.
1. Agregue varias direcciones *(por ejemplo, Reino Unido, EE. UU., CA)* durante el proceso de cierre de compra y revise el pedido.
1. En la página de pago, seleccione la opción de pago con tarjeta de crédito, introduzca las credenciales necesarias y realice el pedido.

<u>Resultados esperados</u>:

El pedido se puede realizar correctamente.

<u>Resultados reales</u>:

El pedido no se ha realizado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
