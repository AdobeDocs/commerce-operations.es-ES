---
title: "MDVA-40609: Datos de productos desactivados ausentes en la tabla cataloginventory_stock_status"
description: El parche MDVA-40609 resuelve el problema en el que los datos de productos desactivados no se muestran en la tabla de índice cataloginventory_stock_status, lo que provoca la visualización de cantidades de productos incorrectas. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6. El ID del parche es MDVA-40609. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# MDVA-40609: datos de productos desactivados ausentes en la tabla cataloginventory_stock_status

El parche MDVA-40609 resuelve el problema en el que los datos de productos deshabilitados no se muestran en la tabla de índice `cataloginventory_stock_status`, lo que provoca la visualización de cantidades de productos incorrectas. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6. El ID del parche es MDVA-40609. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los datos de productos deshabilitados no se muestran en la tabla de índice `cataloginventory_stock_status`, lo que provoca que se muestren cantidades de productos incorrectas.

<u>Requisitos previos</u>:

Módulo de inventario instalado.

<u>Pasos a seguir</u>:

1. Configurar dos sitios web con tiendas y vistas de tiendas.
1. Crear un origen y un stock adicionales.
1. Añada un producto simple:
   * Establezca Habilitar producto en *No*.
   * Asigne dos orígenes con Estado de artículo de Source = Existencia y Cantidad mayor que cero.
1. Guarde el producto.
1. Marque la pestaña **Cantidad de productos vendibles**.

<u>Resultados esperados</u>:

Ambos saldos han introducido valores superiores a cero.

<u>Resultados reales</u>:

Un inventario tiene un valor cero.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
