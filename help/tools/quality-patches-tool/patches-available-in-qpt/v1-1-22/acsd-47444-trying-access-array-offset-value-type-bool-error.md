---
title: 'ACSD-47444: error _[!UICONTROL Trying to access array offset on value of type bool]_ al acceder a ciertas rutas de categoría no existentes para productos conocidos en PHP 7.4'
description: Aplique el parche ACSD-47444 para corregir el problema de Adobe Commerce donde hay un error _[!UICONTROL Trying to access array offset on value of type bool]_ al acceder a ciertas rutas de categoría no existentes para productos conocidos, en PHP 7.4.
feature: Categories, Products
role: Admin
exl-id: 9f04ee28-d22c-4fdf-9228-e436abe973e8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-47444: error _[!UICONTROL Trying to access array offset on value of type bool]_al acceder a determinadas rutas de categoría no existentes para productos conocidos en PHP 7.4

El parche ACSD-47444 resuelve el problema en el que se ve un error de _[!UICONTROL Trying to access array offset on value of type bool]_al acceder a ciertas rutas de categoría no existentes para productos conocidos en PHP 7.4. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.22.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Experimenta el siguiente error: _[!UICONTROL Trying to access array offset on value of type bool]_al acceder a ciertas rutas de categoría no existentes para productos conocidos, en PHP 7.4.

<u>Requisitos previos</u>:

PHP 7.4.

<u>Pasos a seguir</u>:

1. Cree un nuevo producto con el nombre &quot;test&quot;.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** > conjunto **[!UICONTROL Generate "category/product" URL Rewrites]** = _No_.
1. Vaya a la tienda y visite la URL como ../abc/test.html (&quot;abc&quot; - no debería existir).

<u>Resultados esperados</u>:

404 páginas.

<u>Resultados reales</u>:

Error 500:

_[!UICONTROL Notice: Trying to access array offset on value of type bool in /app/code/Magento/CatalogUrlRewrite/Model/Storage/DynamicStorage.php on line 182]_

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
