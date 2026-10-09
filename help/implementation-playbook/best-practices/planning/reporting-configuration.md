---
title: Práctica recomendada para la configuración de informes
description: Optimice el rendimiento del sitio eliminando el módulo de creación de informes si no lo está utilizando.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 1%
---
# Práctica recomendada para la configuración de informes

Si tu empresa no requiere informes o la funcionalidad de segmentos dinámicos del cliente, deshabilita la funcionalidad [Informes](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/reports) para mejorar el rendimiento de la tienda.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Deshabilitar informes

Si no utiliza los informes o los segmentos dinámicos de clientes, deshabilite la funcionalidad Informes.

1. Desde el administrador, vaya a **Tiendas** > **Configuración** > **Configuración** > **General** > **Informes**.
1. En **Opciones generales**, establezca **Habilitar informes** en *No*.
1. Vaciar la caché ejecutando `php bin/magento cache:flush` o en el administrador en **Sistema** > **Herramientas** > **Administración de caché**.

## Más información

- [Generación de informes en Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/reports-menu)
- [Segmentos dinámicos de cliente](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments)
