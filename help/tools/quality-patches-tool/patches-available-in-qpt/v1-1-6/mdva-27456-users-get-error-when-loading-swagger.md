---
title: 'MDVA-27456: Los usuarios reciben un error al cargar Swagger'
description: El parche MDVA-27456 corrige el problema en el que los usuarios reciben un error al intentar cargar Swagger. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6. El ID del parche es MDVA-27456. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.7.
feature: Tools and External Services
role: Admin
exl-id: a7d5dc7d-b916-4a09-9068-646f8474bba4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# MDVA-27456: Los usuarios reciben un error al cargar Swagger

El parche MDVA-27456 corrige el problema en el que los usuarios reciben un error al intentar cargar Swagger. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6. El ID del parche es MDVA-27456. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.3.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.5-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios reciben un error al cargar Swagger.

<u>Pasos a seguir</u>:

Ir a `../swagger.`

<u>Resultados esperados</u>:

Swagger se carga sin ningún error.

<u>Resultados reales</u>:

Los usuarios reciben el siguiente error: *No se pudo cargar la definición de la API*. El registro de errores contiene:

*report.CRITICAL: ID del informe: webapi-5ea9c6da19cb1; mensaje: el tipo de parámetro &quot;\DateTime&quot; no es válido. Compruebe el parámetro e inténtelo de nuevo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
