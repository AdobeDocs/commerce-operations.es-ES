---
title: "ACSD-56979: imágenes de producto eliminadas tras la actualización de ensayo eliminada"
description: Aplique el parche ACSD-56979 para corregir el problema de Adobe Commerce en el que las imágenes de producto se eliminan después de eliminar una actualización de ensayo
feature: Products
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-56979: imágenes de producto eliminadas después de actualizar el ensayo

El parche ACSD-56979 corrige el problema por el que las imágenes de producto se eliminan después de eliminar una actualización de ensayo. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49. El ID del parche es ACSD-56979. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con Adobe Commerce y versiones de Magento Open Source:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las imágenes de producto se eliminan después de eliminar una actualización de ensayo.

<u>Pasos a seguir</u>:

1. En la barra lateral de administración de Commerce, vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y cree un producto.
1. En **[!UICONTROL Images and Videos]**, cargue una imagen y guarde el producto.
1. En el cuadro **[!UICONTROL Scheduled Changes]**, seleccione **[!UICONTROL Schedule New Update]**.
   1. Elija una fecha de inicio en unos minutos en el futuro.
   1. No elija una fecha de finalización.
1. En el cuadro **[!UICONTROL Scheduled Changes]**, seleccione el vínculo **[!UICONTROL View/Edit]**.
1. Vaya a **[!UICONTROL Remove from Update]** > **[!UICONTROL Delete the Update]** y seleccione **[!UICONTROL Done]**.
1. Actualice la página.

<u>Resultados esperados</u>:

Dado que la actualización se elimina antes de la fecha de inicio programada, el producto debe seguir siendo el mismo.

<u>Resultados reales</u>:

El contenido de la imagen se pierde y muestra cero bytes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
