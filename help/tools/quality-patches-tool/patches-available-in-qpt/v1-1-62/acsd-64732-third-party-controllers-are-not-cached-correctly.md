---
title: 'ACSD-64732: Los controladores de terceros no se almacenan correctamente en caché con los segmentos de los clientes'
description: Aplique el parche ACSD-64732 para solucionar el problema de Adobe Commerce en el que los controladores de terceros no se almacenan correctamente en la caché con segmentos de clientes.
feature: Cache
role: Admin, Developer
exl-id: 378e5a96-06dd-4796-9e45-a67cf539fcce
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '315'
ht-degree: 0%
---
# ACSD-64732: Los controladores de terceros no se almacenan correctamente en caché con los segmentos de los clientes

El parche ACSD-64732 corrige el problema en el que los controladores de terceros no se almacenan correctamente en caché con segmentos de clientes. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62. El ID del parche es ACSD-64732. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los controladores de terceros no se almacenan correctamente en caché con los segmentos del cliente.

<u>Pasos a seguir</u>:

1. Vaya al controlador personalizado (/catalog/category/vary).
1. Vaya a la ficha **[!UICONTROL Network]** y compruebe el valor de **[!DNL X-Magento-Vary]**.

<u>Resultados esperados</u>:

El valor **[!UICONTROL X-Magento-Vary]** debe ser el mismo en el controlador personalizado.

<u>Resultados reales</u>:

El valor de **[!UICONTROL X-Magento-Vary]** es diferente, lo que causa errores de caché. Esto significa que la caché generada anteriormente no se puede utilizar al visitar el controlador personalizado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura en la nube: Actualizaciones y parches > Aplicar parches en la guía de Commerce en la infraestructura en la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
