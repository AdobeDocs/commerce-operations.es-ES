---
title: 'ACSD-59083: errores de tabla base o vista no encontrados durante actualizaciones simultáneas de mview'
description: Aplique el parche ACSD-59083 para corregir el problema de Adobe Commerce en el que determinadas operaciones de actualización de la base de datos fallan con el error "No se encontró la tabla o vista base".
feature: System
role: Admin, Developer
exl-id: a0fa2ac9-e61f-43d5-81ff-edf178b1abc0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-59083: *No se encontró la tabla o vista base* errores durante las actualizaciones simultáneas de `mview`

El parche ACSD-59083 corrige el problema en el que ciertas operaciones de actualización de la base de datos fallan con el error &quot;No se encontró la tabla o vista base&quot; cuando se ejecutan `mview` actualizaciones simultáneamente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. El ID del parche es ACSD-59083. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.5-p5

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Algunas operaciones de actualización de la base de datos generan errores en &#39;No se encontró la tabla o vista base&#39; cuando se ejecutan simultáneamente `mview` actualizaciones.

<u>Pasos a seguir</u>:

1. Establezca el modo del indizador en **[!UICONTROL Update on Schedule]**.
1. Inserte registros en `cl` tablas utilizando los siguientes comandos SQL:

   ```
   INSERT INTO catalogrule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogsearch_fulltext_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_category_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_attribute_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_category_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_price_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO customer_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO design_config_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO salesrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_product_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_rule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   ```

1. Instale el perfil `setup/performance-toolkit/profiles/ce/small.xml`.
1. Agregue un punto de interrupción en el archivo `magento2ee/lib/internal/Magento/Framework/ForeignKey/Config/DbReader.php` en la línea 72.
1. Borre la caché.
1. Haga clic **[!UICONTROL Add to Cart]** en cualquier producto.
1. Inicie el trabajo cron cuando la ejecución alcance el punto de interrupción.
1. Reanude el proceso después de iniciar el trabajo cron.

<u>Resultados esperados</u>:

Las operaciones de la base de datos se ejecutan correctamente sin errores.

<u>Resultados reales</u>:

Se produce un error durante la ejecución:

```
SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento24.design_config_dummy_cl__tmp663bb682960345_17794892' doesn't exist in /www/magento24/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
