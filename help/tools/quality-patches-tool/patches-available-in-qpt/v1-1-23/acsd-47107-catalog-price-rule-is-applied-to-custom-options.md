---
title: 'ACSD-47107: la regla de precio de catálogo se aplica a las opciones personalizadas'
description: Aplique el parche ACSD-47107 para corregir el problema de Adobe Commerce en el que la regla de precio de catálogo se aplica a las opciones personalizadas.
feature: Catalog Management, Orders, Price Rules
role: Developer
exl-id: 6fcf896b-ffa9-4cfb-926a-21659ac9f116
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-47107: la regla de precio de catálogo se aplica a las opciones personalizadas

El parche ACSD-47107 corrige el problema en el que la regla de precio de catálogo se aplica a las opciones personalizadas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.23. El ID del parche es ACSD-47107. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.4-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La regla de precio de catálogo se aplica a las opciones personalizadas.

<u>Pasos a seguir</u>:

1. Cree una regla de precios de catálogo.
1. Configúrelo en *Aplicar como porcentaje del precio original* y agregue un descuento del 10%.
1. Seleccione cualquier producto.
1. Cree algunas opciones personalizadas.
1. Comprueba el precio en el front-end.

<u>Resultados esperados</u>:

La regla de precio de catálogo no se aplica a las opciones personalizadas; solo se aplica al precio original del producto.

<u>Resultados reales</u>:

La regla de precio de catálogo se aplica a las opciones personalizadas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
