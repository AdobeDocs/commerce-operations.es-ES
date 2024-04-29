---
title: Sugerencias y trucos del compositor
description: Obtenga información acerca de las tareas comunes de desarrollo del Compositor y sugerencias para resolver problemas rápidamente.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 5ead5fb1-3bb3-4e77-a4f1-8e10c4f91efb
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# Sugerencias y trucos del compositor

Puede encontrar problemas al desarrollar módulos Adobe Commerce con Composer. Estas prácticas recomendadas describen algunas tareas comunes para facilitar el desarrollo y ayudarle a resolver problemas rápidamente.

>[!NOTE]
>
>Estas directrices se aplican principalmente a [arquitectura de referencia global (GRA)](../overview.md) proyectos.

## Acelere el uso de Composer

Instalar [https://github.com/hirak/prestissimo](https://github.com/hirak/prestissimo) para acelerar las descargas de paquetes asincrónicos de Composer.

```bash
composer global require hirak/prestissimo
```

Si tiene problemas, desinstale `prestissimo`:

```bash
composer global remove hirak/prestissimo
```

## Resolver problemas de versiones imprecisos

Composer a veces se bloquea con las versiones de paquetes. Puede ver mensajes sobre versiones que son incompatibles, aunque no lo sean. Antes de depurar los problemas de compatibilidad, intente restablecer el Compositor:

1. Borre la memoria caché del Compositor.

   ```bash
   composer clearcache
   ```

1. Retire el `composer.lock` para todos los paquetes.

   ```bash
   rm -rf vendor/* composer.lock
   ```

1. Vuelva a instalar los paquetes de Composer.

   ```bash
   composer install
   ```

>[!TIP]
>
>Estos pasos actualizan todos los paquetes a la última versión disponible. Revertir el `composer.lock` de Git para deshacer estas actualizaciones.

## Buscar posibles actualizaciones en los paquetes de cliente

1. Averigüe qué paquetes pueden estar obsoletos.

   ```bash
   composer outdated
   ```

1. Filtre usando caracteres comodín o el `--minor-only` para omitir actualizaciones incompatibles con versiones anteriores:

   ```bash
   composer outdated 'magento/*'
   composer outdated --minor-only 'magento/*'
   ```

## Averiguar si hay un módulo instalado

Ver detalles acerca de todos los paquetes instalados en una rama Git.

```bash
composer info
```

Ejecutar `composer install` después de cambiar las ramas de Git y antes de ejecutar `composer info`. De lo contrario, Composer muestra los detalles de la rama anterior que se ha extraído.

>[!TIP]
>
>Para filtrar o buscar, utilice uno de los siguientes comandos.
>
>```bash
>composer info '*magento*'
>composer info | grep magento
>```

## Descubra por qué está instalado un paquete (versión específica de a)

A veces, Composer instala la última versión disponible de un paquete debido a una dependencia estricta en otro paquete.

Averigüe si hay una dependencia estricta en otro paquete.

```bash
composer why client/module-example
```

Si los resultados muestran una lista de metapaquetes u otro paquete que no sea explícitamente necesario, ejecute el comando en ese paquete:

```bash
composer why example/metapackage
```

## Averiguar por qué no se instala un paquete

A veces, Composer no instala un paquete porque entra en conflicto con otro paquete, otro paquete lo reemplaza o no lo ha definido como una dependencia.

Averigüe por qué no está instalado un paquete.

```bash
composer why-not client/module-example
```

## Aloje un repositorio privado de Composer.

Si necesita un repositorio privado de Composer, utilice [Empaquetador privado](https://packagist.com/) o [JFrog Artifactory](https://jfrog.com/integration/php-composer-repository/). No use [Satis](https://github.com/composer/satis).

- **Empaquetador privado** es seguro, cuesta alrededor de $ 600 USD por año con tres usuarios administradores y está alojado.

- **JFrog Artifactory** comienza en $1,176 USD por año. No se usa tan comúnmente como Packagist, pero soporta más lenguajes que PHP.

- **Satis** no tiene seguridad integrada ni automatización y requiere alojamiento adicional. Solo es gratis si tu tiempo también es gratis.

## Versiones de paquetes

Uso [Versiones semánticas 2.0.0](https://semver.org/spec/v2.0.0.html) como se describe en Adobe Commerce [esquema de versiones](https://developer.adobe.com/commerce/php/development/versioning/). No reinvente la rueda.

Para las dependencias del módulo Adobe Commerce, siga las [dependencias de versión del módulo](https://developer.adobe.com/commerce/php/development/versioning/dependencies/) documentación.

No utilice la definición de versión dentro de `composer.json` archivo. En su lugar, utilice etiquetas Git para las versiones. Consulte [Versiones del compositor y restricciones](https://getcomposer.org/doc/articles/versions.md#versions-and-constraints).

## Dónde colocar los módulos que se incluyen en un archivo y no a través de Composer

Cree un repositorio Git para los módulos de un archivo y alojarlos. Cada módulo de Adobe Commerce tiene un `composer.json` archivo. Después de alojarlo en Git y sincronizarlo con Private Packagist, puede instalarlo con Composer.

Cuando reciba una nueva versión del paquete, cargue el código en Git, etiquete e instale la nueva versión con Composer.
