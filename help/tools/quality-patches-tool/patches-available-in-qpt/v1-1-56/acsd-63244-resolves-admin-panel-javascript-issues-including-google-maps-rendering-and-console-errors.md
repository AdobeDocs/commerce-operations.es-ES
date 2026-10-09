---
title: 'ACSD-63244: resolver los problemas de JavaScript del panel de administración, incluidos los errores de procesamiento y consola de [!DNL Google Maps]'
description: El parche ACSD-63244 corrige varios problemas de JavaScript en el panel de administración, incluidos problemas con el procesamiento de [!DNL Google Maps] y errores recurrentes de tipo no capturado this._each no es una función en la consola del explorador.
feature: Admin Workspace
role: Admin, Developer
exl-id: 1985c845-219e-4af4-8f70-62dd57722494
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '341'
ht-degree: 0%
---
# ACSD-63244: resolver los problemas de JavaScript del panel de administración, incluidos los errores de procesamiento y consola de [!DNL Google Maps]

La revisión ACSD-63244 corrige varios problemas de JavaScript en el panel de administración, incluidos problemas con el procesamiento de [!DNL Google Maps] y errores recurrentes de `Uncaught TypeError: this._each is not a function` en la consola del explorador. Este parche está disponible con [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. El ID del parche es ACSD-63244. Tenga en cuenta que el problema estaba programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4, 2.4.4-p9, 2.4.6-p7, 2.4.7

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

* El error `Uncaught TypeError: this._each is not a function` aparece en la consola del explorador, lo que interrumpe la funcionalidad de la IU de administración.
* El error de JavaScript impide que [!DNL Google Maps] se represente correctamente.

<u>Pasos a seguir</u>:

1. Cargue la IU de administración de Adobe Commerce.
1. Abra la consola del explorador y ejecute el siguiente script:

   ```text
   Object.values([] || {}).forEach((function(e) {  
   e("dd")  
   }));  
   ```

<u>Resultados esperados</u>:

Las funciones de JavaScript disponibles en la biblioteca JS predeterminada se ejecutan correctamente sin errores.

<u>Resultados reales</u>:

Los errores de JavaScript aparecen en la consola del explorador:

```text
Uncaught TypeError: this._each is not a function
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
