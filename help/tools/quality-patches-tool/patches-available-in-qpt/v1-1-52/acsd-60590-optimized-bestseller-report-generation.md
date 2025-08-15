---
title: 'ACSD-60590: Mejora del rendimiento de la generación de informes diarios agregados de éxito de ventas'
description: Aplique el parche ACSD-60590 para solucionar el problema de Adobe Commerce, en el que el informe diario agregado de productos más vendidos tarda una cantidad de tiempo considerable en generarse para un gran volumen de pedidos realizados.
feature: Reporting
role: Admin, Developer
exl-id: 3b2b92eb-d4fc-4cd7-a117-a2c1caac72ec
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-60590: Mejora del rendimiento de la generación de informes diarios agregados de éxito de ventas

El parche ACSD-60590 soluciona el problema por el que el informe diario de ventas acumuladas de Bestsellers tarda bastante tiempo en generarse para un gran volumen de pedidos realizados. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.52. El ID del parche es ACSD-60590. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El informe diario agregado de superventas tarda un tiempo considerable en generarse para un gran volumen de pedidos realizados.

<u>Requisitos previos</u>

Un gran número de pedidos (por ejemplo: *500k*).

<u>Pasos a seguir</u>:

1. Ejecute el siguiente comando:

   `update sales_order set created_at = DATE(DATE_SUB(NOW(), INTERVAL ROUND(RAND()*3650) DAY))  ;`

1. Ejecute el trabajo `aggregate_sales_report_bestsellers_data`.

<u>Resultados esperados</u>:

El trabajo finaliza en menos de 30 segundos.

<u>Resultados reales</u>:

La consulta tarda unos 10 minutos en cada almacén para `created_at` fechas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
