---
title: Práctica recomendada para la configuración de informes
description: Optimice el rendimiento del sitio eliminando el módulo de creación de informes si no lo está utilizando.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Práctica recomendada para la configuración de informes

Si su empresa no requiere la funcionalidad de creación de informes o segmentos dinámicos de clientes, deshabilite la [Funcionalidad de informes](https://docs.magento.com/user-guide/configuration/general/reports.html) para mejorar el rendimiento de la tienda.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Deshabilitar informes

Si no utiliza los informes o los segmentos dinámicos de clientes, deshabilite la funcionalidad Informes.

1. Desde Admin, vaya a **Tiendas** > **Configuración** > **Configuración** > **General** > **Informes**.
1. En **Opciones generales**, configurado **Habilitar informes** hasta *No*.
1. Vaciar la caché ejecutando `php bin/magento cache:flush` o en el Administrador de **Sistema** > **Herramientas** > **Administración de caché**.

## Información adicional

- [Generación de informes en Adobe Commerce](https://docs.magento.com/user-guide/reports.html)
- [Segmentos dinámicos de cliente](https://docs.magento.com/user-guide/marketing/customer-segments.html)
