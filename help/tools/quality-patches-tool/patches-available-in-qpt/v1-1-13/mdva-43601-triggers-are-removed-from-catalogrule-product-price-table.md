---
title: 'MDVA-43601: los Déclencheur se eliminan de la tabla "catalog_product_price" después de la reindexación completa'
description: El parche MDVA-43601 corrige el problema en el que los déclencheur se eliminan de la tabla "catalog_product_price" después de un reíndice completo de "catalog_rule" o "catalog_product". Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. El ID del parche es MDVA-43601. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Catalog Management, Orders, Products
role: Admin
exl-id: b9580806-ac35-4c86-8eee-c9f16d654171
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# MDVA-43601: los Déclencheur se eliminan de la tabla &quot;catalog_product_price&quot; después de la reindexación completa

La revisión MDVA-43601 corrige el problema en el cual los déclencheur se eliminan de la tabla `catalogrule_product_price` después de un reíndice completo de `catalogrule_rule` o `catalogrule_product`. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. El ID del parche es MDVA-43601. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los déclencheur se quitan de la tabla `catalogrule_product_price` después de un reíndice completo de `catalogrule_rule` o `catalogrule_product`.

<u>Pasos a seguir</u>:

1. Establecer todos los indizadores en *Actualizar por programación*.
1. Compruebe las déclencheur creadas para la tabla `catalogrule_product_price` ejecutando la siguiente solicitud SQL:

   ```sql
   show triggers like '%catalogrule_%'\G
   ```

1. Reindexe manualmente `catalogrule_rule` o `catalogrule_product` ejecutando el siguiente comando: `bin/magento indexer:reindex catalogrule_rule`
1. Vuelva a comprobar los déclencheur de la tabla `catalogrule_product_price`.

<u>Resultados esperados</u>:

Los déclencheur de la tabla `catalogrule_product_price` se conservan después de un reíndice completo.

<u>Resultados reales</u>:

No se encontraron déclencheur para la tabla `catalogrule_product_price`.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
