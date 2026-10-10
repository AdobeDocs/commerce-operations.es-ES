---
title: Comprobar parche para el problema de Adobe Commerce con la herramienta Parches de calidad
description: Este artículo proporciona información general sobre la herramienta Parches de calidad (QPT) y vínculos a recursos que explican cómo utilizarla.
feature: Tools and External Services
role: Admin
exl-id: 4d651c3c-95ad-4b53-bf77-92758acb795d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
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
source-wordcount: '443'
ht-degree: 0%
---
# Comprobar parche para el problema de Adobe Commerce con la herramienta Parches de calidad

Este artículo proporciona información general sobre la herramienta Parches de calidad (QPT) y vínculos a recursos que explican cómo utilizarla.

## Productos y versiones afectados

* Adobe Commerce local, todas [las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)
* Adobe Commerce en la infraestructura de la nube, todas [las versiones compatibles](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf)

## Qué es la herramienta Parches de calidad

La [Herramienta de Parches de Calidad](https://github.com/magento/quality-patches) (QPT) son parches individuales desarrollados por Adobe y la comunidad de Magento Open Source.

Le permite hacer lo siguiente:

* aplicar parches de calidad incluidos en el paquete
* revertir parches aplicados anteriormente
* consulte la información general sobre parches de calidad disponibles para la versión instalada de Adobe Commerce.

Este es un ejemplo de la tabla de estado que puede obtener para ver los parches disponibles:

![Tabla de estado de la herramienta Parches de calidad que muestra los parches disponibles y su estado de instalación](/help/assets/tools/status_table.png)

La herramienta está diseñada para permitirle autoabastecerse con parches para problemas que pueda experimentar con Adobe Commerce o aplicar fácilmente los parches sugeridos por el soporte de Adobe Commerce.

>[!NOTE]
>
>QPT es solo para parches de calidad. Los parches de seguridad están disponibles en [Magento Security Center](/help/release/release-notes/overview.md).

## Parches disponibles en la herramienta Parches de calidad

Consulte [Herramienta de parches de calidad](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en nuestra documentación para desarrolladores para ver la lista de parches disponibles.

## Cómo instalar y utilizar la herramienta Parches de calidad

Los comandos de instalación y uso son diferentes para Adobe Commerce local y para Adobe Commerce en la infraestructura en la nube, ya que para la nube el paquete QPT se incluye en el paquete ece-tools.

### Cómo instalar y utilizar QPT para Adobe Commerce local

Consulte [Guía de actualización de software > Parches](/help/tools/quality-patches-tool/usage.md) en nuestra documentación para desarrolladores para obtener más información sobre cómo instalar y utilizar QPT para aplicar y revertir parches.

### Cómo instalar y utilizar QPT para Adobe Commerce en la infraestructura en la nube

Consulte [Cloud for Adobe Commerce > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en nuestra documentación para desarrolladores para obtener más información sobre cómo instalar y utilizar QPT para aplicar y revertir parches en Adobe Commerce en la infraestructura en la nube.

## Lectura relacionada

* [Notas de la versión de la herramienta Parches de calidad](/help/tools/quality-patches-tool/release-notes.md) en nuestra documentación para desarrolladores.
* [Cómo aplicar parches de compositor proporcionados por Adobe](https://experienceleague.adobe.com/es/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) en la base de conocimiento de soporte.
