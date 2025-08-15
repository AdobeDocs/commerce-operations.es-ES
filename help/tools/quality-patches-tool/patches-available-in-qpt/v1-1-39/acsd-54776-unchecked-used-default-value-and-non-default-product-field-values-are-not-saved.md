---
title: 'ACSD-54776: los valores de campo de producto [!UICONTROL Use Default Value] sin marcar y no predeterminados no se guardan para el segundo sitio web, tienda y vista de tienda'
description: Aplique el parche ACSD-54776 para corregir el problema de Adobe Commerce en el que los valores de los campos de producto [!UICONTROL Use Default Value] y no predeterminados no marcados no se guardan para la segunda vista del sitio web, la tienda y la tienda.
feature: Products
role: Admin, Developer
exl-id: d9f63abb-5d00-4777-a186-1120344af018
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-54776: *[!UICONTROL Use Default Value]* sin marcar y los valores de campo de producto no predeterminados no se guardan

>[!NOTE]
>
>Este parche reemplaza el parche [ACSD-51984](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-35/acsd-51984-unchecked-used-default-value-and-non-default-product-field-values-are-not-saved.md) lanzado en QPT 1.1.35.

La revisión ACSD-54776 corrige el problema en el cual los valores de **[!UICONTROL Use Default Value]** sin marcar y los campos de producto no predeterminados no se guardan para la segunda vista del sitio web, la tienda y la tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39. El ID del parche es ACSD-54776. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p4, 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los valores de campo de producto *[!UICONTROL Use Default Value]* y no predeterminado que no están marcados no se guardan para el segundo sitio web, tienda y vista de tienda.

<u>Pasos a seguir</u>:

1. Vaya al servidor y vaya a **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** y cree un nuevo sitio web, tienda y vista de tienda.
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**, cree un producto simple, guárdelo y asigne el producto a ambos sitios web desde **[!UICONTROL Product in Websites]**.
1. Cambie el ámbito a la vista de tienda recién creada en el paso 2.
1. Vaya a **[!UICONTROL Search Engine Optimization]** y desmarque las casillas de verificación de **[!UICONTROL Use Default Value]** para [!UICONTROL Meta Title], [!UICONTROL Meta Keywords] y [!UICONTROL Meta Description].
1. Limpie el texto de los campos: *[!UICONTROL Meta Title]*, *[!UICONTROL Meta Keywords]* y *[!UICONTROL Meta Description]*, y haga clic en **[!UICONTROL Save]**.
1. Volver a **[!UICONTROL Search Engine Optimization]**.

<u>Resultados esperados</u>

Se guardan los valores de los campos y las casillas de verificación.

<u>Resultados reales</u>

Los valores de los campos y las casillas de verificación no se guardan.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es>) en la guía [!DNL Quality Patches Tool].
