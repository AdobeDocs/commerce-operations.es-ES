---
title: 'ACSD-62793: Faltan atributos de fecha y hora en el componente de hora de las exportaciones. Además, si **[!UICONTROL Fields Enclosure]** está habilitado, los valores de atributo deben estar entre comillas dobles'
description: Aplique el parche ACSD-62793 para corregir el problema de Adobe Commerce en el que los atributos datetime de los datos exportados no contienen el componente de tiempo. Además, si **[!UICONTROL Fields Enclosure]** está habilitado, los valores de atributo de la columna *additional_attributes* se escribirán entre comillas dobles.
feature: Attributes, Data Import/Export, Catalog Service
role: Admin, Developer
exl-id: 340dcc84-dcb8-40ed-b2ab-2d950d1dd1ca
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-62793: Faltan atributos de fecha y hora en el componente de hora de las exportaciones. Además, si **[!UICONTROL Fields Enclosure]** está habilitado, los valores de atributo deben estar entre comillas dobles

El parche ACSD-62793 corrige el problema de que a los atributos datetime de los datos exportados les falta el componente de tiempo. Además, si **[!UICONTROL Fields Enclosure]** está habilitado, los valores de atributo de la columna *additional_attributes* se escribirán entre comillas dobles. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. El ID del parche es ACSD-62793. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los atributos de fecha y hora de los datos exportados no incluyen el componente de tiempo. Además, si **[!UICONTROL Fields Enclosure]** está habilitado, los valores de atributo de la columna *additional_attributes* se escribirán entre comillas dobles.

<u>Pasos a seguir</u>:

1. Crear un atributo de producto con **[!UICONTROL Catalog Input Type for Store Owner]** = **[!UICONTROL Date and Time]**.
1. Asigne el atributo al conjunto de atributos **[!UICONTROL Default]**.
1. Cree un producto simple con un valor de fecha y hora para el nuevo atributo.
1. Exporte el producto a un archivo CSV desde **[!UICONTROL System]** > *Transferencia de datos* > **[!UICONTROL Export]**.
1. Compruebe el valor del atributo en la columna *additional_attributes*. Solo tiene la parte de la fecha, pero no la hora.
1. Actualice el valor del atributo para utilizar la hora, p. ej., &quot;08/10/22, 3:20 p. m.&quot;.
1. Importe el archivo CSV.
1. Compruebe la tabla *catalog_product_entity_datetime*.

<u>Resultados esperados</u>:

La fecha y la hora se exportan e importan correctamente.

<u>Resultados reales</u>:

Solo se exporta e importa la parte de fecha.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
