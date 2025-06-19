---
title: 'MDVA-38852: El inventario de catálogo bloquea las tablas, lo que reduce el rendimiento'
description: El parche MDVA-38852 resuelve el problema en el que el inventario de catálogo bloquea las tablas para las actualizaciones, lo que reduce significativamente el rendimiento cuando se realizan varios pedidos paralelos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. El ID del parche es MDVA-38852. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.6.
feature: Catalog Management, Inventory, Orders
role: Admin
exl-id: ce93130b-8d96-47b8-96c6-da5988b34ae0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-38852: El inventario de catálogo bloquea las tablas, lo que reduce el rendimiento

El parche MDVA-38852 resuelve el problema en el que el inventario de catálogo bloquea las tablas para las actualizaciones, lo que reduce significativamente el rendimiento cuando se realizan varios pedidos paralelos. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. El ID del parche es MDVA-38852. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.3.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El inventario de catálogo bloquea las tablas para las actualizaciones, lo que reduce significativamente el rendimiento en casos en los que se realizan varios pedidos paralelos.

<u>Pasos a seguir</u>:

1. Añadir un producto al carro de compras.
1. Continúe con el cierre de compra e intente realizar un pedido.

<u>Resultados esperados</u>:

* No hay interbloqueos.
* El rendimiento no disminuye en los casos en que se realizan varios pedidos paralelos.

<u>Resultados reales</u>:

* Realizar un pedido es extremadamente lento cuando hay varios usuarios simultáneos.
* Se producen errores de interbloqueo con el aspecto siguiente:

```SQL
"SQLSTATE[40001]: Serialization failure: 1213 Deadlock found when trying to get lock; try restarting transaction, query was:
INSERT INTO `quote_payment` (`quote_id`, `method`, `additional_information`) VALUES (?, ?, ?)"
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
