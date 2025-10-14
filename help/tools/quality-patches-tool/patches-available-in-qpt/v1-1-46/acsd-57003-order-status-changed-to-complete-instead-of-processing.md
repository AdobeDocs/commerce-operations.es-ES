---
title: 'ACSD-57003: el estado del pedido cambia a *Completo* en lugar de cambiar a *Procesando*'
description: Aplique el parche ACSD-57003 para corregir el problema de Adobe Commerce en el que el estado del pedido cambia a *Completado* en lugar de cambiar a *Procesando*.
feature: Orders, Invoices, Shipping/Delivery
role: Admin, Developer
exl-id: a28ecc35-5c9a-4bba-b0b9-67fbe37ed8c3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-57003: el estado del pedido cambia a *Completo* en lugar de cambiar a *Procesando*

El parche ACSD-57003 corrige el problema en el que el estado del pedido cambia a *Completo* en lugar de cambiar a *Procesando*. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.46. El ID del parche es ACSD-57003. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3, 2.4.6-p8, 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p9, 2.4.7-p2 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado del pedido cambia a *Completo* en lugar de cambiar a *Procesando* cuando un pedido se reembolsa parcialmente y se envía parcialmente.

<u>Pasos a seguir</u>:

1. Cree un pedido con dos productos configurables.
1. Facturar todos los artículos.
1. Enviar solo el primer artículo.
1. Devolver o crear un abono solo para el artículo enviado (*primer artículo*).
1. Compruebe el estado del pedido.

<u>Resultados esperados</u>:

El estado del pedido debe ser _Procesando_.

<u>Resultados reales</u>:

El estado del pedido cambia a *Completo* después de crear una nota de abono para el artículo enviado parcialmente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
