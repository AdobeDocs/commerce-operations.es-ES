---
title: 'MDVA-32776: El estado de las existencias no se actualiza con la realización del pedido'
description: El parche MDVA-32776 soluciona el problema de que el estado de las existencias no se actualiza cuando se realiza un pedido, pero no se envía. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6. El ID del parche es MDVA-32776. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
feature: Orders
role: Admin
exl-id: 6f872c72-c96f-4c23-b6df-44e3da3a81c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-32776: El estado de las existencias no se actualiza con la realización del pedido

El parche MDVA-32776 soluciona el problema de que el estado de las existencias no se actualiza cuando se realiza un pedido, pero no se envía. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6. El ID del parche es MDVA-32776. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.0

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado de stock no se actualiza cuando se realiza un pedido, pero no se envía.

<u>Requisitos previos</u>:

1. Módulo de inventario instalado.
1. Mostrar productos sin existencias está establecido en *Sí*.

   Para configurarlo, vaya a **Tiendas** > **Configuración** > **Catálogo** > **Inventario** > **Mostrar productos sin existencias** = *Sí*.

<u>Pasos a seguir</u>:

1. Cree dos productos simples con qty = 11 y 22.
1. Cree un producto agrupado con los productos simples creados en el paso uno.
1. Añada productos agrupados al carro de compras estableciendo una de las cantidades de productos en 11 y haciendo que el otro producto simple se quede sin existencias.
1. Complete el cierre de compra y realice el pedido.

<u>Resultados esperados</u>:

Los productos agrupados muestran etiquetas `out-of-stock` cuando los productos simples asociados se quedan sin existencias.

<u>Resultados reales</u>:

1. El producto simple con cantidad = 11 muestra sin existencias.
1. El producto agrupado no muestra un mensaje *sin existencias* para el producto con una cantidad = 11. Sin embargo, si se agrega este producto al carro de compras, se producirá un error *sin existencias*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es).
