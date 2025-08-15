---
title: 'ACSD-60788: no se ejecutaron los scripts personalizados para  [!DNL Google Tag Manager] debido a errores de CSP'
description: Aplique el parche ACSD-60788 para corregir el problema de Adobe Commerce en el que los scripts personalizados para [!DNL Google Tag Manager] no se ejecutan debido a errores de Política de seguridad de contenido (CSP).
feature: Security
role: Admin, Developer
exl-id: 3392da76-86cb-4357-8658-c95d914a5829
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-60788: los scripts personalizados para [!DNL Google Tag Manager] no se ejecutan debido a errores de la directiva de seguridad de contenido

El parche ACSD-60788 corrige el problema en el que los scripts personalizados para [!DNL Google Tag Manager] no se ejecutan debido a errores de la directiva de seguridad de contenido. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52. El ID del parche es ACSD-60788. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los scripts personalizados de [!DNL Google Tag Manager] no se ejecutan debido a errores de la Política de seguridad de contenido (CSP).

<u>Pasos a seguir</u>:

1. Configure la variable *[!DNL Google Tag Manager]*.
1. Configure la etiqueta de HTML personalizada *[!DNL Google Tag Manager]*.
1. Inserte el siguiente código JavaScript en la primera etiqueta:

   ```
   <script nonce="{{gtmNonce}}">
   console.log("Nonce from simple JS {{gtmNonce}}");
   </script>
   ```

1. Vaciar las cachés después de configurar *GTM*.
1. Abra la consola de desarrollador en el explorador.
1. Abra la Página principal.

<u>Resultados esperados</u>:

La consola de desarrollo del explorador muestra *Nonce de JS simple (caracteres aleatorios)*.

<u>Resultados reales</u>:

La consola de desarrollo del navegador muestra *Nonce de JS simple sin definir*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
