---
title: Optimización de imágenes para un sitio más interactivo
description: Conozca los pasos para optimizar las imágenes y utilice la Optimización rápida de imágenes para optimizar el tiempo de respuesta en sus sitios de Adobe Commerce.
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%
---
# Optimización de imágenes para un sitio más interactivo

Para Adobe Commerce en implementaciones de infraestructura en la nube, mejore el tiempo de respuesta del sitio optimizando las imágenes antes de cargarlas. A continuación, utilice la Optimización rápida de imágenes para acelerar la entrega de imágenes y simplificar el mantenimiento de los conjuntos de fuentes de imágenes.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

Adobe Commerce en la infraestructura en la nube


## Optimización y compresión de imágenes

Antes de cargar imágenes en los sitios de Commerce, optimícelas y comprímelas para equilibrar el rendimiento con la calidad de visualización. Esto ayuda a aumentar el espacio y reducir los tiempos de carga de la página.

- El formato PNG ofrece imágenes de tamaño más pequeño para imágenes con grandes áreas de color sólido.

- El formato JPEG ofrece imágenes de menor tamaño para todos los demás tipos de imagen. Utilice la compresión más alta (sin una degradación apreciable). Esto suele ser del 60 al 80 por ciento.

## Habilitar y configurar la optimización rápida de imágenes

Después de configurar el servicio de Fastly para su proyecto de Adobe Commerce Cloud, consulte [Optimización de imagen de Fastly](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/cdn/fastly-image-optimization) para obtener instrucciones para habilitar y configurar la optimización de imágenes.

## Más información

- [Configuración rápida](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)
- [Las imágenes mal optimizadas pueden provocar problemas de rendimiento](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow)
