---
title: 'ACSD-53239: el indexador de inventario limpia todas las cachés'
description: Aplique el parche ACSD-53239 para corregir el problema de Adobe Commerce donde el indexador de inventario limpia todas las cachés en el modo [!UICONTROL Update on Schedule].
feature: GraphQL, Inventory, Catalog Management
role: Admin, Developer
exl-id: 69e71e2d-8f26-4200-ad4a-6bd9e45627e4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-53239: el indexador de inventario limpia todas las cachés en el modo [!UICONTROL Update on Schedule]

El parche ACSD-53239 corrige el problema en el que el indizador de inventario limpia todas las cachés en el modo [!UICONTROL Update on Schedule]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.36. El ID del parche es ACSD-53239. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.5-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El indizador de inventario limpia todas las cachés en el modo [!UICONTROL Update on Schedule].

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Catalog Products]** y seleccione unos *1200* productos.
2. Actualice *[!UICONTROL Qty]* a un nuevo valor y haga clic en **[!UICONTROL Save]**.
3. Ejecute `bin/magento cron:run` inmediatamente después de guardar.
4. Ejecute la siguiente consulta de GraphQL:

   ```GraphQL
   {
     storeConfig {
     absolute_footer
     }
   }
   ```

<u>Resultados esperados</u>

La consulta se procesa en el tiempo habitual.

<u>Resultados reales</u>

La consulta se procesa de forma inusualmente lenta.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
