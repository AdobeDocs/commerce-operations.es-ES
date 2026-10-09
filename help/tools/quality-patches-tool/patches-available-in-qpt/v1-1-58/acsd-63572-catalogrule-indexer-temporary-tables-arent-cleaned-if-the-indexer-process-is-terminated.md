---
title: 'ACSD-63572: las tablas temporales del indexador "catalogGroup" no se limpian si se termina el proceso del indexador'
description: Aplique el parche ACSD-63572 para corregir el problema de Adobe Commerce en el que las tablas del indizador no se limpian cuando el proceso finalizó debido a una actualización del sistema o se detuvo en [!UICONTROL CLI].
feature: System
Role: Admin, Developers
exl-id: 1cab7058-ca20-4d43-bfca-9b0e3ad35f42
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%
---
# ACSD-63572: las tablas temporales del indizador `catalogrule` no se limpian si finaliza el proceso del indizador

La revisión ACSD-63572 corrige el problema en el que las tablas temporales del indizador no se limpian cuando el proceso finalizó debido a un sistema o actualización o se detuvo en [!UICONTROL CLI]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. El ID del parche es ACSD-63572. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las tablas temporales del indizador no se limpian cuando el proceso finalizó debido a una actualización del sistema o se detuvo en [!UICONTROL CLI].

<u>Pasos a seguir</u>:

1. Abra [!UICONTROL CLI].
1. Ejecutar comando: `bin/magento indexer:reindex catalogrule_rule`.
1. Cancele el proceso antes de que finalice el uso de: `^C`.
1. Restablecer indizadores mediante: `bin/magento indexer:reset catalogrule_rule catalogrule_product`.
1. Repita los pasos anteriores varias veces.
1. Compruebe si se han creado las siguientes tablas temporales en la base de datos:

   ```text
   catalogrule_product__temp*
   catalogrule_product_price__temp*
   ```

<u>Resultados esperados</u>:

Las tablas temporales antiguas se eliminan cuando no son necesarias.

<u>Resultados reales</u>:

Las tablas temporales antiguas no se eliminan.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
