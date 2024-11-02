---
title: Práctica recomendada para la configuración de informes
description: Optimice el rendimiento del sitio eliminando el módulo de creación de informes si no lo está utilizando.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '121'
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

- [Generar informes en Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/reports-menu)
- [Segmentos dinámicos del cliente](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments)
