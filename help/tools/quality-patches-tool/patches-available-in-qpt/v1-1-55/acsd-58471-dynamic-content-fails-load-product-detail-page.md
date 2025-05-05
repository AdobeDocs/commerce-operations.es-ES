---
title: 'ACSD-58471: el contenido dinámico no se puede cargar en la página de detalles del producto, cuando se programaron las reglas de precio del catálogo asociadas'
description: Aplique el parche ACSD-58471 para corregir el problema de Adobe Commerce en el que el contenido dinámico no se carga en la página de detalles del producto cuando se programan las reglas de precios del catálogo asociadas.
feature: Catalog Management
role: Admin, Developer
exl-id: 6ff68b74-67fc-400c-aa79-a1274fd19708
source-git-commit: 28390659fe180180c9b2c8d16239008a1f8a510b
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-58471: el contenido dinámico no se puede cargar en la página de detalles del producto, cuando se programaron las reglas de precio del catálogo asociadas

El parche ACSD-58471 soluciona el problema de que el contenido dinámico no se carga en la página de detalles del producto cuando se programan las reglas de precios del catálogo asociadas. El sistema ahora muestra correctamente el contenido dinámico asociado con las reglas de precios de catálogo programadas en la página de detalles del producto. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. El ID del parche es ACSD-58471. Este problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.5-p4

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El contenido dinámico no se carga en la página de detalles del producto cuando las reglas de precios del catálogo están programadas.

<u>Pasos a seguir</u>:

1. Crear un bloque dinámico en Commerce [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Dynamic Blocks]**.
1. Crear un bloque estático en [!UICONTROL Admin] > **[!UICONTROL Content]** > **[!UICONTROL Blocks]**. Utilice widgets para añadir contenido.
1. Cree un producto y añada el bloque CMS a la descripción.
1. Cree una regla de catálogo con una actualización programada y asigne el producto y el bloque dinámico creado en **[!UICONTROL Marketing]** > Promociones > **[!UICONTROL Catalog Products Rules]**.
1. Ejecute el cron y compruebe que la página de detalles del producto muestra el contenido dinámico después de la hora de inicio programada.
1. Cree una regla de catálogo sin una actualización programada y asigne el producto y el bloque dinámico creado en **[!UICONTROL Marketing]** > Promociones > **[!UICONTROL Catalog Products Rules]**.
1. Ejecute el cron y compruebe si la página detallada del producto muestra el contenido dinámico después de la hora programada.


<u>Resultados esperados</u>:

El contenido dinámico se carga después de la hora de inicio programada.

<u>Resultados reales</u>:

El contenido dinámico no se carga.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
