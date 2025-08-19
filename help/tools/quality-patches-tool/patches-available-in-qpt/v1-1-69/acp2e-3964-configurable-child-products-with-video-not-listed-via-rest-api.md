---
title: 'ACP2E-3964: Productos secundarios configurables con vídeo no enumerados mediante la API de REST'
description: Aplique el parche ACP2E-3964 para corregir el problema de Adobe Commerce en el que los productos secundarios de productos configurables con un vídeo en [!UICONTROL Media Gallery] no aparecen en la lista mediante la API de REST.
feature: Products, Media, REST, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f48ced28035c65db561f4700113652574d302ec9
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# ACP2E-3964: Productos secundarios configurables con vídeo no enumerados mediante la API de REST

El parche ACP2E-3964 corrige el problema en el que los productos secundarios de productos configurables con un vídeo en **[!UICONTROL Media Gallery]** no se enumeran a través de la API de REST. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACP2E-3964. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos secundarios de productos configurables con un vídeo en **[!UICONTROL Media Gallery]** no se pueden enumerar mediante la API de REST, lo que genera una respuesta de error.

<u>Pasos a seguir</u>:

1. Cree un nuevo producto configurable y añada un solo producto secundario.
1. Edite el producto secundario y agregue un vídeo en **[!UICONTROL Images and Videos]** (por ejemplo, [https://vimeo.com/1084537](https://vimeo.com/1084537)).
1. Guarde el producto secundario.
1. Envíe una solicitud GET al extremo de la API REST: `rest/v1/configurable-products/%sku%/children` mediante un token de portador de administrador.

<u>Resultados esperados</u>:

La API de REST debe devolver los datos del producto secundario sin errores, incluida la información de vídeo en **[!UICONTROL Media Gallery]**.

<u>Resultados reales</u>:

La API de REST devuelve un error:

```
Error: Call to a member function getVideoProvider() on null in vendor/magento/module-product-video/Model/Product/Attribute/Media/ExternalVideoEntryConverter.php:87
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
