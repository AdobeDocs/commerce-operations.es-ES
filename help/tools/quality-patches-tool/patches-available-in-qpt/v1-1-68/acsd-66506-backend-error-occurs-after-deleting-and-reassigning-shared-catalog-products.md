---
title: 'ACSD-66506: El error del servidor se produce después de eliminar y reasignar productos de catálogo compartido'
description: Aplique el parche ACSD-66506 para corregir el problema de Adobe Commerce en el que el back-end genera el error * El producto solicitado no existe. Compruebe el producto e inténtelo de nuevo* después de eliminar los productos asignados anteriormente y asignar nuevos a un catálogo compartido.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8f77101832ccfb415d040c202f0fc7221f97419a
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# ACSD-66506: El error del servidor se produce después de eliminar y reasignar productos de catálogo compartido

La revisión ACSD-66506 corrige el problema en el cual el servidor genera el error *El producto solicitado no existe. Compruebe el producto y vuelva a intentarlo* después de eliminar los productos asignados anteriormente y asignar nuevos productos a un catálogo compartido. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. El ID del parche es ACSD-66506. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Después de eliminar los productos asignados anteriormente y asignar nuevos a **[!UICONTROL Shared Catalog]**, el servidor devuelve el siguiente error: *El producto solicitado no existe. Compruebe el producto y vuelva a intentarlo*

<u>Pasos a seguir</u>:

1. Crear algunos productos con el kit de herramientas de rendimiento: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`
1. Vaya a la configuración de **[!UICONTROL [!DNL B2B] Features]** y establezca **[!UICONTROL Enable Company]** y **[!UICONTROL Enable Shared Catalog]** en `Yes`.
1. Crear un nuevo catálogo compartido.
1. Asigne todos los productos generados al catálogo compartido recién creado.
1. Use **[!UICONTROL Product Import]** para eliminar un producto que se asignó al catálogo compartido.
   1. Exportar un producto filtrado por SKU.
   1. Seleccione **[!UICONTROL Import Behavior: Delete]** y luego importe el mismo archivo.
1. Abra **[!UICONTROL Shared Catalog]** y configure los precios y la estructura.
   1. Seleccione **[!UICONTROL Set Pricing and Structure]**.
   1. Haga clic en **[!UICONTROL Next]** y luego en **[!UICONTROL Generate Catalog]**.
   1. Haga clic en **[!UICONTROL Save]**.

<u>Resultados esperados</u>:

No se produce ningún error y los productos permanecen en el catálogo compartido aunque se produzca un error.

<u>Resultados reales</u>:

Se produce un error: *El producto solicitado no existe. Compruebe el producto y vuelva a intentarlo*. Todos los productos se eliminarán del catálogo compartido.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
