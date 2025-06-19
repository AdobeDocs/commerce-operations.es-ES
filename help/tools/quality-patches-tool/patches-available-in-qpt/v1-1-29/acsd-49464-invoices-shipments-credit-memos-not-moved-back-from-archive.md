---
title: 'ACSD-49464: facturas, envíos y notas de abono que no se han movido del archivo'
description: Aplique el parche ACSD-49464 para solucionar el problema de Adobe Commerce en el que las facturas, los envíos y los abonos no se mueven de vuelta del archivo cuando orderId es diferente.
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: d9ccd043-cbd3-4be5-ab29-c5351da53030
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-49464: facturas, envíos y notas de abono que no se han movido del archivo

El parche ACSD-49464 corrige el problema en el que las facturas, los envíos y los abonos no se mueven de nuevo del archivo cuando orderId es diferente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-49464. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las facturas, los envíos y los abonos no se mueven de vuelta del archivo cuando orderId es diferente.

<u>Pasos a seguir</u>:

1. Activar el archivado de pedidos, facturas, envíos y notas de abono.
1. Cree y complete un pedido, incluidos el envío, la factura y la nota de abono.
1. Asegúrese de que los ID de envío, de factura y de nota de abono no sean los mismos que el número de pedido.
1. Mueva el orden para archivar.
1. Restaure el pedido archivado en Order Management.
1. Compruebe los detalles de la factura, el envío y el abono en las páginas respectivas de cuadrícula [!UICONTROL Invoice], [!UICONTROL Shipping] y [!UICONTROL Credit Memo].

<u>Resultados esperados</u>:

Los registros relacionados originales se restauran cuando el orden se mueve de la lista de archivos a la administración de pedidos.

<u>Resultados reales</u>:

* No hay registros para el envío, la factura y las notas de abono si todos los ID son diferentes.
* Si el pedido y los registros relacionados tienen el mismo ID, se devuelven los registros.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
