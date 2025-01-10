---
title: 'ACSD-62629: la lista de productos en los widgets muestra categorías incorrectas'
description: Aplique el parche ACSD-62629 para corregir el problema de Adobe Commerce en el que una lista de productos utilizada en widgets no respeta las condiciones de categoría.
feature: Page Content
role: Admin, Developer
source-git-commit: 6440738bf01a95a2f1e666826685d325bf393249
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# ACSD-62629: la lista de productos en los widgets muestra categorías incorrectas

El parche ACSD-62629 corrige el problema de que la lista de productos utilizada en los widgets no respeta las condiciones de categoría. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. El ID del parche es ACSD-62629. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La lista de productos utilizada en los widgets no respeta la condición de categoría.

<u>Pasos a seguir</u>:

1. Cree un(a) [!UICONTROL simple product] denominado TEST y agréguelo a la categoría 1.
1. Cree una actualización de ensayo sin una fecha de finalización para el producto TEST. Espere hasta que se active la actualización.
1. Cree un(a) [!UICONTROL configurable product] denominado(a) PRUEBA 2 con dos productos secundarios y agréguelo a Categoría 2.
1. Cree otro(a) [!UICONTROL simple product] denominado(a) TEST 5 y agréguelo a Category 1.
1. Ejecute un reindexado completo.
1. Vaya a **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** y edite la página principal.
1. Agregar un widget de [!UICONTROL Products] con *[!UICONTROL Appearance]* establecido en *[!UICONTROL Product Carousel]* y *[!UICONTROL Category]* establecido en Categoría 2. Guarde la página.
1. Vaya al front-end y abra la página principal.

<u>Resultados esperados</u>:

Solo el producto TEST 2 (configurable) debe estar presente en la página.

<u>Resultados reales</u>:

Los productos TEST 5 (simple) y TEST 2 (configurable) están presentes en la página.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
