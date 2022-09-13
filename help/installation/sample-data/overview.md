---
title: Información general de datos de ejemplo
description: Obtenga información sobre el uso de datos de ejemplo para proyectos de Adobe Commerce y Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# Información general de datos de ejemplo

Los datos de muestra proporcionan una tienda basada en el tema de Luma, equipado con productos, categorías, registro de clientes, etc. Funciona igual que una tienda de comercio y puede manipular las reglas de precios, inventario y precios promocionales mediante el Administrador.

Puede instalar datos de ejemplo antes o después de instalar el software Commerce. Cuando haya terminado con los datos de ejemplo, puede eliminarlos o instalarlos de nuevo, tal como se describe en [Eliminar módulos de datos de ejemplo o actualizar datos de ejemplo](remove-or-update.md).

>[!WARNING]
>
>No puede desinstalar datos de ejemplo. Solo se recomienda utilizar datos de ejemplo para obtener información sobre cómo funcionan Adobe Commerce y Magento Open Source. Evite realizar cualquier desarrollo en un sistema en el que haya instalado datos de ejemplo.

Puede instalar datos de ejemplo opcionales de cualquiera de estas formas:

| Método de instalación | Descripción | Nivel de aptitud requerido |
|--- |--- |--- |
| Uso del compositor | [Ejecutar `magento sampledata:deploy` para modificar la raíz de la aplicación `composer.json`](composer-packages.md) para habilitar módulos de datos de ejemplo. | Requiere conocimientos del Compositor y acceso al sistema de archivos de Comercio. |
| Clonación de repositorios | [Clonar el repositorio de GitHub](git-repositories.md) y el repositorio de datos de ejemplo, y luego vincúlelos juntos. | Solo para desarrolladores colaboradores. Todos los demás deben utilizar uno de los métodos anteriores. |
