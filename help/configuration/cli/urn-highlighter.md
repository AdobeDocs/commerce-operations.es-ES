---
title: Marcador URN
description: Aprenda a configurar el resaltado de URN en el IDE.
exl-id: 6389ab58-af70-4b33-800e-be3191c5a4cc
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Descripción general del resaltador URN

{{file-system-owner}}

El código de Commerce hace referencia a todos los esquemas XSD como [Nombres uniformes de recursos (URN)](https://www.ietf.org/rfc/rfc2141.txt). Si está desarrollando código y necesita hacer referencia a XSD, este comando configura el entorno de desarrollo integrado (IDE) para reconocer y resaltar URN. Esto facilita el desarrollo.

De forma predeterminada, un IDE como PhpStorm no está configurado para reconocer URN y, como resultado, se muestran en texto rojo de la siguiente manera:

![PhpStorm no está configurado para reconocer URN](../../assets/configuration/urn-before.png)

El `bin/magento dev:urn-catalog:generate` Este comando permite al IDE (actualmente, sólo PhpStorm y código de Visual Studio) reconocer y resaltar URN como los siguientes:

![Habilitar IDE para reconocer URN](../../assets/configuration/urn-after.png)

Específicamente, este comando crea la siguiente configuración de PhpStorm:

![Ejemplo de configuración de PhpStorm](../../assets/configuration/urn-settings.png)

## Configurar el IDE

Actualmente, solo se admiten PhpStorm y código de Visual Studio.

Sintaxis del comando:

```bash
bin/magento dev:urn-catalog:generate <path>
```

Donde `<path>` es la ruta a su PhpStorm `misc.xml` , que se encuentra en relación con la raíz del proyecto. Normalmente, `<path>` es `.idea/misc.xml`.

>[!INFO]
>
>Para mantener actualizados los esquemas y DTD, ejecute el `dev:urn-catalog:generate` cada vez que añada, modifique o elimine módulos de Commerce 2 que contengan `*.xsd` archivos.
