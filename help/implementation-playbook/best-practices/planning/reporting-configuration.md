---
title: Práctica recomendada para la configuración de informes
description: Optimizar el rendimiento del sitio eliminando el módulo de informes si no lo utiliza.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Práctica recomendada para la configuración de informes

Si su empresa no requiere informes o la funcionalidad de segmentos de clientes dinámicos, deshabilite la variable [Funcionalidad de los informes](https://docs.magento.com/user-guide/configuration/general/reports.html) para mejorar el rendimiento del almacén.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en infraestructura en la nube
- Adobe Commerce local

## Deshabilitar informes

Si no utiliza los segmentos Informes o de clientes dinámicos, deshabilite la funcionalidad Informes .

1. Desde el administrador, vaya a **Almacenes** > **Configuración** > **Configuración** > **General** > **Informes**.
1. En **Opciones generales**, conjunto **Habilitar informes** a *No*.
1. Vaciar caché ejecutando `php bin/magento cache:flush` o en el Administrador de **Sistema** > **Herramientas** > **Administración de caché**.

## Información adicional

- [Generar informes en Adobe Commerce](https://docs.magento.com/user-guide/reports.html)
- [Segmentos dinámicos del cliente](https://docs.magento.com/user-guide/marketing/customer-segments.html)
