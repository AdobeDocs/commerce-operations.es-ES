---
title: Parches disponibles en la descripción general de la herramienta QPT
description: Este artículo proporciona información general sobre [!DNL Quality Patches Tool] (QPT) y vínculos a recursos que explican cómo utilizarlo.
feature: Support, Tools and External Services
role: Admin
exl-id: e67e5823-d878-4efc-90af-c7bb8c59d654
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: a59f76dc-e003-5617-951e-dffa5bd3de81
    internal-label: Support
  - id: 618ab558-d6ad-5352-99d6-d5702c6fdf80
    internal-label: Tools and External Services
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%
---
# Parches disponibles en la descripción general de la herramienta QPT

Este artículo proporciona información general sobre [!DNL Quality Patches Tool] (QPT) y vínculos a recursos que explican cómo utilizarlo.

## Productos y versiones afectados

* Adobe Commerce local, todas [las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce en la infraestructura de la nube, todas [las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## ¿Qué es la herramienta Parches de calidad?

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) (QPT) es una herramienta que le permite aplicar parches de calidad individuales desarrollados por Adobe y la comunidad de Magento Open Source.

Le permite hacer lo siguiente:

* aplicar parches de calidad incluidos en el paquete
* revertir parches aplicados anteriormente
* consulte la información general sobre parches de calidad disponibles para la versión instalada de Adobe Commerce.

Este es un ejemplo de la tabla de estado que puede obtener para ver los parches disponibles:

![Tabla de estado de la herramienta Parches de calidad que muestra los parches disponibles y su estado de instalación](/help/assets/tools/status_table.png)

La herramienta está diseñada para permitirle autoabastecerse con parches para problemas que pueda experimentar con Adobe Commerce o aplicar fácilmente los parches sugeridos por el soporte de Adobe Commerce.

>[!NOTE]
>
>QPT es solo para parches de calidad. Los parches de seguridad están disponibles en [Notas de la versión para Adobe Commerce y Magento Open Source](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/overview.html).

## Parches disponibles en [!DNL Quality Patches Tool]

En esta sección de la Base de conocimiento de soporte de Adobe Commerce, encontrará descripciones detalladas de los problemas, resueltos por parches QPT, agrupados por versión de QPT.
También puede ver una lista de los parches QPT disponibles y filtrar el por componente, utilizando la tabla generada dinámicamente en la página [[!DNL Quality Patches Tool]: Buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) de nuestra base de conocimiento de soporte.

## Cómo instalar y utilizar [!DNL Quality Patches Tool]

Los comandos de instalación y uso son diferentes para Adobe Commerce local y para Adobe Commerce en la infraestructura en la nube, ya que para la nube el paquete QPT se incluye en el paquete ece-tools.

### Cómo instalar y utilizar QPT para Adobe Commerce local

Consulte [Commerce > Herramientas > Uso](../usage.md) en nuestra documentación para desarrolladores para obtener más información sobre cómo instalar y utilizar QPT para aplicar y revertir parches.

### Cómo instalar y utilizar QPT para Adobe Commerce en la infraestructura en la nube

Consulte [Guía de Commerce en la infraestructura de la nube > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores para obtener más información sobre cómo instalar y utilizar QPT para aplicar y revertir parches en Adobe Commerce en la infraestructura de la nube.

## Lectura relacionada

* [[!DNL Quality Patches Tool] notas de la versión](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/release-notes.html) en nuestra documentación para desarrolladores.
