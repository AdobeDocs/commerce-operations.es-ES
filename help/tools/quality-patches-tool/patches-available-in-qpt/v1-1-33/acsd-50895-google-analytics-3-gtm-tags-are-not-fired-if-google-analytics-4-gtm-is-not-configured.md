---
title: 'ACSD-50895: [!DNL Google Analytics] 3 etiquetas GTM no se activan si no se ha configurado  [!DNL Google Analytics] 4 GTM'
description: Aplique el parche ACSD-50895 para solucionar el problema de Adobe Commerce donde  [!DNL Google Analytics] 3 etiquetas GTM no se activan si  [!DNL Google Analytics] 4 GTM no está configurada.
role: Admin
exl-id: 871e2ca1-dc10-435c-9325-62f5b9b673ad
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-50895: [!DNL Google Analytics] 3 etiquetas GTM no se activan si [!DNL Google Analytics] 4 GTM no está configurada

El parche ACSD-50895 corrige el problema en el que [!DNL Google Analytics] 3 etiquetas GTM no se activan si [!DNL Google Analytics] 4 GTM no está configurado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33. El ID del parche es ACSD-50895. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!DNL Google Analytics] 3 etiquetas GTM no se activan si [!DNL Google Analytics] 4 GTM no está configurada.

<u>Pasos a seguir</u>:

1. Inicie sesión como usuario administrador.
1. Habilite **[!DNL Google Analytics 3]** y **[!DNL Google Tag Manager]** en **Administración** > **Tienda** > **Configuración** > **Ventas** > **API de Google** > **Google Analytics**.
1. No habilite **[!DNL Google Analytics 4]** ni **[!DNL Google Tag Manager]**.
1. Abra la página del producto en la Tienda.

<u>Resultados esperados</u>:

Las etiquetas GTM se activan cuando solo se activa **[!DNL Google Analytics]** 3 GTM.

<u>Resultados reales</u>:

Las etiquetas GTM no se activan cuando **[!DNL Google Analytics]** 4 GTM está desactivado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
