---
title: 'ACSD-64111: corrige el error *InvalidArgumentException: la clase no existe* al establecer condiciones anidadas para un componente de producto en  [!DNL Page Builder]'
feature: Products, Page Builder
role: Admin, Developer
exl-id: dc39c65b-fb78-4105-b0e8-92a78b49adaf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-64111: corrige el error *InvalidArgumentException: la clase no existe* al establecer condiciones anidadas para un componente de producto en [!DNL Page Builder]

La revisión ACSD-64111 corrige el problema donde *InvalidArgumentException: la clase no existe* se produce un error en `vendor/magento/module-rule/Model/ConditionFactory.php:50` al establecer condiciones anidadas para un componente de producto en [!DNL Page Builder]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60. El ID del parche es ACSD-64111. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación)  2.4.6-p8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Error *InvalidArgumentException: la clase no existe en /app/&lt;id de proyecto\>/vendor/magento/module-rule/Model/ConditionFactory.php* se produce al agregar un *[!UICONTROL Conditions Combination]* en la condición del widget [!DNL Page Builder] Productos.

<u>Pasos a seguir</u>:

1. Inicie sesión en Adobe Commerce admin.
1. Vaya a **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**.
1. Agregar una página nueva (o editar una página existente).
1. Expanda la sección **[!UICONTROL Content]** y haga clic en **[!UICONTROL Edit with Page Builder]**.
1. Agregue una fila nueva y, a continuación, el widget **[!UICONTROL Products]**.
1. Configure el widget **[!UICONTROL Products]**.
1. Seleccione **[!UICONTROL Condition]** en **[!UICONTROL Select Products By]**.
1. Agregue una nueva condición y seleccione **[!UICONTROL Conditions Combination]** en la lista desplegable.

<u>Resultados esperados</u>:

No hay errores en los registros.

<u>Resultados reales</u>:

La siguiente excepción se registra en los registros:

*report.CRITICAL: InvalidArgumentException: la clase no existe en vendor/magento/module-rule/Model/ConditionFactory.php:50*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
