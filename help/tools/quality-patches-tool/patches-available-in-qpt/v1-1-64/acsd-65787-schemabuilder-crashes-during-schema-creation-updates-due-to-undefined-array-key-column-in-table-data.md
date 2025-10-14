---
title: 'ACSD-65787: SchemaBuilder se bloquea durante la creación o actualización del esquema debido a la clave de matriz "column" no definida en los datos de la tabla'
description: Aplique el parche ACSD-65787 para corregir el problema de Adobe Commerce en el que la clase SchemaBuilder se bloquea durante la creación del esquema o se actualiza debido a una "columna" de clave de matriz no definida al procesar los datos de tabla.
feature: Backend Development, Deploy
role: Admin, Developer
exl-id: c01d1799-13fe-4657-a480-698efbe45a30
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-65787: `SchemaBuilder` se bloquea durante la creación o actualización del esquema debido a una &quot;columna&quot; de clave de matriz no definida en los datos de la tabla

El parche ACSD-65787 corrige el problema en el que la clase `SchemaBuilder` se bloquea durante la creación o las actualizaciones de esquemas debido a una &quot;columna&quot; de clave de matriz no definida al procesar los datos de tabla. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. El ID del parche es ACSD-65787. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La clase `SchemaBuilder` se bloquea durante la creación del esquema o se actualiza debido a una &quot;columna&quot; de clave de matriz no definida al procesar los datos de tabla.

<u>Pasos a seguir</u>:

1. Ejecute el siguiente comando:

```
bin/magento setup:upgrade
```

<u>Resultados esperados</u>:

Sin errores.

<u>Resultados reales</u>:

```
Error "Warning: Undefined array key "column" in SchemaBuilder.php on line 90
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
