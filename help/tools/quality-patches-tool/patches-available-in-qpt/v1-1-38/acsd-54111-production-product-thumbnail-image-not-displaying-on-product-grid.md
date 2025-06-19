---
title: 'ACSD-54111: la imagen en miniatura del producto no se muestra'
description: Aplique el parche ACSD-54111 para solucionar el problema de Adobe Commerce, donde todas las imágenes se sustituyen por la imagen de marcador de posición de producto predeterminada.
feature: Products
role: Admin, Developer
exl-id: 4615ebf6-aa68-4d49-8d91-e9756b3d4a05
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-54111: la imagen en miniatura del producto no se muestra

El parche ACSD-54111 soluciona el problema de reemplazar todas las imágenes por la imagen de marcador de posición de producto predeterminada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.38. El ID del parche es ACSD-54111. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación): 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación): 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se muestra la imagen en miniatura del producto.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]** > **[!UICONTROL Edit Theme]** > **[!UICONTROL Product Image Watermarks]** > **[!UICONTROL Thumbnail]**.
1. Cargue la imagen con una miniatura y establezca la posición de la imagen como *[!UICONTROL Center]*.
1. Haga clic en **[!UICONTROL Save Configuration]**.
1. Borrar caché.
1. Vaya a la tienda como cliente/invitado.
1. Añadir un producto al carro de compras.
1. Ejecute `bin/magento catalog:image:resize` desde la consola.
1. Abra el minicarrito en el front-end o la cuadrícula de producto en el back-end para ver si las miniaturas de la imagen están visibles.

<u>Resultados esperados</u>:

Las imágenes de producto no se sustituyen por la imagen de marcador de posición.

<u>Resultados reales</u>:

Las imágenes de producto se sustituyen por la imagen de marcador de posición de producto predeterminada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
