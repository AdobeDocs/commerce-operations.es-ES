---
title: 'ACSD-64149: Los segmento de cliente con una [!UICONTROL Date range] condición se pueden guardar cuando solo se edita una fecha'
description: Aplicar el ACSD-64149 parche para solucionar el problema de Adobe Systems Commerce, por el que los segmento de clientes con una condición **[!UICONTROL Date range]** se pueden guardar cuando solo se edita una de las fechas.
feature: Customers, Admin Workspace
role: Admin, Developer
exl-id: 5423bbd3-75e9-4137-b2d5-3a0ceb3384ad
source-git-commit: 352bbe1c8a14de8ccc24854d251002df9d48e68a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-64149: Los segmento de cliente con una [!UICONTROL Date range] condición se pueden guardar cuando solo se edita una fecha

El parche ACSD-64149 corrige el problema por el que se puede guardar un segmento de cliente con una condición de intervalo de fecha cuando solo se edita una de las fechas. Este parche está disponible cuando se instala 1.1.60 [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) . El ID parche es ACSD-64149. Tenga en cuenta que este problema está programado para solucionarse en Adobe Systems Commerce 2.4.8.

## Productos y versiones afectados

**El parche se crea para Adobe Systems versión de Commerce:**

* Adobe Systems Commerce (todos los métodos implementación) 2.4.6-p8

**Compatible con las versiones de Adobe Systems Commerce:**

* Adobe Systems Commerce (todos los métodos implementación) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>El parche podría aplicarse a otras versiones con nuevas [!DNL Quality Patches Tool] versiones. Para comprobar si el parche es compatible con su versión de Adobe Systems Commerce, actualice el `magento/quality-patches` paquete a la versión más reciente y compruebe la compatibilidad en la [[!DNL Quality Patches Tool]Search para parches Página](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Emitir

Al editar un segmento de cliente existente con una condición en productos dentro del carro de compras especificado por un intervalo de fecha, el consumidor `matchCustomerSegmentProcessor` falla con un error SQL.

<u>Procedimiento</u>:

1. Asegúrese de que el consumidor `matchCustomerSegmentProcessor` está ejecutando:

   ```bash
   $ bin/magento que:cons:st matchCustomerSegmentProcessor
   ```

1. Vaya al **[!UICONTROL Magento backend]** archivo .
1. Vaya a **[!UICONTROL Customers]** > **[!UICONTROL Segments]**.
1. Haga clic en **[!UICONTROL Add Segment]**.
1. Introduzca un **[!UICONTROL Segment Name]**, seleccione un sitio web en **[!UICONTROL Assigned to Website]** y asegúrese de que **[!UICONTROL Status]** está configurado como *Activo*.
1. Haga clic en **[!UICONTROL Save and Continue Edit]**.
1. Vaya a la pestaña y añada una nueva condición: *Productos{} > {}Lista* de **[!UICONTROL Conditions]** productos{*}*.
1. añadir una subcondición para el **[!UICONTROL Date range]** y establezca un archivo .**[!UICONTROL Date range]**
1. Haga clic en el botón de confirmación verde situado junto al **[!UICONTROL Date range]** archivo .
1. **[!UICONTROL Date range]** Haga clic de nuevo, seleccione el selector de fecha, edite uno de los valores de fecha y confirme haciendo clic en el botón verde.

<u>Resultados esperados</u>:

La **[!UICONTROL Date range]** selector no debe añadir tiempo a la fecha al editar.

<u>Resultados reales</u>:

* El **[!UICONTROL Date range]** selector añade hora a la fecha:
   * Una fecha solo tiene la fecha, mientras que la otra tiene la fecha y la hora especificadas.
* El siguiente error aparece en los registros:

  ```
  report.CRITICAL: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 2, query was: SELECT `item`.`quote_id` FROM `quote_item` AS `item`
  INNER JOIN `quote` AS `list` ON item.quote_id = list.entity_id WHERE (list.is_active = 1) AND () [] []
  ```


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función de su método implementación:

* Adobe Systems de comercio o Magento Open Source local: [[!DNL Quality Patches Tool] uso >](/help/tools/quality-patches-tool/usage.md) en el [!DNL Quality Patches Tool] guía.
* Adobe Systems Commerce on infraestructura en la nube: Upgrades and Patches > Aplicar Patches in the Commerce on Cloud Infrastructure guía.

## Lecturas relacionadas

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: Un herramienta de autoservicio para parches](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) de calidad en el Herramientas guía.
