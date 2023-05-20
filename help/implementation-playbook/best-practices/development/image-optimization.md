---
title: Optimización de imágenes para un sitio más interactivo
description: Conozca los pasos para optimizar las imágenes y utilice la Optimización rápida de imágenes para optimizar el tiempo de respuesta en sus sitios de Adobe Commerce.
role: Developer, Admin
feature: Best Practices
feature-set: Commerce
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Optimización de imágenes para un sitio más interactivo

Para Adobe Commerce en implementaciones de infraestructura en la nube, mejore el tiempo de respuesta del sitio optimizando las imágenes antes de cargarlas. A continuación, utilice la Optimización rápida de imágenes para acelerar la entrega de imágenes y simplificar el mantenimiento de los conjuntos de fuentes de imágenes.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

Adobe Commerce en la infraestructura en la nube


## Optimización y compresión de imágenes

Antes de cargar imágenes en los sitios de Commerce, optimícelas y comprímalas para equilibrar el rendimiento y la calidad de visualización. Esto ayuda a aumentar el espacio y reducir los tiempos de carga de la página.

- El formato PNG ofrece imágenes de tamaño más pequeño para imágenes con grandes áreas de color sólido.

- El formato JPEG ofrece imágenes de menor tamaño para todos los demás tipos de imagen. Utilice la compresión más alta (sin una degradación apreciable). Esto suele ser del 60 al 80 por ciento.

## Habilitar y configurar la optimización rápida de imágenes

Después de configurar el servicio de Fastly para el proyecto de Adobe Commerce Cloud, consulte [Optimización rápida de imágenes](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) para obtener instrucciones sobre cómo habilitar y configurar la optimización de imágenes.

## Información adicional

- [Configuración rápida](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [Las imágenes mal optimizadas pueden provocar problemas de rendimiento](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
