---
title: Instalación de la herramienta de compatibilidad de actualización
description: Siga estos pasos para instalar la herramienta de compatibilidad de actualización para su proyecto de Adobe Commerce.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---


# Instalación de la herramienta de compatibilidad de actualización

La herramienta de compatibilidad de actualización es una herramienta de línea de comandos que comprueba una instancia personalizada de Adobe Commerce en relación con una versión específica analizando todos los módulos instalados en ella. Devuelve una lista de errores y advertencias que deben solucionarse antes de actualizar a la última versión de Adobe Commerce.

## Flujo de trabajo

El diagrama siguiente muestra el flujo de trabajo esperado al ejecutar la herramienta de compatibilidad de actualización:

![Diagrama de la herramienta de compatibilidad de actualización](../../assets/upgrade-guide/mvp-diagram-v3.png)

## ¿Para quién es la herramienta de compatibilidad de actualización?

El siguiente caso de uso describe el proceso típico para que un socio de Adobe Commerce actualice una instancia de cliente:

1. Un ingeniero de software de un socio descarga el paquete de la herramienta de compatibilidad de actualización del [Repositorio de Adobe Commerce](https://repo.magento.com/) y lo ejecuta durante la fase beta de la versión más reciente de Adobe Commerce. Consulte la [Descargar la herramienta de compatibilidad de actualización](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) para obtener más información.
1. El ingeniero de software genera una instancia de vainilla para la versión específica de Adobe Commerce que está instalada actualmente. Consulte la [Guía del colaborador](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) para obtener más información sobre el uso de la variable `instance` para generar una instalación de vainilla.
1. El ingeniero de software ve que hay varias áreas personalizadas rotas en los módulos de inventario y catálogo y que también obtienen una puntuación de complejidad de X. Consulte la [Desarrollador](../upgrade-compatibility-tool/developer.md) para obtener más información sobre la puntuación de complejidad.
1. Con esta información, el ingeniero de software es capaz de comprender la complejidad de la actualización y puede retransmitir esta información al administrador de cuentas del socio.
1. El administrador de cuentas crea una cronología y un coste para la actualización de Adobe Commerce, que les permite obtener la aprobación de su administrador.
1. Con la aprobación de su administrador, el ingeniero de software trabaja en las modificaciones de código necesarias para corregir los módulos rotos.
1. El ingeniero de software ejecuta la herramienta de compatibilidad de actualización una vez más con una versión preliminar de Adobe Commerce para garantizar que no haya problemas nuevos y que los cambios de código solucionen los problemas encontrados durante la fase beta.
1. Todo se cierra la compra y el ingeniero de software inserta el código en un entorno de ensayo, donde las pruebas de regresión confirman que todas las pruebas son verdes, lo que les permite publicar la última versión de Adobe Commerce en producción el mismo día en que se lanza el lanzamiento previo a la versión de Adobe Commerce.

   ![Audiencia de la herramienta de compatibilidad de actualización](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>Una instancia de vainilla es una instalación limpia de una rama o etiqueta de versión especificada para una versión específica.

## Requisitos previos

Consulte [requisitos previos](../upgrade-compatibility-tool/prerequisites.md) para obtener más información.

>[!NOTE]
>
>Puede ejecutar la herramienta de compatibilidad de actualización en cualquier sistema operativo. No es necesario ejecutar la herramienta de compatibilidad de actualización en la que se encuentra su instancia de Adobe Commerce. Es necesario que la herramienta de compatibilidad de actualización tenga acceso al código fuente de la instancia de Adobe Commerce. Por ejemplo, puede instalar la herramienta en un servidor y apuntarla a la instalación de Adobe Commerce en otro servidor.

Si está ejecutando la herramienta de compatibilidad de actualización en una instancia de Adobe Commerce con módulos y archivos grandes, la herramienta puede requerir una gran cantidad de RAM, al menos 2 GB de RAM.

### Acciones recomendadas

Las prácticas recomendadas de Adobe Commerce recomiendan evitar tener dos módulos con el mismo nombre. Si esto sucede, la herramienta de compatibilidad de actualización muestra un error de segmentación.

Para evitar este error, se recomienda ejecutar el `bin` con la opción añadida `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>La variable `<dir>` es el directorio donde se encuentra la instancia de Adobe Commerce.

La variable `-m` permite que la herramienta de compatibilidad de actualización analice cada módulo específico de forma independiente para evitar encontrar dos módulos con el mismo nombre en la instancia de Adobe Commerce.

Esta opción de comando también permite a la herramienta de compatibilidad de actualización analizar una carpeta que contiene varios módulos:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Esta recomendación también ayuda con los problemas de memoria que pueden producirse al ejecutar la herramienta de compatibilidad de actualización.

## Descargar la herramienta de compatibilidad de actualización

Para descargar la herramienta de compatibilidad de actualización, ejecute el siguiente comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Instalar

Para instalar la herramienta de compatibilidad de actualización, debe instalar los requisitos previos necesarios:

* Claves de acceso de Adobe Commerce
* Compositor
* Node.js

### Claves de acceso de Adobe Commerce

Debe tener [Claves de acceso de Adobe Commerce](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) para descargar y utilizar la herramienta de compatibilidad de actualización. Añada sus claves de acceso de Adobe Commerce a su `auth.json` que se encuentra en `~/.composer` de forma predeterminada.

>[!WARNING]
>
>Compruebe su **COMPOSER_HOME** variable de entorno para ver dónde está la variable `auth.json` se encuentra.

La variable **clave pública** corresponde a la variable _username_ que **clave privada** es la variable _password_:

### Ejemplo de claves de acceso de Adobe Commerce

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

### Compositor

Clona el repositorio de la herramienta de compatibilidad de actualización y ejecuta `composer install` en su terminal para instalar dependencias.

>[!WARNING]
>
>Si la variable **Claves de acceso de Adobe Commerce** no están correctamente configurados, la herramienta de compatibilidad de actualización no se instalará y obtendrá errores al ejecutar la `composer install` comando.

### Node.js

Para instalar Node.js, consulte Node.js [documentación](https://nodejs.dev/learn/how-to-install-nodejs).

## Extensiones de terceros

Adobe recomienda ponerse en contacto con el proveedor de extensiones para determinar si la extensión es totalmente compatible con Adobe Commerce 2.4.x.

Consulte [Ejecutar la herramienta](../upgrade-compatibility-tool/run.md) para obtener información sobre la ejecución de la herramienta de compatibilidad de actualización.
