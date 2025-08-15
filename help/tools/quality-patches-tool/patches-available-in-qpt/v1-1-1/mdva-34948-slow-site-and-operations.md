---
title: 'MDVA-34948: Ralentización del sitio web'
description: El parche de MDVA-34948 Adobe Commerce soluciona el problema de la ralentización del sitio web. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1. El ID del parche es MDVA-34948. Tenga en cuenta que el problema se corrigió en la versión 2.4.1 de Adobe Commerce.
feature: Observability, Configuration
role: Admin
exl-id: 3c2a2d44-7d60-42da-a0a3-785fb61d571e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# MDVA-34948: Ralentización del sitio web


## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce en nuestra infraestructura en la nube 2.4.0-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce local y Adobe Commerce en nuestra infraestructura de nube 2.3.6-2.3.6-p1, 2.4.0-2.4.0-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El sitio web se vuelve lento, lo que dificulta las operaciones.

<u>Pasos a seguir</u>:

1. Ejecute `show processlist` en MySQL.
1. Compruebe si hay varias consultas como:

```sql
   SELECT GET_LOCK(SYSTEM_CONFIG', '10');
```

<u>Resultados esperados</u>:

`GET_LOCK` debe ejecutarse de inmediato.

<u>Resultados reales</u>:

Varias consultas `GET_LOCK` se quedan atascadas durante un máximo de 10 segundos cada una.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
