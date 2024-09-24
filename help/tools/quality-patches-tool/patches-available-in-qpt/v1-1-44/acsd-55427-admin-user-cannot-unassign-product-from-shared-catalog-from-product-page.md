---
title: "ACSD-55427: un administrador no puede anular la asignación de un producto de **[!UICONTROL Product in Shared Catalogs]** en la página del producto"
description: Aplique el parche ACSD-55427 para corregir el problema de Adobe Commerce en el que no se puede quitar la asignación de un producto de **[!UICONTROL Product in Shared Catalogs]**.
feature: Products, B2B
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-55427: un administrador no puede anular la asignación de un producto de **[!UICONTROL Product in Shared Catalogs]** en la página del producto

La revisión ACSD-55427 corrige el problema en el cual no se puede anular la asignación de un producto de **[!UICONTROL Product in Shared Catalogs]** en la página del producto en el catálogo en el Administrador de Commerce. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44. El ID del parche es ACSD-55427. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No puede anular la asignación de un producto de **[!UICONTROL Product in Shared Catalogs]** en la página del producto en el catálogo en el Administrador de Commerce.

<u>Pasos a seguir</u>:

Requisitos previos: Adobe Commerce instalado con B2B y **[!UICONTROL Shared Catalogs]** habilitado.
1. Cree un producto.
1. Vaya al panel del catálogo compartido y abra el catálogo compartido predeterminado.
1. Asigne el producto al catálogo predeterminado y establezca un precio inferior al precio del producto.
1. Guarde el catálogo compartido.
1. Ejecute [!UICONTROL CRON] para actualizar los consumidores/indexadores.
1. Abra el producto y elimínelo de la sección **[!UICONTROL Product in Shared Catalogs]**.

<u>Resultados esperados</u>:

El producto debe eliminarse de la sección **[!UICONTROL Product in Shared Catalogs]**.

<u>Resultados reales</u>:

El producto aún se muestra en la sección **[!UICONTROL Product in Shared Catalogs]**.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
