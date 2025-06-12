---
title: 'MDVA-40488: los productos configurables con productos secundarios agotados no se muestran en el rango de precios correcto'
description: El parche MDVA-40488 resuelve el problema en el que los productos configurables con productos secundarios agotados no se muestran en su rango de precios correcto. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9. El ID del parche es MDVA-40488. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: Configuration, Orders, Products
role: Admin
exl-id: 9a843d1b-88df-4bd7-a358-3aa34c436bdf
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# MDVA-40488: los productos configurables con productos secundarios agotados no se muestran en el rango de precios correcto

El parche MDVA-40488 resuelve el problema en el que los productos configurables con productos secundarios agotados no se muestran en su rango de precios correcto. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9. El ID del parche es MDVA-40488. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos configurables con productos secundarios agotados no se muestran en su rango de precios correcto.

<u>Requisitos previos</u>:

Vaya a Commerce Admin > **tiendas** > **configuración** > **catálogo** > **Inventario** > **opciones de stock** y establezca la configuración de **Mostrar productos sin existencias** en *Sí*.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con dos productos asociados. Por ejemplo: productos simples rojo y marrón.
1. Establezca el inventario del producto simple en Rojo, establezca el estado de stock en *En stock* y, a continuación, establezca el estado Habilitar producto en *No*.
1. Establezca el inventario del producto simple Marrón y, a continuación, establezca el estado Habilitar producto en *Sí*.
1. Asegúrese de que el estado de Stock del producto configurable sea *En Stock*.
1. Cambie el inventario del producto simple Marrón a 0 y establezca el estado de las existencias en *Agotado*.
1. En este punto, el estado de stock del producto configurable sigue siendo *En stock*.
1. Realice una reindexación.
1. Compruebe `min_price` y `max_price` para el producto configurable en la tabla de base de datos `catalog_product_index_price`; los dos valores se establecen en 0.
1. Pero si establecemos el estado de stock del producto configurable en *Agotado* y reindexamos, podemos ver valores distintos de cero de `min_price` y `max_price` del producto configurable.

<u>Resultados esperados</u>:

Si todos los productos secundarios están *Agotados* y el producto configurable en sí también está *Agotados*, el precio se calcula usando todos los productos secundarios.

<u>Resultados reales</u>:

Los valores `min_price` y `max_price` del producto configurable en la tabla de base de datos `catalog_product_index_price` se establecen en 0 cuando el estado de existencias configurable es *En existencias*, pero si es *Sin existencias*, se convierten en valores distintos de cero.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
