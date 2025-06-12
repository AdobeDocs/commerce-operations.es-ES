---
title: 'ACSD-50621: Los precios de nivel de diferentes sitios web en el catálogo compartido no son visibles'
description: Aplique el parche ACSD-50621 para corregir el problema de Adobe Commerce en el que los precios de nivel de diferentes sitios web en el catálogo compartido no son visibles al editarlos en un entorno de varios sitios web.
feature: Catalog Management, Orders
role: Admin
exl-id: 2256dee7-e544-4723-9753-ba9cf7247880
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-50621: Los precios de nivel de diferentes sitios web en el catálogo compartido no son visibles

El parche ACSD-50621 soluciona el problema de que los precios de nivel de los distintos sitios web del catálogo compartido no son visibles al editarlos en un entorno de varios sitios web. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.32. El ID del parche es ACSD-50621. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los precios de nivel de diferentes sitios web en el catálogo compartido no son visibles al editarlos en un entorno de varios sitios web.

<u>Pasos a seguir</u>:

1. Establezca **[!UICONTROL Catalog Price Scope]** en **[!UICONTROL Website]**.
1. Cree un sitio web, una tienda y una vista de tienda adicionales.
1. Cree un producto simple y asígnelo a todos los sitios web.
1. Cree un catálogo compartido personalizado.
1. Vaya a **[!UICONTROL Set Pricing and Structure]** para el catálogo compartido personalizado que ha creado.
1. En el paso 1: seleccione los productos para el catálogo. Añada el producto simple que ha creado.
1. En el paso 2: establezca los precios personalizados y haga clic en **[!UICONTROL Configure]**.
1. Establece diferentes niveles de precios para diferentes sitios web.
1. Seleccione **[!UICONTROL Done]**, haga clic en **[!UICONTROL Generate Catalog]** y luego haga clic en **[!UICONTROL Save]**.
1. Corre cron.
1. Vaya a **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** y verifique el precio del nivel.

<u>Resultados esperados</u>:

Están presentes todos los precios de nivel configurados previamente para diferentes sitios web.

<u>Resultados reales</u>:

Los precios de nivel que se configuraron anteriormente no están presentes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
