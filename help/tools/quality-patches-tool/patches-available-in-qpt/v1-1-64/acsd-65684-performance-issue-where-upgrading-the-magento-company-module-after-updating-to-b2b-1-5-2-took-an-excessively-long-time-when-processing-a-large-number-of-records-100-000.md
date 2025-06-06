---
title: 'ACSD-65684: La actualización de Magento_Company en B2B 1.5.2 es lenta, con más de 100 000 registros en company_structure'
description: Aplique el parche ACSD-65684 para corregir el problema de Adobe Commerce en el que la actualización del módulo Magento_Company en B2B 1.5.2 tarda demasiado debido al procesamiento de un gran número de registros (~100 000+) en la tabla company_structure.
feature: B2B
role: Admin, Developer
source-git-commit: dbf1bf3483aa7e52f5d1c950ab82f504c44fc989
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# ACSD-65684: La actualización de `Magento_Company` en [!DNL B2B] 1.5.2 es lenta, con más de 100 000 registros en `company_structure`

La revisión ACSD-65684 corrige un problema de rendimiento en el que la actualización del módulo `Magento_Company` en [!DNL B2B] 1.5.2 tarda demasiado tiempo al procesar más de 100 000 registros en la tabla `company_structure`. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. El ID del parche es ACSD-65684. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce B2B (todos los métodos de implementación) 1.5.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce B2B (todos los métodos de implementación) 1.5.2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Problema de rendimiento en el cual la actualización del módulo `Magento_Company` en [!DNL B2B] 1.5.2 tarda demasiado cuando se procesan más de 100 000 registros en la tabla `company_structure`.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce 2.4.7-p4 con [!DNL B2B].
1. Agregar 100.000 registros a la tabla `company_structure`.
1. Actualice a Adobe Commerce 2.4.7-p5 y al módulo [!DNL B2B] más reciente (1.5.2).
1. Aplicar parche ACSD-65540.
1. Ejecutar:

```
bin/magento setup:upgrade
```

<u>Resultados esperados</u>:

`setup:upgrade` se completa en un tiempo razonable.

<u>Resultados reales</u>:

`setup:upgrade` tarda demasiado tiempo en completarse.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
