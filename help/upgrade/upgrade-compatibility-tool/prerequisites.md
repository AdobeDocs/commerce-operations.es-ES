---
title: '"[!DNL Upgrade Compatibility Tool] Requisitos previos"'
description: 'Verifique que su sistema cumpla los requisitos necesarios para ejecutar el [!DNL Upgrade Compatibility Tool] para su proyecto de Adobe Commerce. '
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] requisitos previos

{{commerce-only}}

Los requisitos mínimos para ejecutar el [!DNL Upgrade Compatibility Tool] son:

| **Requisitos** | **Restricciones** |
|----------------|-----------------|
| Versión de PHP | >= 7,3 |
| Compositor | ninguno |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`o `>=16.0.0`) |
| Limitaciones de memoria | Al menos 2 GB de RAM |
| Claves de acceso de Adobe Commerce | ninguno |
| Adobe Commerce | ninguno |

Puede ejecutar el [!DNL Upgrade Compatibility Tool] en varios sistemas operativos (Windows no es compatible). No es necesario ejecutar el [!DNL Upgrade Compatibility Tool] donde se encuentra la instancia de Adobe Commerce.

Es necesario para el [!DNL Upgrade Compatibility Tool] para tener acceso al código fuente de la instancia de Adobe Commerce. Por ejemplo, puede instalarlo en un servidor y señalarlo en la instalación de Adobe Commerce en otro servidor. Consulte la [instalar](../upgrade-compatibility-tool/install.md) para obtener más información.

Si está ejecutando el [!DNL Upgrade Compatibility Tool] en una instancia de Adobe Commerce con módulos y archivos grandes, la herramienta podría requerir una gran cantidad de RAM (al menos 2 GB). Puede usar la variable `[=MODULE-PATH]` en el comando para especificar el directorio de rutas del módulo para evitar problemas debido a una limitación de memoria baja:

```bash
bin/uct upgrade:check <dir> -m[=MODULE-PATH]
```

Donde los argumentos son los siguientes:

- `<dir>`: directorio de instalación de Adobe Commerce.
- `[=MODULE-PATH]`: Directorio de rutas del módulo específico.
