---
title: 'MDVA-39605: El TTL de caché de Redis (fecha de caducidad) tiene un valor incorrecto'
description: El parche MDVA-39605 resuelve el problema en el que el TTL de la caché de Redis (fecha de caducidad) tiene un valor incorrecto. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. El ID del parche es MDVA-39605. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Cache, Console, Services
role: Admin
exl-id: 65f5d50a-e49e-4155-9d1a-3758f0c723a8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# MDVA-39605: El TTL de caché de Redis (fecha de caducidad) tiene un valor incorrecto

El parche MDVA-39605 resuelve el problema en el que el TTL de la caché de Redis (fecha de caducidad) tiene un valor incorrecto. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. El ID del parche es MDVA-39605. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El TTL de la caché de Redis (fecha de caducidad) tiene un valor incorrecto.

<u>Pasos a seguir</u>:

Para probar la corrección, vacíe la caché y abra un producto configurable en la tienda. A continuación, abra un terminal (consola) y siga los pasos a continuación:

1. Ejecute el comando: `redis-cli`.
1. Ejecutar `KEYS "*PRICE"` (sólo debe haber una clave en el resultado, por ejemplo, `zc:ti:e54_PRICE`). Copie la clave.
1. Ejecute `SMEMBERS` seguido de la clave del paso anterior (por ejemplo, `SMEMBERS zc:ti:e54_PRICE`). Copie cualquier clave del resultado (por ejemplo, e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. Ejecute `KEYS "*<key>"` con el nombre de clave del paso anterior para obtener el nombre de clave completo (por ejemplo, `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`). Solo debe haber una clave en el resultado (por ejemplo, `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`). Como puede observar, el nombre de clave completo es simplemente el nombre de clave con el prefijo &quot;`zc:k:`&quot;. Ahora copie el nombre de clave completo.
1. Ejecute `HGETALL` seguido del nombre de clave completo del paso 4 para comprobar el valor. El valor debe contener datos serializados de productos asociados de un producto configurable relacionado.
1. Ejecute `TTL` seguido del nombre de clave completo del paso 4 para comprobar si la clave tiene caducidad. El resultado debe ser diferente de **-1** y **-2** y debe ser aproximadamente 2592000 (30 días). Aunque la caducidad establecida en el código es de un año, la biblioteca Redis utilizada en Adobe Commerce tiene un límite máximo estricto de 2592000.

<u>Resultados esperados</u>:

El límite de caducidad es de 2592000 s

<u>Resultados reales</u>:

El límite de caducidad se ha establecido en **-1** o **-2**.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
