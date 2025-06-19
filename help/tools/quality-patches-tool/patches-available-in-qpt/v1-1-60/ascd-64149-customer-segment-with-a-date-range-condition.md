---
title: 'ACSD-64149: el segmento de cliente con una condición [!UICONTROL Date range] se puede guardar cuando solo se edita una fecha'
description: Aplique el parche ACSD-64149 para corregir el problema de Adobe Commerce en el que el segmento de cliente con una condición **[!UICONTROL Date range]** se puede guardar cuando solo se edita una de las fechas.
feature: Customers, Admin Workspace
role: Admin, Developer
exl-id: 5423bbd3-75e9-4137-b2d5-3a0ceb3384ad
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-64149: el segmento de cliente con una condición [!UICONTROL Date range] se puede guardar cuando solo se edita una fecha

El parche ACSD-64149 corrige el problema en el que un segmento de cliente con una condición de intervalo de fechas se puede guardar cuando solo se edita una de las fechas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60. El ID del parche es ACSD-64149. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al editar un segmento de cliente existente con una condición en productos dentro del carro de compras especificado por un intervalo de fechas, el consumidor `matchCustomerSegmentProcessor` falla con un error SQL.

<u>Pasos a seguir</u>:

1. Asegúrese de que el consumidor `matchCustomerSegmentProcessor` se está ejecutando:

   ```bash
   $ bin/magento que:cons:st matchCustomerSegmentProcessor
   ```

1. Vaya a **[!UICONTROL Magento backend]**.
1. Ir a **[!UICONTROL Customers]** > **[!UICONTROL Segments]**.
1. Haga clic en **[!UICONTROL Add Segment]**.
1. Escriba un **[!UICONTROL Segment Name]**, seleccione un sitio web en **[!UICONTROL Assigned to Website]** y asegúrese de que **[!UICONTROL Status]** está establecido en *Activo*.
1. Haga clic en **[!UICONTROL Save and Continue Edit]**.
1. Vaya a la ficha **[!UICONTROL Conditions]** y agregue una nueva condición: *Productos{} > {}Lista de productos*{*}*.
1. Agregue una subcondición para **[!UICONTROL Date range]** y establezca una **[!UICONTROL Date range]** válida.
1. Haga clic en el botón de confirmación verde junto a **[!UICONTROL Date range]**.
1. Vuelva a hacer clic en **[!UICONTROL Date range]**, seleccione el selector de fechas, edite uno de los valores de fecha y confirme haciendo clic en el botón verde.

<u>Resultados esperados</u>:

El selector **[!UICONTROL Date range]** no debe agregar la hora a la fecha al editar.

<u>Resultados reales</u>:

* El selector **[!UICONTROL Date range]** agrega hora a la fecha:
   * Una fecha solo tiene la fecha, mientras que la otra tiene la fecha y la hora especificadas.
* El siguiente error aparece en los registros:

  ```
  report.CRITICAL: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 2, query was: SELECT `item`.`quote_id` FROM `quote_item` AS `item`
  INNER JOIN `quote` AS `list` ON item.quote_id = list.entity_id WHERE (list.is_active = 1) AND () [] []
  ```


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura en la nube: Actualizaciones y parches > Aplicar parches en la guía de Commerce en la infraestructura en la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
