---
title: Resumen de datos de muestra
description: Obtenga información sobre el uso de datos de ejemplo para proyectos de Adobe Commerce y Magento Open Source.
exl-id: 828b009d-a6ff-4db2-aa1a-838f6f55a194
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---

# Resumen de datos de muestra

Los datos de muestra proporcionan una tienda basada en el tema de Luma equipado con productos, categorías, registro de clientes, etc. Funciona igual que una tienda de comercio y puede manipular los precios, el inventario y las reglas de precios promocionales usando el administrador.

Puede instalar datos de ejemplo antes o después de instalar el software Commerce. Cuando haya terminado con los datos de ejemplo, puede eliminarlos o instalarlos de nuevo, tal como se describe en [Quitar módulos de datos de ejemplo o actualizar datos de ejemplo](remove-or-update.md).

>[!WARNING]
>
>No puede desinstalar datos de ejemplo. Le recomendamos que utilice datos de ejemplo solo para obtener información sobre cómo funcionan Adobe Commerce y Magento Open Source. Evite realizar cualquier desarrollo en un sistema en el que haya instalado datos de ejemplo.

Puede instalar datos de ejemplo opcionales de cualquiera de las siguientes maneras:

| Método de instalación | Descripción | Nivel de habilidad requerido |
|--- |--- |--- |
| Uso del compositor | [Ejecutar `magento sampledata:deploy` para modificar la raíz de la aplicación `composer.json`](composer-packages.md) para habilitar los módulos de datos de ejemplo. | Requiere conocimientos de Compositor y acceso al sistema de archivos de Commerce. |
| Clonación de repositorios | [Clone el repositorio de GitHub](git-repositories.md) y el repositorio de datos de ejemplo y, a continuación, vincúlelos. | Solo para desarrolladores colaboradores. Todos los demás deben utilizar uno de los métodos anteriores. |
