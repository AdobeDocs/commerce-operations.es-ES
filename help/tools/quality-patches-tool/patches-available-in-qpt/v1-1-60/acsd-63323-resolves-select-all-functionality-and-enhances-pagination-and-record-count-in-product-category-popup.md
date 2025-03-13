---
title: 'ACSD-63323: resuelve la funcionalidad [!UICONTROL Select All] y mejora la paginación y el recuento de registros en la ventana emergente de categoría de producto'
description: Aplique el parche ACSD-63323 para corregir el problema de Adobe Commerce en el que la opción [!UICONTROL Select All] no funciona al agregar productos a una categoría. Además, garantiza que la paginación y la etiqueta de recuento de registros funcionen correctamente al añadir productos a una categoría a través de la cuadrícula emergente.
feature: Products
role: Admin, Developer
source-git-commit: f3f0cc93adf83b485ca50811adcc561638e3c5c2
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# ACSD-63323: resuelve la funcionalidad [!UICONTROL Select All] y mejora la paginación y el recuento de registros en la ventana emergente de categoría de producto

El parche ACSD-63323 corrige el problema en el que la opción **[!UICONTROL Select All]** no funciona al agregar productos a una categoría. Además, garantiza que la paginación y la etiqueta de recuento de registros funcionen correctamente al añadir productos a una categoría a través de la cuadrícula emergente. Esta revisión está disponible cuando [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) está instalado. El ID del parche es ACSD-63323. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Corrige el problema en el cual la opción **[!UICONTROL Select All]** no funciona en Administración > **[!UICONTROL Categories]** > Elegir una categoría > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**. También ayuda a que la paginación y la etiqueta de recuento de registros funcionen correctamente al añadir productos a una categoría a través de la cuadrícula emergente.


<u>Pasos a seguir</u>:

1. Genere *1200* productos con el comando:

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Abra **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y vea el número de productos: se encontraron *1200* registros.
1. Abra una categoría predeterminada > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]**.
1. Haga clic en **[!UICONTROL Assign]** > **[!UICONTROL Select All]**.
1. Cambiar el número de productos de la página a valor = *5*.


**Resultados esperados**:

*El mensaje debe ser: 1200 registros encontrados (1200 seleccionados)*

**Resultados reales**:

* La paginación no funciona.
* Se muestra un mensaje incorrecto: *5* registros encontrados (*20* seleccionados)

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.


