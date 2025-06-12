---
title: 'ACSD-56616: Visualización de productos agrupados en la tienda durante una simple escasez de existencias'
description: Aplique el parche ACSD-56616 para corregir el problema de Adobe Commerce en el que los productos agrupados aparecen inesperadamente en la tienda cuando todos los productos simples asociados están agotados.
feature: Products
role: Admin, Developer
exl-id: 8b225d9d-1898-4c4d-81be-7b92cbf7d06f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-56616: Visualización de productos agrupados en la tienda durante una simple escasez de existencias.

El parche ACSD-56616 soluciona el problema de que los productos agrupados aparecen inesperadamente en la tienda cuando todos los productos simples asociados están agotados. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45. El ID del parche es ACSD-56616. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Visualización incorrecta de la tienda de productos empaquetados durante la simple escasez de existencias.

<u>Pasos a seguir</u>:

1. Cree un nuevo sitio web, tienda o tienda.
1. Cree una nueva fuente.
1. Cree un nuevo inventario de stock y asígnelo al sitio web recién creado.
1. Configure los indexadores para que se actualicen según lo programado.
1. Genere dos productos simples, S1 (cantidad = 1) y S2 (cantidad = 1), y asígnelos al nuevo sitio web y a las nuevas existencias.
1. Cree el producto *bundled1* y asócielo con el nuevo sitio web, colocándolo en la categoría *CAT*.
1. Defina dos opciones desplegables necesarias y vincule el producto simple *S1* a la opción1 y *S2* a la opción2.
1. Guarde los productos.
1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** y habilite *Agregar código de tienda a la dirección URL* = *Sí*.
1. Abra la tienda y compre el producto agrupado.
1. Corre dos veces.
1. Volver a la categoría *CAT*.

<u>Resultados esperados</u>:

El producto *bundle1* no tiene existencias.

<u>Resultados reales</u>:

El producto *bundle1* está visible con precio = *$0*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
