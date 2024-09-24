---
title: "ACSD-46815: la implementación de contenido estático falla al utilizar una estrategia compacta"
description: Aplique el parche ACSD-46815 para solucionar el problema de Adobe Commerce en el que la implementación de contenido estático falla al utilizar una estrategia compacta.
feature: Deploy, Page Content, SCD
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# ACSD-46815: la implementación de contenido estático falla al utilizar una estrategia compacta

El parche ACSD-46815 corrige el problema en el que la implementación de contenido estático falla cuando se utiliza la estrategia compacta. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20. El ID del parche es ACSD-46815. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La implementación de contenido estático falla al implementar con una estrategia compacta.

<u>Pasos a seguir</u>:

1. Implemente el contenido estático con una estrategia compacta ejecutando el siguiente comando:

```bash
bin/magento setup:static-content:deploy -f -s compact
```

<u>Resultados esperados</u>:

La implementación de contenido estático se completa sin ningún error.

<u>Resultados reales</u>:

La implementación de contenido estático falla con una estrategia compacta. El siguiente error se produce durante el proceso de implementación: *El contenido de /app/pub/static/adminhtml/Magento/base/default/.El archivo /node_modules/@spectrum-css/vars/dist/spectrum-global.css no se puede leer.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura en la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
