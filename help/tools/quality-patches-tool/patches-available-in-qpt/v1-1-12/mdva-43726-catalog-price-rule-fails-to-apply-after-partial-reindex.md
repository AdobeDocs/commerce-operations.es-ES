---
title: 'MDVA-43726: La regla de precios de catálogo no se aplica después de una reindexación parcial'
description: El parche MDVA-43726 corrige el problema en el que la regla de precios de catálogo basada en la coincidencia de atributos de nivel de tienda no se aplica después de una reindexación parcial. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-43726. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
exl-id: db536749-eb89-4bb5-9c69-f448f74497b8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# MDVA-43726: La regla de precios de catálogo no se aplica después de una reindexación parcial

El parche MDVA-43726 corrige el problema en el que la regla de precios de catálogo basada en la coincidencia de atributos de nivel de tienda no se aplica después de una reindexación parcial. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-43726. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La regla de precios de catálogo basada en la coincidencia de atributos en el nivel de tienda no se aplica tras una reindexación parcial.

<u>Pasos a seguir</u>:

1. Establezca el modo del indexador para que se ejecute según lo programado.
1. Cree dos atributos de producto configurables. Por ejemplo: Color (Muestra visual) y Tamaño (Muestra de texto).
1. Cree un producto configurable con ambos atributos creados en el paso 2.
1. Después de crear los productos, cree un atributo de tipo **Yes/No** y haga que sea visible en las condiciones de regla.
1. Agregue este atributo al conjunto de atributos predeterminado.
1. Cree una regla de precios de catálogo para aplicarla cuando este atributo esté establecido en **Yes**.
1. Abra uno de los productos simples relacionados con el producto configurable.
1. Cambie el ámbito para almacenar la vista y actualice el valor del atributo a **Yes**.
1. Ejecute `CRON` y compruebe el precio en el front-end.
1. Ejecute un reindexado completo. De nuevo, compruebe el precio en el front-end.
1. Actualice la categoría de producto configurable.
1. Ejecute `CRON` y vuelva a comprobar el precio en el front-end.

<u>Resultados esperados</u>:

La regla de catálogo se aplica correctamente sin una reindexación completa mediante indexadores incrementales.

<u>Resultados reales</u>:

La regla de catálogo no se aplica sin ejecutar una reindexación completa.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
