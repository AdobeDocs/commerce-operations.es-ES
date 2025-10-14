---
title: 'MDVA-42855: La nueva dirección del cliente no se guarda en la libreta de direcciones durante el cierre de compra '
description: El parche MDVA-42855 corrige el problema en el que la nueva dirección del cliente no se guarda en la libreta de direcciones durante el cierre de compra. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-42855. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Checkout, Orders, Shipping/Delivery
role: Admin
exl-id: 924b8f57-1fec-4e62-bf0e-1f9cafa75cab
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---

# MDVA-42855: La nueva dirección del cliente no se guarda en la libreta de direcciones durante el cierre de compra

El parche MDVA-42855 corrige el problema en el que la nueva dirección del cliente no se guarda en la libreta de direcciones durante el cierre de compra. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-42855. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La nueva dirección del cliente no se guarda en la libreta de direcciones durante el cierre de compra.

<u>Pasos a seguir</u>:

1. Cree una cuenta de cliente y actualice la dirección de envío y facturación predeterminada.
1. Añada un producto al carro de compras y navegue hasta la página de cierre de compra.
1. En Envío, haga clic en **+ Nueva dirección**.
1. Escriba su nueva dirección y marque la casilla de verificación **Guardar en la libreta de direcciones**.
1. En Pago, marca la casilla **Mi dirección de facturación y envío es la misma**.
1. Realice el pedido.
1. Compruebe la libreta de direcciones.

<u>Resultados esperados</u>:

La nueva dirección de envío se guarda en la libreta de direcciones.

<u>Resultados reales</u>:

La nueva dirección de envío no se guarda en la libreta de direcciones.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
