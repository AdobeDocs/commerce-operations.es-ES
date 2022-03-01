---
title: Instale el [!DNL Upgrade Compatibility Tool]
description: Siga estos pasos para instalar el [!DNL Upgrade Compatibility Tool] para su proyecto de Adobe Commerce.
source-git-commit: 317a044e66fe796ff66b9d8cf7b308f741eb82c1
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---


# Instale el [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

La variable [!DNL Upgrade Compatibility Tool] es una herramienta de línea de comandos que comprueba una instancia personalizada de Adobe Commerce en una versión específica analizando todos los módulos instalados en ella. Devuelve una lista de errores y advertencias que deben solucionarse antes de actualizar a la última versión de Adobe Commerce.

## Flujo de trabajo

El diagrama siguiente muestra el flujo de trabajo esperado al ejecutar el [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagrama](../../assets/upgrade-guide/mvp-diagram-v3.png)

## Quién es el [!DNL Upgrade Compatibility Tool] para?

El siguiente caso de uso describe el proceso típico para que un socio de Adobe Commerce actualice una instancia de cliente:

1. Un ingeniero de software de un socio descarga el [!DNL Upgrade Compatibility Tool] desde el [Repositorio de Adobe Commerce](https://repo.magento.com/) y lo ejecuta durante la fase beta de la versión más reciente de Adobe Commerce. Consulte la [Descargue el [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) para obtener más información.
1. El ingeniero de software genera una instancia de vainilla para la versión específica de Adobe Commerce que está instalada actualmente. Consulte la [Guía del colaborador](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) para obtener más información sobre el uso de la variable `instance` para generar una instalación de vainilla.
1. El ingeniero de software ve que hay varias áreas personalizadas rotas en los módulos de inventario y catálogo y que también obtienen una puntuación de complejidad de X. Consulte la [Desarrollador](../upgrade-compatibility-tool/developer.md) para obtener más información sobre la puntuación de complejidad.
1. Con esta información, el ingeniero de software es capaz de comprender la complejidad de la actualización y puede retransmitir esta información al administrador de cuentas del socio.
1. El administrador de cuentas crea una cronología y un coste para la actualización de Adobe Commerce, que les permite obtener la aprobación de su administrador.
1. Con la aprobación de su administrador, el ingeniero de software trabaja en las modificaciones de código necesarias para corregir los módulos rotos.
1. El ingeniero de software ejecuta el [!DNL Upgrade Compatibility Tool] una vez más con una versión preliminar de Adobe Commerce para garantizar que no haya problemas nuevos y que los cambios de código solucionen los problemas encontrados durante la fase beta.
1. Todo se cierra la compra y el ingeniero de software inserta el código en un entorno de ensayo, donde las pruebas de regresión confirman que todas las pruebas son verdes, lo que les permite publicar la última versión de Adobe Commerce en producción el mismo día en que se lanza el lanzamiento previo a la versión de Adobe Commerce.

   ![[!DNL Upgrade Compatibility Tool] audiencia](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>Una instancia de vainilla es una instalación limpia de una rama o etiqueta de versión especificada para una versión específica.

## Requisitos previos

Consulte [requisitos previos](../upgrade-compatibility-tool/prerequisites.md) para obtener más información.

>[!NOTE]
>
>Puede ejecutar el [!DNL Upgrade Compatibility Tool] en cualquier sistema operativo. No es necesario ejecutar el [!DNL Upgrade Compatibility Tool] donde se encuentra la instancia de Adobe Commerce. Es necesario para el [!DNL Upgrade Compatibility Tool] para tener acceso al código fuente de la instancia de Adobe Commerce. Por ejemplo, puede instalar la herramienta en un servidor y apuntarla a la instalación de Adobe Commerce en otro servidor.

Si está ejecutando el [!DNL Upgrade Compatibility Tool] en una instancia de Adobe Commerce con módulos y archivos grandes, la herramienta puede requerir una gran cantidad de RAM, al menos 2 GB de RAM.

### Acciones recomendadas

Las prácticas recomendadas de Adobe Commerce recomiendan evitar tener dos módulos con el mismo nombre. Si esto sucede, la variable [!DNL Upgrade Compatibility Tool] muestra un error de segmentación.

Para evitar este error, se recomienda ejecutar el `bin` con la opción añadida `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>La variable `<dir>` es el directorio donde se encuentra la instancia de Adobe Commerce.

La variable `-m` permite que el [!DNL Upgrade Compatibility Tool] para analizar cada módulo específico de forma independiente a fin de evitar encontrar dos módulos con el mismo nombre en la instancia de Adobe Commerce.

Esta opción de comando también permite [!DNL Upgrade Compatibility Tool] para analizar una carpeta que contiene varios módulos:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Esta recomendación también ayuda con los problemas de memoria que pueden producirse al ejecutar el [!DNL Upgrade Compatibility Tool].

## Descargue el [!DNL Upgrade Compatibility Tool]

Para descargar el [!DNL Upgrade Compatibility Tool], ejecute el siguiente comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Instalar

Para instalar el [!DNL Upgrade Compatibility Tool], debe instalar los requisitos previos necesarios:

* Claves de acceso de Adobe Commerce
* Compositor
* Node.js

### Claves de acceso de Adobe Commerce

Debe tener [Claves de acceso de Adobe Commerce](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) para descargar y usar el [!DNL Upgrade Compatibility Tool]. Añada sus claves de acceso de Adobe Commerce a su `auth.json` que se encuentra en `~/.composer` de forma predeterminada.

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

Clonar el [!DNL Upgrade Compatibility Tool] repositorio y ejecutar `composer install` en su terminal para instalar dependencias.

>[!WARNING]
>
>Si la variable **Claves de acceso de Adobe Commerce** no están correctamente configurados, la variable [!DNL Upgrade Compatibility Tool] no se instalará y obtendrá errores al ejecutar el `composer install` comando.

### Node.js

Para instalar Node.js, consulte Node.js [documentación](https://nodejs.dev/learn/how-to-install-nodejs).

## Extensiones de terceros

Adobe recomienda ponerse en contacto con el proveedor de extensiones para determinar si la extensión es totalmente compatible con Adobe Commerce 2.4.x.

Consulte [Ejecutar la herramienta](../upgrade-compatibility-tool/run.md) para obtener información sobre cómo ejecutar el [!DNL Upgrade Compatibility Tool].
