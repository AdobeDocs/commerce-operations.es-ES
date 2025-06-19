---
title: 'ACSD-49973: rendimiento mejorado al recuperar productos agrupados mediante  [!DNL GraphQL]'
description: Aplique el parche ACSD-49973 para corregir el problema de Adobe Commerce donde se produce una degradación del rendimiento al recuperar productos agrupados mediante  [!DNL GraphQL].
feature: GraphQL, Products
role: Admin
exl-id: d4817522-65dd-4ac8-8759-8518818684ed
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# ACSD-49973: rendimiento mejorado al recuperar productos agrupados mediante [!DNL GraphQL]

El parche ACSD-49973 mejora el rendimiento al recuperar productos agrupados mediante [!DNL GraphQL]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30. El ID del parche es ACSD-49973. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce una degradación del rendimiento al recuperar productos agrupados mediante [!DNL GraphQL].

<u>Requisitos previos</u>:

Cree 2000 paquetes de productos usando [Performance toolkit](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html).

<u>Pasos a seguir</u>:

1. Habilitar el registrador de consultas [!DNL DB]:

   ```
   bin/magento dev:query-log:enable
   ```

1. Ejecute la siguiente consulta [!DNL GraphQL]:

   ```GraphQL
   {
     products(
       search: "bundle"
       pageSize: 2000,
       sort: { relevance: DESC }
     ) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Buscar solicitudes en la tabla `catalog_product_bundle_selection` de `var/log/db.log`.

<u>Resultados esperados</u>:

Las solicitudes para la tabla `catalog_product_bundle_selection` no deben estar presentes en `var/log/db.log`.

<u>Resultados reales</u>:

Hay 2000 solicitudes a `catalog_product_bundle_selection` tabla que se activan al mismo tiempo, lo que provoca una degradación del rendimiento.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool]
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
