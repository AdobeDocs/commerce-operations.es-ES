---
title: 'ACSD-65540: Se produce un error de SQL debido a la falta de la función REGEXP_LIKE en las actualizaciones de company_structure'
description: Aplique el parche ACSD-65540 para corregir el problema de Adobe Commerce en el que se produce un error SQL debido a la falta de la función REGEXP_LIKE en las actualizaciones company_structure.
feature: B2B
role: Admin, Developer
source-git-commit: 105bc9bd1b234a7cc582f072f4ede03b82cc81bc
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---


# ACSD-65540: Se produce un error de SQL debido a la función `REGEXP_LIKE` que falta en `company_structure` actualizaciones

La revisión ACSD-65540 corrige el problema en el que se produce un error de SQL debido a que falta la función `REGEXP_LIKE` en las actualizaciones de `company_structure`. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. El ID del parche es ACSD-65540.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce B2B (todos los métodos de implementación) 1.5.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce B2B (todos los métodos de implementación) 1.5.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Error de sintaxis SQL debido a que falta la función `REGEXP_LIKE` en las actualizaciones de `company_structure`.

<u>Pasos a seguir</u>:

1. Actualizar [!DNL B2B] a la versión 1.5.2.
1. Ejecute el siguiente comando:

```
bin/magento setup:upgrade
```

<u>Resultados esperados</u>:

La actualización se ha completado correctamente.

<u>Resultados reales</u>:

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^331(/.+)?$'))
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
