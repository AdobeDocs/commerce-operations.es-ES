---
title: '"[!DNL Upgrade Compatibility Tool] Requisitos previos"'
description: 'Verifique que su sistema cumpla los requisitos necesarios para ejecutar el [!DNL Upgrade Compatibility Tool] para su proyecto de Adobe Commerce. '
source-git-commit: c4769b555df49ed2f0b2fffbeaf458c5a64816ba
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] requisitos previos

{{commerce-only}}

Ejecución de [!DNL Upgrade Compatibility Tool] ayuda a identificar lo que debe hacer **before** actualizar su versión de Adobe Commerce.

Los requisitos mínimos para ejecutar el [!DNL Upgrade Compatibility Tool] son:

| **Requisitos** | **Restricciones** |
|----------------|-----------------|
| Versión de PHP | >= 7,3 |
| Compositor | ninguno |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`o `>=16.0.0`) |
| Limitaciones de memoria | Al menos 2 GB de RAM |
| Claves de acceso de Adobe Commerce | ninguno |
| Adobe Commerce | ninguno |

Puede ejecutar el [!DNL Upgrade Compatibility Tool] en cualquier sistema operativo. No es necesario ejecutar el [!DNL Upgrade Compatibility Tool] donde se encuentra la instancia de Adobe Commerce.

Es necesario para el [!DNL Upgrade Compatibility Tool] para tener acceso al código fuente de la instancia de Adobe Commerce. Por ejemplo, puede instalarlo en un servidor y señalarlo en la instalación de Adobe Commerce en otro servidor. Consulte la [instalar](../upgrade-compatibility-tool/install.md) para obtener más información.

Si está ejecutando el [!DNL Upgrade Compatibility Tool] en una instancia de Adobe Commerce con módulos y archivos grandes, la herramienta puede requerir una gran cantidad de RAM, al menos 2 GB de RAM.
