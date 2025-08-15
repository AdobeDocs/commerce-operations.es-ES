---
title: 'ACSD-49502: el vínculo descargable no se actualizó correctamente después de  [!DNL staging] actualizar'
description: Aplique el parche ACSD-49502 para corregir el problema de Adobe Commerce donde el vínculo descargable no se actualiza correctamente después de que se aplique una  [!DNL staging] actualización al producto descargable.
feature: Staging
role: Admin
exl-id: 9bdc9a7e-4291-4438-9ba0-65fcab1f95bb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-49502: el vínculo descargable no se actualizó correctamente después de la actualización de [!DNL staging]

La revisión ACSD-49502 corrige el problema en el cual el vínculo descargable no se actualiza correctamente después de que se aplique una actualización [!DNL staging] al producto descargable. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-49502. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El vínculo descargable no se actualiza correctamente después de aplicar una actualización [!DNL staging] al producto descargable.

<u>Pasos a seguir</u>:

1. Cree un producto descargable con vínculos.
1. Cree una cuenta de cliente e inicie sesión.
1. Añadir el producto descargable al carro de compras desde la tienda.
1. En **[!UICONTROL Admin]**, programe una nueva actualización para el producto descargable y deje que se complete la actualización programada.
1. Complete el pedido en la tienda.

<u>Resultados esperados</u>:

Los vínculos descargables se conservan al utilizar actualizaciones programadas mientras los productos añadidos anteriormente están en el carro de compras.

<u>Resultados reales</u>:

Faltan vínculos descargables en las páginas *[!UICONTROL My Account]* ([!UICONTROL My Downloadable Products]) del cliente y de vista de pedidos en **[!UICONTROL Admin]**.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
