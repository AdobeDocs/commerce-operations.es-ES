---
title: Requisitos previos de la herramienta de compatibilidad de actualización
description: 'Compruebe que su sistema cumple los requisitos necesarios para ejecutar la herramienta de compatibilidad de actualización para su proyecto de Adobe Commerce. '
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Requisitos previos de la herramienta de compatibilidad de actualización

La ejecución de la herramienta de compatibilidad de actualización le ayuda a identificar lo que debe hacer **before** actualizar su versión de Adobe Commerce.

Los requisitos mínimos para ejecutar la herramienta de compatibilidad de actualización son:

| **Requisitos** | **Restricciones** |
|----------------|-----------------|
| Versión de PHP | >= 7,3 |
| Compositor | ninguno |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`o `>=16.0.0`) |
| Limitaciones de memoria | Al menos 2 GB de RAM |
| Claves de acceso de Adobe Commerce | ninguno |
| Adobe Commerce (código abierto o empresa) | ninguno |

Puede ejecutar la herramienta de compatibilidad de actualización en cualquier sistema operativo. No es necesario ejecutar la herramienta de compatibilidad de actualización en la que se encuentra su instancia de Adobe Commerce.

Es necesario que la herramienta de compatibilidad de actualización tenga acceso al código fuente de la instancia de Adobe Commerce. Por ejemplo, puede instalarlo en un servidor y señalarlo en la instalación de Adobe Commerce en otro servidor. Consulte la [instalar](../upgrade-compatibility-tool/install.md) para obtener más información.
