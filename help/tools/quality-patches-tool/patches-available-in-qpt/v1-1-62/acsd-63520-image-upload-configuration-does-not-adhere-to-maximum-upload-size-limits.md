---
title: 'ACSD-63520: las imágenes cargadas a través de la configuración de carga de imágenes superan los límites de tamaño configurados'
description: Aplique el parche ACSD-63520 para corregir el problema de Adobe Commerce en el que las imágenes cargadas a través de la configuración de carga de imágenes en el panel de administración no se adhieren a los límites configurados de tamaño máximo de carga.
feature: Media, Products
role: Admin, Developer
source-git-commit: 987d335f03d552763f75adb73890787abf235e66
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---


# ACSD-63520: las imágenes cargadas a través de [!UICONTROL Image Upload Configuration] superan los límites de tamaño configurados

El parche ACSD-63520 resuelve un problema en el cual las imágenes cargadas a través de [!UICONTROL Images Upload Configuration] no respetan los límites configurados de tamaño máximo de carga. Para solucionarlo, configure la configuración de [!UICONTROL Images Upload Configuration] en el panel [!UICONTROL Admin]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62. El ID del parche es ACSD-63520. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.7

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de [!DNL Adobe Commerce], actualice el paquete de `magento/quality-patches` a la versión más reciente y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las imágenes cargadas a través de [!UICONTROL Images Upload Configuration] en el panel [!UICONTROL Admin] no respetan el límite de tamaño máximo de carga.

<u>Pasos a seguir</u>:

1. Inicie sesión en el panel **[!UICONTROL Admin]**.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Images Upload Configuration]** y establezca:
   * Calidad: 100
   * Habilitar cambio de tamaño de front-end: sí
   * Anchura máxima: 800
   * Altura máxima: 600
1. Expanda **[!UICONTROL Media Gallery Image Optimization]** y establezca:
   * Habilitar optimización de imágenes: sí
   * Anchura máxima: 1000
   * Altura máxima: 1000
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Configurable Product]**.
   1. Agregar **[!UICONTROL Product Name]**, **[!UICONTROL SKU]** y **[!UICONTROL Price]**.
   1. Haga clic en **[!UICONTROL Create Configurations]**, seleccione **[!UICONTROL Attributes]** y haga clic en **[!UICONTROL Next]**.
   1. Elija tamaños (S, M, L, XL), haga clic en **[!UICONTROL Next]**.
   1. En **[!UICONTROL Images]**, seleccione **[!UICONTROL Apply single set of images to all SKUs]**.
   1. Cargue una imagen (mínimo 1024 x 1024), haga clic en **[!UICONTROL Next]**.
   1. Haga clic en **[!UICONTROL Generate Product]**.
1. Haga clic en **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

Las imágenes deben seguir los límites configurados de tamaño de carga y cambio de tamaño.

<u>Resultados reales</u>:

Las imágenes no cambian de tamaño y superan los límites de tamaño de carga configurados.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
