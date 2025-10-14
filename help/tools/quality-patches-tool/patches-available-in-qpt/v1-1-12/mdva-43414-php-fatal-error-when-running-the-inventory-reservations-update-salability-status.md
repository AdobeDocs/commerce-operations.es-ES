---
title: 'MDVA-43414: Error grave de PHP al ejecutar "inventory.booking.updateSalabilityStatus"'
description: El parche MDVA-43414 resuelve el error grave de PHP que se produce al ejecutar el consumidor de cola "inventory.booking.updateSalabilityStatus" en los SKU numéricos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-43414. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
feature: Inventory, Orders
role: Admin
exl-id: 893a5665-ff1b-4862-a984-d9abf642fba3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-43414: Error grave de PHP al ejecutar &quot;inventory.booking.updateSalabilityStatus&quot;

El parche MDVA-43414 resuelve el error irrecuperable de PHP que se produce al ejecutar el consumidor de cola `inventory.reservations.updateSalabilityStatus` en SKU numéricas. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-43414. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.6-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.6 - 2.3.7-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error grave de PHP al ejecutar el consumidor de cola &quot;inventory.booking.updateSalabilityStatus&quot; en SKU numéricas.

<u>Requisitos previos</u>:

Módulos de inventario instalados.

<u>Pasos a seguir</u>:

1. Crear un origen de inventario personalizado y asignarlo a un nuevo inventario de stock.
1. Cree un producto con el origen de inventario personalizado.
1. Asegúrese de que el SKU del producto sea un valor entero.
1. Haga un pedido.
1. Ejecute el comando `bin/magento queue:consumer:start inventory.reservations.updateSalabilityStatus`.

<u>Resultados esperados</u>:

La cola se inicia sin ningún error.

<u>Resultados reales</u>:

Error grave de PHP:

```PHP
PHP Fatal error:  Uncaught TypeError: Argument 1 passed to Magento\InventoryIndexer\Model\Queue\UpdateIndexSalabilityStatus\IndexProcessor::getIndexSalabilityStatus() must be of the type string, int given, called in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php on line 119 and defined in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php:136
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
