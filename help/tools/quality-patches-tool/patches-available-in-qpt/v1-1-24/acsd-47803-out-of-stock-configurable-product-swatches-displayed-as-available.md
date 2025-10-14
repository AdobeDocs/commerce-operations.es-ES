---
title: 'ACSD-47803: muestras de productos configurables y agotadas que se muestran como disponibles'
description: Aplique el parche ACSD-47803 para solucionar el problema de Adobe Commerce donde las muestras de productos configurables y sin existencias se muestran como disponibles.
feature: Configuration, Orders, Products
role: Admin
exl-id: c1b80949-65ed-4a44-8be4-25decda32142
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-47803: muestras de productos configurables y agotadas que se muestran como disponibles

El parche ACSD-47803 corrige el problema en el que se muestran muestras de productos configurables sin existencias como disponibles. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24. El ID del parche es ACSD-47803. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las muestras de productos configurables y sin existencias se muestran como disponibles.

<u>Pasos a seguir</u>:

>[!NOTE]
>
>Los pasos siguientes hacen referencia a los datos de ejemplo como ejemplo.

1. En el administrador de [!UICONTROL Commerce], vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** y establezca **[!UICONTROL Display Out of Stock Products]** Yes *en*.
1. De nuevo, desde Admin, vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y edite un producto configurable en la página de edición de productos (por ejemplo, el SKU &quot;WB04&quot;, si utiliza datos de ejemplo):
   * Para una de las variantes de configuración, establezca la cantidad en *0* (por ejemplo, para &quot;WB04-M-Purple&quot;).
1. Ahora abra el producto configurable en la tienda.
1. Seleccione el tamaño del producto para la variante configurable sin existencias (es decir, &quot;M&quot;).

<u>Resultados esperados</u>:

Las opciones sin existencias están deshabilitadas y marcadas como [!UICONTROL Out of Stock].

<u>Resultados reales</u>:

Todas las muestras de color están habilitadas, incluso la que es [!UICONTROL Out of Stock].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
