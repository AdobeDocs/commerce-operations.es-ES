---
title: "ACSD-50512: Error al actualizar la fecha de inicio de una actualización de ensayo de producto descargable"
description: Aplique el parche ACSD-51892 para corregir el problema de rendimiento de Adobe Commerce donde el error *El vínculo descargable no está relacionado con el producto.Compruebe el vínculo e inténtelo de nuevo*, se produce al actualizar la fecha de inicio de una actualización de ensayo de producto descargable.
feature: Products, Staging
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-50512: Error al actualizar la fecha de inicio de la actualización descargable del ensayo del producto

El parche ACSD-50512 corrige el problema donde el error *El vínculo descargable no está relacionado con el producto. Compruebe el vínculo e inténtelo de nuevo*, esto ocurre al actualizar la fecha de inicio de una actualización de ensayo de producto descargable. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.33. El ID del parche es ACSD-51502. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El error *El vínculo descargable no está relacionado con el producto. Compruebe el vínculo e inténtelo de nuevo*, esto ocurre al actualizar la fecha de inicio de una actualización de ensayo de producto descargable.

<u>Pasos a seguir</u>:

1. Cree un producto descargable con *vínculos descargables* y *vínculos de ejemplo*.
1. Cree una actualización programada para el mismo producto y guarde el producto.
1. Edite la actualización programada preconfigurada (del paso 2) y cambie la fecha de inicio.
1. Guarde la actualización programada.

<u>Resultados esperados</u>:

Los cambios realizados en la actualización programada se han guardado correctamente.

<u>Resultados reales</u>:

Recibió el error: *El vínculo descargable no está relacionado con el producto. Verifique el vínculo e inténtelo de nuevo*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
