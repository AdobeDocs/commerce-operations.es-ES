---
title: 'ACSD-64532: la variable ENV establecida en *false* se trata como una cadena *false* en lugar de como un BOOLEAN *FALSE*'
description: Aplique el parche ACSD-64532 para solucionar el problema de Adobe Commerce donde una variable "ENV" configurada como *false* se trata como una cadena *false* en lugar de como un valor BOOLEANO *FALSE*.
feature: Variables
role: Admin, Developer
exl-id: 7940df1f-d527-4b57-bde7-7a0216b12436
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8d0b446f-5b16-5a10-b272-01143504a11c
    internal-label: System
subfeature_v2:
  - id: 2191e157-828a-5358-ad69-ebcaa8402915
    internal-label: Variables
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
source-wordcount: '353'
ht-degree: 0%
---
# ACSD-64532: La variable ENV establecida en &quot;false&quot; se trata como una cadena &quot;false&quot; en lugar de como un BOOLEAN FALSE

El parche ACSD-64532 corrige el problema en el que la variable `ENV` establecida en *false* se trata como una cadena *false* en lugar de `BOOLEAN` *FALSE*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62. El ID del parche es ACSD-64532. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
Adobe Commerce (todos los métodos de implementación) 2.4.6-p8

**Compatible con versiones de Adobe Commerce:**
Adobe Commerce (todos los métodos de implementación) 2.4.6-p2 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La variable `ENV` establecida en *false* se trata como una cadena *false* en lugar de `BOOLEAN` *FALSE*.

<u>Pasos a seguir</u>:
1. Agregue `env:MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK` con el valor *false* a las variables de entorno en Adobe Commerce en la infraestructura de la nube.
1. Espere a que se vuelva a implementar.
1. Ejecute la secuencia de comandos comprobando el valor:

   ```php
   <?php
   require '../app/bootstrap.php';
   $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
   $objectManager = $bootstrap->getObjectManager();
   $deploymentConfig = $objectManager->get('Magento\Framework\App\DeploymentConfig');
   $useAppLock = $deploymentConfig->get('indexer/use_application_lock');
   
   var_dump($useAppLock);
   
   $configParsedValue = $deploymentConfig->get('indexer/use_application_lock') ?: false;
   
   var_dump($configParsedValue); 
   ```

<u>Resultados esperados</u>:
`$configParsedValue`, que es el resultado del método `isUseApplicationLock()`, debe devolver un valor negativo para que se pueda interpretar correctamente dentro del método `\Magento\Indexer\Model\Mview\View\State::getStatus()`.

<u>Resultados reales</u>:
`$configParsedValue` tiene un valor de *`string(5) false`*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:
* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
