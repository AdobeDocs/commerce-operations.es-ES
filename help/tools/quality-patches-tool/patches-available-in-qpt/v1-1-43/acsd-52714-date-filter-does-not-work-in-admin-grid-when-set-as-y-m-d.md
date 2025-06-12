---
title: 'ACSD-52714: El filtro de fecha no funciona en la cuadrícula de administración cuando se establece como d-m-a'
description: Aplique el parche ACSD-52714 para corregir el problema de Adobe Commerce en el que el filtro de fecha no funciona en la cuadrícula de administración cuando el formato de fecha se establece como d-m-a.
feature: Attributes
role: Admin, Developer
exl-id: 4a34900b-9566-41bb-8d3e-18a440117907
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-52714: El filtro de fecha no funciona en la cuadrícula de administración cuando se establece como d-m-a

El parche ACSD-52714 corrige el problema de que el filtro de fecha no funciona en la cuadrícula de administración cuando el formato de fecha se establece como d-m-a. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43. El ID del parche es ACSD-52714. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El filtro de fecha no funciona en la cuadrícula de administración cuando el formato de fecha está establecido como d-m-a.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce limpio.
1. Editar
   `/app/code/Magento/Customer/view/adminhtml/ui_component/customer_listing.xml`
archivo y añadir
   `<dateFormat>Y-MM-dd</dateFormat>`
hasta
   `<column name="created_at" class="Magento\Ui\Component\Listing\Columns\Date" component="Magento_Ui/js/grid/columns/date" sortOrder="100">`
en la etiqueta
   `<dataType>date</dataType>`

1. Vaciar la caché `bin/magento c:f`.
1. Inicie sesión en el administrador y cree un nuevo cliente desde **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.

   * desde: fecha actual menos 1 día
   * hasta: fecha actual

1. Haga clic en **[!UICONTROL Apply Filters]**.

<u>Resultados esperados</u>:

El filtro de fecha de la cuadrícula funciona correctamente, independientemente de la configuración regional establecida.

<u>Resultados reales</u>:

Aparece el siguiente mensaje: *No se encontraron registros*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
