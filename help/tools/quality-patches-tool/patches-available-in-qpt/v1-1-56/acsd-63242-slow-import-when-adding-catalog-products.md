---
title: 'ACSD-63242: importación lenta al añadir más de 10 000 productos de catálogo'
description: Aplique el parche ACSD-63242 para corregir el problema de Adobe Commerce de las importaciones lentas cuando se añaden productos de catálogo con más de 10 000 entradas.
feature: Data Import/Export
role: Admin, Developer
exl-id: 2d9114c8-72e4-4a11-89e7-b1a41c1fe14f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# ACSD-63242: importación lenta al añadir más de 10 000 productos de catálogo

El parche ACSD-63242 corrige el problema de las importaciones lentas cuando se añaden productos de catálogo con más de 10 000 entradas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. El ID del parche es ACSD-63242. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6-p8

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p8 y 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La importación de productos es lenta cuando se añaden productos del catálogo con más de 10 000 entradas.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Import]** > **[!UICONTROL Products]** > **[!UICONTROL Add/Update]**.
1. Importe un archivo con más de 10 000 entradas.

<u>Resultados esperados</u>:

La importación de productos del catálogo se ejecuta en el tiempo esperado.

<u>Resultados reales</u>:

La importación de productos es lenta. El `var/log/exception.log` contiene:

```PHP
Exception: Warning: DOMXPath::query(): Recursion limit exceeded in /var/www/html/lib/internal/Magento/Framework/Validator/HTML/ConfigurableWYSIWYGValidator.php on line 114 in /var/www/html/lib/internal/Magento/Framework/App/ErrorHandler.php:62
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
