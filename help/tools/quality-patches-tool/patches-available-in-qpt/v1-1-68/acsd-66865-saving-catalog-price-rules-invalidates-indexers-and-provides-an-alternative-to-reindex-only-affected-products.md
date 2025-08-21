---
title: 'ACSD-66865: al guardar un [!UICONTROL Catalog Price Rule], se invalidan los indexadores y se proporciona una alternativa para reindexar solo los productos afectados'
description: Aplique el parche ACSD-66865 para solucionar el problema de Adobe Commerce donde  al guardar [!UICONTROL Catalog Price Rules] se invalidan los indizadores y se proporciona una alternativa para reindexar solo los productos afectados.
feature: Price Rules, Price Indexer
role: Admin, Developer
type: Troubleshooting
source-git-commit: fe36522b99ec3fe7189d164cfca6127c9119e06e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-66865: al guardar un **[!UICONTROL Catalog Price Rule]**, se invalidan los indexadores y se proporciona una alternativa para reindexar solo los productos afectados

El parche ACSD-66865 corrige el problema por el cual guardar un **[!UICONTROL Catalog Price Rule]** invalida los indexadores y proporciona una alternativa para reindexar solo los productos afectados. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. El ID del parche es ACSD-66865. Tenga en cuenta que este problema se solucionó en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Guardar un **[!UICONTROL Catalog Price Rule]** hace que todos los indizadores se invaliden, lo que activa reíndices completos en lugar de reindexar únicamente los productos afectados.

<u>Pasos a seguir</u>:

1. Asegúrese de que cron no esté en ejecución y de que todos los indexadores estén configurados para actualizarse según lo programado (excepto `customer_grid`, que puede actualizarse al guardar).
2. Ejecute un reíndice manual completo con el comando: `php bin/magento indexer:reindex`.
3. Comprobar que todos los índices muestran el estado *[!UICONTROL Ready]* con *0* elementos en el registro de pendientes.
4. En la barra lateral de Administración, vaya a **[!UICONTROL Marketing]** > *[!UICONTROL Promotions]* > **[!UICONTROL Catalog Price Rule]**. Cree una regla de precios de catálogo activa para un solo producto (por ejemplo, con una condición *SKU*).
5. Ejecute el comando: `php bin/magento indexer:status` para comprobar el estado del indizador.
6. Observe que varios índices están marcados como **[!UICONTROL Reindex Required]** aunque solo un producto se vea afectado.

<u>Resultados esperados</u>:

Solo se identifican los datos del producto afectados y se activa un reíndice parcial en lugar de un reíndice completo en todos los indexadores.

<u>Resultados reales</u>:

Se activa un reíndice completo para todos los indizadores, incluso cuando solo un producto se ve afectado por **[!UICONTROL Catalog Price Rule]**.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
