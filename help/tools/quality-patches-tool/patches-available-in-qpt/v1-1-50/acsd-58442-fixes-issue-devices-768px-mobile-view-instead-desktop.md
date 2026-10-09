---
title: 'ACSD-58442: corrige el problema en el que los dispositivos con una anchura de 768 píxeles se tratan como móviles, lo que provoca que el menú y el encabezado se carguen en la vista móvil, no en el escritorio'
description: Aplique el parche ACSD-58442 para corregir el problema de Adobe Commerce en el que los dispositivos con una anchura de 768 píxeles se tratan como móviles, lo que provoca que el menú y el encabezado se carguen en una vista móvil en lugar de en el escritorio.
feature: Storefront
role: Admin, Developer
exl-id: 86ea64aa-10fc-4fa3-9902-918fb8983ca0
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
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
source-wordcount: '448'
ht-degree: 0%
---
# ACSD-58442: corrige el problema en el que los dispositivos con una anchura de 768 píxeles se tratan como móviles, lo que provoca que el menú y el encabezado se carguen en la vista móvil, no en el escritorio

El parche ACSD-58442 corrige el problema de Adobe Commerce en el que los dispositivos con una anchura de 768 píxeles se tratan como móviles, lo que provoca que el menú y el encabezado se carguen en una vista móvil en lugar de en un escritorio. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50. El ID del parche es ACSD-58442. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El sistema ahora trata los dispositivos con una anchura de 768 píxeles como escritorio, lo que garantiza que el menú y el encabezado se carguen correctamente. Anteriormente, los dispositivos con una anchura de 768 píxeles se trataban como móviles, lo que provocaba que el menú y el encabezado se cargaran en una vista móvil.

<u>Pasos a seguir</u>:

1. Cargue la página principal en un iPad Mini o use la herramienta de inspección de un explorador para cambiar el tamaño del explorador a una anchura de *768px*.
1. Abra el menú principal.

<u>Resultados esperados</u>:

El menú y el encabezado se cargan como una vista de escritorio.

<u>Resultados reales</u>:

El menú y el encabezado se cargan como una vista móvil.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
