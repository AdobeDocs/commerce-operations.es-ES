---
title: 'ACSD-58790: corrige la funcionalidad de pellizco a zoom en las imágenes de la página de detalles del producto en la vista móvil en  [!DNL Chrome]'
description: ACSD-58790 corrige el problema de Adobe Commerce donde la imagen en la vista móvil de  [!DNL Chrome] no hizo zoom en la imagen como se esperaba.
feature: Storefront
role: Admin, Developer
exl-id: 46b324bf-c2a0-4086-87ee-96e8c4883494
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-58790: corrige la funcionalidad de pellizco a zoom en las imágenes de la página de detalles del producto en la vista móvil de [!DNL Chrome]

El parche ACSD-58790 corrige el problema de Adobe Commerce en el que la imagen de la vista móvil de [!DNL Chrome] no aumentaba la imagen como se esperaba. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50. El ID del parche es ACSD-58790. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Corrige la funcionalidad de pellizco para zoom en las imágenes de la página de detalles del producto en la vista móvil de [!DNL Chrome].

<u>Pasos a seguir</u>:

1. Cree un producto con una imagen.
1. Abra el producto desde un explorador [!DNL Chrome].
1. Haga clic en la imagen y compruebe que la imagen amplía al hacer doble clic.
1. Cambie a la vista móvil con las herramientas para desarrolladores de [!DNL Chrome].
1. Haga clic en la imagen.
1. Pulse dos veces.

<u>Resultados esperados</u>:

La imagen se amplía al hacer doble clic.

<u>Resultados reales</u>:

La imagen no aumenta cuando se hace doble clic. Este problema es específico de [!DNL Chrome] en la vista móvil, ya que la funcionalidad de zoom funciona según lo esperado en [!DNL Firefox].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
