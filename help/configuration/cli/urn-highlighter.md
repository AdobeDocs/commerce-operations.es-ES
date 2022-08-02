---
title: Marcador URN
description: Aprenda a configurar el resaltado de URN en su IDE.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---


# Descripción general del marcador de resaltado URN

{{file-system-owner}}

El código de comercio hace referencia a todos los esquemas XSD como [Nombres de recursos uniformes (URN)](https://www.ietf.org/rfc/rfc2141.txt). Si está desarrollando código y necesita hacer referencia a XSD, este comando configura su entorno de desarrollo integrado (IDE) para reconocer y resaltar las URN. Esto facilita el desarrollo.

De forma predeterminada, un IDE como PhpStorm no está configurado para reconocer direcciones URL y, como resultado, se muestran en rojo como se indica a continuación:

![PhpStorm no está configurado para reconocer URN](../../assets/configuration/urn-before.png)

La variable `bin/magento dev:urn-catalog:generate` habilita su IDE (actualmente, solo PhpStorm y código de Visual Studio) para reconocer y resaltar las URL como las siguientes:

![Habilitar IDE para reconocer URN](../../assets/configuration/urn-after.png)

Específicamente, este comando crea la siguiente configuración de PhpStorm:

![Ejemplo de configuración de PhpStorm](../../assets/configuration/urn-settings.png)

## Configurar el IDE

Actualmente, solo se admiten PhpStorm y el código de Visual Studio.

Sintaxis de comandos:

```bash
bin/magento dev:urn-catalog:generate <path>
```

Donde `<path>` es la ruta a su PhpStorm `misc.xml` , que se encuentra en relación con la raíz del proyecto. Normalmente, `<path>` es `.idea/misc.xml`.

>[!INFO]
>
>Para mantener los &quot;Esquemas y DTD&quot; actualizados, ejecute el `dev:urn-catalog:generate` cada vez que agregue, modifique o elimine módulos Commerce 2 que contengan `*.xsd` archivos.
