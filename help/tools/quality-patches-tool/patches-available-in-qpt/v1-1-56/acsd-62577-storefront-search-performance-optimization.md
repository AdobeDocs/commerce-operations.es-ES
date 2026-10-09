---
title: 'ACSD-62577: Optimización del rendimiento de búsqueda en tiendas'
description: Aplique el parche ACSD-62577 para corregir el problema de Adobe Commerce en el que el rendimiento de la búsqueda en la tienda se ve degradado debido a la lenta ejecución de la consulta provocada por una tabla search_query de gran tamaño.
feature: Search
role: Admin, Developer
exl-id: 211c1e3c-0739-4ff6-a25c-b27d335920d1
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%
---
# ACSD-62577: Optimización del rendimiento de búsqueda en tiendas

El parche ACSD-62577 corrige el problema con el rendimiento lento de las consultas de búsqueda de tienda al optimizar tanto los índices de consulta como de tabla. Este parche está disponible con [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. El ID del parche es ACSD-62577. Tenga en cuenta que el problema estaba programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6, 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las tablas grandes de `search_query` ralentizan considerablemente las búsquedas de tienda, lo que aumenta los tiempos de respuesta de front-end debido a consultas ineficientes y a la falta de índices de tabla optimizados.

<u>Pasos a seguir</u>:

1. Configure Adobe Commerce Develop utilizando el kit de herramientas de rendimiento `small.xml`.
1. Obtenga acceso a la línea de comandos de SQL y elimine la tabla `search_query` mediante los siguientes comandos:

   ```text
   SET FOREIGN_KEY_CHECKS = 0;  
   DROP TABLE search_query;  
   SET FOREIGN_KEY_CHECKS = 1;  
   ```

1. Rellene la tabla `search_query` con un gran número de registros, por ejemplo: 4 millones de registros.
1. Déclencheur la reindexación y vaciado de cachés.

   ```shell
   bin/magento indexer:reindex  
   bin/magento c:c  
   bin/magento c:f  
   ```

1. Habilitar registros de depuración de base de datos:

   ```shell
   bin/magento dev:query-log:enable  
   ```

1. Busca un término en la barra de búsqueda de la tienda, por ejemplo,
   `http://your_magento_instance/default/catalogsearch/result/?q=test.`
1. Compruebe `db.log` el tiempo de ejecución de la consulta para el siguiente SQL:

   ```sql
   SELECT COUNT(*) FROM (  
   SELECT DISTINCT `main_table`.`query_text`  
   FROM `search_query` AS `main_table`  
   WHERE (main_table.store_id IN (1))  
   AND (main_table.num_results > 0)  
   ORDER BY `main_table`.`popularity` DESC  
   LIMIT 100  ) AS `result` WHERE (result.query_text = 'test')  
   ```

<u>Resultados esperados</u>:

El tiempo de ejecución de la consulta está optimizado, lo que da como resultado un aumento menos significativo del tiempo de respuesta al procesar tablas grandes de `search_query`.

<u>Resultados reales</u>:

El tiempo de ejecución de la consulta aumenta significativamente debido a la administración ineficaz de la tabla `search_query` de gran tamaño:

```text
TIME: 10.8520 seconds  
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
