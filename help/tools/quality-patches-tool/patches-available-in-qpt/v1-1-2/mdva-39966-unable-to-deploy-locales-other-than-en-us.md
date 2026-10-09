---
title: 'MDVA-39966: No se pueden implementar configuraciones regionales que no sean en_US'
description: El parche de MDVA-39966 resuelve el problema en el que el usuario no puede implementar configuraciones regionales que no sean en_US. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. El ID del parche es MDVA-39966. Tenga en cuenta que el problema se corrigió en la versión 2.4.1 de Adobe Commerce.
feature: Deploy
role: Admin
exl-id: 03bb0002-9742-4f26-bb41-1b46f0a3573c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bcd8874c-7b93-5596-bdaa-22660e84df14
    internal-label: Deploy
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%
---
# MDVA-39966: No se pueden implementar configuraciones regionales que no sean en_US

El parche de MDVA-39966 resuelve el problema en el que el usuario no puede implementar configuraciones regionales que no sean en_US. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-39966. Tenga en cuenta que el problema se corrigió en la versión 2.4.1 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.3.5-p2, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se pueden implementar configuraciones regionales que no sean en_US.

<u>Pasos a seguir</u>:

1. Configure dos vistas de tienda con configuraciones regionales diferentes, por ejemplo: en_US y de_DE.
1. Intente implementar contenido estático para estas configuraciones regionales ejecutando el siguiente comando:

```shell
bin/magento setup:static-content:deploy --language=en_US
bin/magento setup:static-content:deploy --language=de_DE
```

<u>Resultados esperados</u>:

Se ha implementado la configuración regional de de_DE.

```shell
bin/magento setup:static-content:deploy --language=de_DE

Deploy using quick strategy
adminhtml/Magento/backend/de_DE         2416/2416           ============================ 100%   9 secs
frontend/Magento/blank/de_DE            2486/2486           ============================ 100%   7 secs
frontend/Magento/luma/de_DE             2504/2504           ============================ 100%   8 secs

Execution time: 27.062166929245
```

<u>Resultados reales</u>:

Se implementó la configuración regional en_US en lugar de de de_DE:

```shell
bin/magento setup:static-content:deploy --language=de_DE

Deploy using quick strategy
adminhtml/Magento/backend/en_US         2416/2416           ============================ 100%   2 secs
frontend/Magento/blank/en_US            2486/2486           ============================ 100%   1 sec
frontend/Magento/luma/en_US             2504/2504           ============================ 100%   2 secs
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
