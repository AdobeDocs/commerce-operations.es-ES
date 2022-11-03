---
title: Optimizar imágenes para un sitio más interactivo
description: Conozca los pasos para optimizar las imágenes y utilizar la optimización de imágenes Fough para optimizar el tiempo de respuesta en sus sitios de Adobe Commerce.
role: Developer, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---


# Optimizar imágenes para un sitio más interactivo

Para Adobe Commerce en implementaciones de infraestructura en la nube, mejore el tiempo de respuesta del sitio optimizando las imágenes antes de cargarlas. A continuación, utilice la optimización de imágenes Fapiente para acelerar la entrega de imágenes y simplificar el mantenimiento de los conjuntos de fuentes de imágenes.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

Adobe Commerce en infraestructura en la nube


## Optimizar y comprimir imágenes

Antes de cargar imágenes a sus sitios de comercio, optimice y comprima las imágenes para equilibrar el rendimiento con la calidad de visualización. Esto ayuda a aumentar el espacio y a reducir los tiempos de carga de las páginas.

- El formato PNG proporciona imágenes de menor tamaño para imágenes con grandes áreas de color sólido.

- El formato JPEG ofrece imágenes de menor tamaño para todos los demás tipos de imágenes. Utilice la compresión más alta (sin degradación visible). Esto es generalmente del 60% al 80%.

## Habilitar y configurar la optimización de imagen Fough

Después de configurar el servicio Finfinito para el proyecto de Adobe Commerce Cloud, consulte [Optimización de imágenes más rápidas](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) para obtener instrucciones sobre cómo habilitar y configurar la optimización de imágenes.

## Información adicional

- [Configuración rápida](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [Las imágenes mal optimizadas pueden provocar problemas de rendimiento](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
