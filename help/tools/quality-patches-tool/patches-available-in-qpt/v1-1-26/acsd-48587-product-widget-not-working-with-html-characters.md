---
title: 'ACSD-48587: el widget de producto no funciona con SKU que contienen caracteres HTML'
description: Aplique el parche ACSD-48587 para solucionar el problema de Adobe Commerce, donde los caracteres especiales de HTML en las reglas de coincidencia de widget de productos impiden que se muestren los productos coincidentes.
feature: Admin Workspace, CMS, Orders, Products
role: Admin
exl-id: c3e31835-03be-46b4-a080-09edf55b5b4e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48587: el widget de producto no funciona con SKU que contienen caracteres HTML

El parche ACSD-48587 corrige el problema en el que los caracteres especiales de HTML en las reglas de coincidencia de widget de productos impiden que se muestren los productos coincidentes. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26. El ID del parche es ACSD-48587. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El widget de producto no funciona con SKU que contengan los símbolos *&quot;&amp;&quot;*.

<u>Pasos a seguir</u>:

1. Cree un producto que contenga *&quot;&amp;&quot;* en el SKU (por ejemplo, s000&amp;01).
1. Edite el contenido de una página de CMS en *Page Builder*.
1. Agregue un widget de productos.
1. Edite el widget y establezca **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]**.
1. Escriba el SKU que contiene *&quot;&amp;&quot;* en el campo SKU del producto.
1. Guarde el contenido y la página de CMS.
1. Compruebe el contenido de *CMS Page* para obtener la *vista previa de Page Builder* y la tienda de productos.

<u>Resultados esperados</u>:

El producto con *&quot;&amp;&quot;* en el SKU se muestra en la vista previa de Page Builder y en la tienda.

<u>Resultados reales</u>:

El producto con *&quot;&amp;&quot;* en el SKU no se muestra en la vista previa de Page Builder.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
