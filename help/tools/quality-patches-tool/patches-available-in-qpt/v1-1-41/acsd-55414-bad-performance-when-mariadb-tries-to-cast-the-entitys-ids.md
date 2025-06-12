---
title: 'ACSD-55414: mal rendimiento cuando MariaDB intenta convertir entitys_ids'
description: Aplique el parche ACSD-55414 para solucionar el problema de Adobe Commerce cuando MariaDB intente convertir entitys_ids de cadena a entero, lo que dificulta el rendimiento de la reindexación.
feature: Attributes
role: Admin, Developer
exl-id: 76309cef-559e-4a55-a27b-7d807ef9f74e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-55414: rendimiento incorrecto cuando MariaDB intenta convertir `entitys_ids`

El parche ACSD-55414 corrige el problema en el que el rendimiento de la reindexación se ve obstaculizado cuando MariaDB intenta convertir `entitys_ids` de cadena a entero. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.41. El ID del parche es ACSD-55414. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El rendimiento de la reindexación se ve obstaculizado cuando MariaDB intenta convertir el `entitys_ids` de cadena a entero.

<u>Pasos a seguir</u>:

1. Actualice `setup/performance-toolkit/profiles/ce/small.xml` configurando *50000* productos simples.
1. Genere este perfil ejecutando el comando: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Ejecutar reindexación: `bin/magento indexer:reindex catalog_product_attribute`.

<u>Resultados esperados</u>:

La reindexación tarda un tiempo razonable en completarse.

<u>Resultados reales</u>:

La reindexación tarda demasiado en completarse.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
