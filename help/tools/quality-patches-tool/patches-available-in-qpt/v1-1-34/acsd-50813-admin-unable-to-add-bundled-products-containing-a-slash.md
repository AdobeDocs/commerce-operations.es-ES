---
title: 'ACSD-50813: el administrador no puede añadir productos agrupados que contengan una barra oblicua'
description: Aplique el parche ACSD-50813 para solucionar el problema de rendimiento de Adobe Commerce en el que el administrador no puede añadir productos agrupados que contengan una barra diagonal (&grave;/&grave;) en el SKU con la funcionalidad *Añadir productos por SKU* al pedido del administrador.
exl-id: ff6fa673-bac1-4ef8-a427-60c2f56068f3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-50813: el administrador no puede añadir productos agrupados que contengan una barra oblicua

El parche ACSD-50813 corrige el problema en el que el administrador no puede agregar al pedido del administrador productos agrupados que contengan una barra diagonal (`/`) en el SKU con la funcionalidad *[!UICONTROL Add Products by SKU]*. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.34. El ID del parche es ACSD-50813. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El administrador no puede agregar al pedido del administrador productos agrupados que contengan una barra diagonal (`/`) en el SKU con la funcionalidad *[!UICONTROL Add Products by SKU]*.

<u>Pasos a seguir</u>:

1. Ir a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Cree un producto sencillo.
1. Cree un nuevo producto agrupado.
1. Agregue una barra diagonal (`/`) en medio del SKU (Ejemplo: *Bu/ndle*).
1. Agregar una opción agrupada con **[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]*.
1. Asigne al menos un producto simple a la opción.
1. Vaya a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** y cree un nuevo pedido.
1. Haga clic en **[!UICONTROL Add Products by SKU]**.
1. Escriba su SKU y haga clic en **[!UICONTROL Add to Order]**.
1. Abra la consola del explorador.
1. Haga clic en **[!UICONTROL Configure]**.

<u>Resultados esperados</u>:

No hay ningún error.

<u>Resultados reales</u>:

Error de JS en la consola:

*Error no detectado: error de sintaxis, expresión no reconocida: div[id=sku_bu/ndle]*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
