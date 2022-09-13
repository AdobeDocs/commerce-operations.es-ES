---
title: Habilitar o deshabilitar módulos
description: Siga estos pasos para administrar los módulos Adobe Commerce o Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---


# Habilitar o deshabilitar módulos

Este comando no tiene requisitos previos.

## Estado del módulo

Utilice el siguiente comando para enumerar los módulos habilitados y deshabilitados:

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

Donde

* `--enabled` enumera todos los módulos habilitados.
* `--disabled` enumera todos los módulos desactivados.
* `<module-list>` es una lista de módulos delimitada por espacios para comprobar el estado. Si [módulo](https://glossary.magento.com/module) nombre contiene caracteres especiales, escriba el nombre entre comillas simples o dobles.

## Módulo habilitar, deshabilitar

Para habilitar o deshabilitar los módulos disponibles, utilice el siguiente comando:

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

Donde

* `<module-list>` es una lista de módulos delimitada por espacios para habilitar o deshabilitar. Si [módulo](https://glossary.magento.com/module) nombre contiene caracteres especiales, escriba el nombre entre comillas simples o dobles.
* `--all` para habilitar o deshabilitar todos los módulos al mismo tiempo.
* `-f` o `--force` para forzar que un módulo se habilite o deshabilite a pesar de las dependencias. Antes de utilizar esta opción, consulte [Acerca de la activación y desactivación de módulos](#about-enabling-and-disabling-modules).
* `-c` o `--clear-static-content` cleans [archivos de vista estáticos generados](../../configuration/cli/static-view-file-deployment.md).

   Si no se borran los archivos de vista estáticos, pueden producirse problemas si hay varios archivos con el mismo nombre y no se borran todos.

   En otras palabras, debido a la [reserva de archivo estático](../../configuration/cli/static-view-file-deployment.md) reglas, si no borra los archivos estáticos y hay más de un archivo llamado `logo.svg` que son diferentes, la alternativa puede provocar que se muestre el archivo incorrecto.

Por ejemplo, para desactivar el `Magento_Weee` , introduzca:

```bash
bin/magento module:disable Magento_Weee
```

Para obtener información importante sobre cómo activar y desactivar módulos, consulte [Acerca de la activación y desactivación de módulos](#about-enabling-and-disabling-modules).

## Actualizar la base de datos

Si ha habilitado uno o más módulos, ejecute el siguiente comando para actualizar la base de datos:

```bash
bin/magento setup:upgrade
```

A continuación, limpie la caché:

```bash
bin/magento cache:clean
```

## Acerca de la activación y desactivación de módulos

Adobe Commerce y Magento Open Source le permiten habilitar o deshabilitar los módulos disponibles actualmente; en otras palabras, cualquier módulo proporcionado por Adobe o cualquier módulo de terceros que esté disponible actualmente.

Algunos módulos dependen de otros módulos, en cuyo caso es posible que no pueda habilitar o deshabilitar un módulo porque tiene dependencias con otros módulos.

Además, podría haber *conflictiva* módulos que no pueden habilitarse al mismo tiempo.

Ejemplos:

* El módulo A depende del módulo B. No puede deshabilitar el módulo B a menos que deshabilite primero el módulo A.

* El módulo A depende del módulo B, ambos desactivados. Debe habilitar el módulo B antes de habilitar el módulo A.

* El módulo A está en conflicto con el módulo B. Puede desactivar el módulo A y el módulo B, o bien puede desactivar cualquiera de los módulos, pero *cannot* habilite el módulo A y el módulo B al mismo tiempo.

* Las dependencias se declaran en la variable `require` en el campo Adobe Commerce y Magento Open Source `composer.json` para cada módulo. Los conflictos se declaran en la `conflict` en módulos&#39; `composer.json` archivos. Utilizamos esa información para crear un gráfico de dependencias: `A->B` significa que el módulo A depende del módulo B.

* A *cadena de dependencia* es la ruta de acceso de un módulo a otro. Por ejemplo, si el módulo A depende del módulo B y el módulo B depende del módulo C, la cadena de dependencias es `A->B->C`.

Si intenta habilitar o deshabilitar un módulo que dependa de otros módulos, el gráfico de dependencias aparece en el mensaje de error.

>[!NOTE]
>
>Es posible que el módulo A `composer.json` declara un conflicto con el módulo B pero no a la inversa.

*Línea de comandos únicamente:* Para forzar que un módulo se habilite o deshabilite independientemente de sus dependencias, use la opción `--force` argumento.

>[!NOTE]
>
>Uso `--force` puede deshabilitar su tienda y causar problemas al acceder al administrador.
