---
title: 'ACSD-49839: La estructura y los precios del catálogo compartido generan un error'
description: Aplique el parche ACSD-49839 para corregir el problema de Adobe Commerce en el que la estructura y los precios del catálogo compartido generan un error en el administrador cuando los productos tienen comillas simples o dobles en el SKU.
feature: Admin Workspace, Catalog Management, Categories
role: Admin
exl-id: b74e3926-16c8-4222-b642-ed1b7095dea4
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-49839: La estructura y los precios del catálogo compartido generan un error

El parche ACSD-49839 corrige el problema en el que la estructura y los precios del catálogo compartido genera un error en el administrador cuando los productos tienen comillas simples o dobles en el SKU. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-49839. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La estructura y los precios del catálogo compartido generan un error en el administrador cuando los productos tienen comillas simples o dobles en el SKU.

<u>Pasos a seguir</u>:

1. Configure algunos SKU de productos con un carácter especial, es decir, comillas dobles como:
   *[Producto&quot;12, Producto&quot;14, Producto&quot;15]*.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Add Shared Catalog]** (por ejemplo,*[Probar catálogo compartido]*).
1. Asignar todo **[!UICONTROL Products and Categories]** > **[!UICONTROL Generate Catalog]** > **[!UICONTROL Save]**.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Test Shared Catalog]** > **[!UICONTROL Action]** > **[!UICONTROL Set Pricing and Structure]**.
1. Marque *[!UICONTROL Root Catalog]* para seleccionar todas las categorías y productos.
1. AJAX Observe las peticiones de la en el panel Red.

<u>Resultados esperados</u>:

La estructura y los precios del catálogo compartido no generan un error en el administrador cuando los productos tienen comillas simples o dobles en el SKU.

<u>Resultados reales</u>:

La estructura y los precios del catálogo compartido generan un error en el administrador cuando los productos tienen comillas simples o dobles en el SKU.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
