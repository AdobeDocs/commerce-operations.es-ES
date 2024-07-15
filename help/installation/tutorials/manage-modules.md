---
title: Habilitar o deshabilitar módulos
description: Siga estos pasos para administrar los módulos de Adobe Commerce.
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 0%

---

# Habilitar o deshabilitar módulos

Este comando no tiene requisitos previos.

## Estado del módulo

Utilice el siguiente comando para ver una lista de los módulos activados y desactivados:

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

Donde

* `--enabled` enumera todos los módulos habilitados.
* `--disabled` enumera todos los módulos deshabilitados.
* `<module-list>` es una lista de módulos delimitados por espacios para comprobar el estado. Si algún nombre de módulo contiene caracteres especiales, escríbalo entre comillas simples o dobles.

>[!NOTE]
>
>No puede habilitar ni deshabilitar módulos directamente en proyectos en la nube. Debe ejecutar estos comandos localmente y, a continuación, insertar los cambios en el archivo `app/etc/config.php` para un entorno. Vea [Flujo de trabajo de proyecto profesional: flujo de trabajo de implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html#deployment-workflow).

## Módulo habilitado, deshabilitar

Para activar o desactivar los módulos disponibles, utilice el siguiente comando:

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

Donde

* `<module-list>` es una lista de módulos delimitados por espacios que se deben habilitar o deshabilitar. Si algún nombre de módulo contiene caracteres especiales, escríbalo entre comillas simples o dobles.
* `--all` para habilitar o deshabilitar todos los módulos al mismo tiempo.
* `-f` o `--force` para forzar que un módulo se habilite o deshabilite a pesar de las dependencias. Antes de usar esta opción, consulte [Acerca de la activación y desactivación de módulos](#about-enabling-and-disabling-modules).
* `-c` o `--clear-static-content` limpia [archivos de vista estática generados](../../configuration/cli/static-view-file-deployment.md).

  Si no se borran los archivos de vista estática, podrían producirse problemas si hay varios archivos con el mismo nombre y no se borran todos.

  En otras palabras, debido a las reglas [static file fallback](../../configuration/cli/static-view-file-deployment.md), si no borra los archivos estáticos y hay más de un archivo de nombre `logo.svg` que son diferentes, la reserva podría hacer que se muestre un archivo incorrecto.

Por ejemplo, para deshabilitar el módulo `Magento_Weee`, escriba:

```bash
bin/magento module:disable Magento_Weee
```

Para obtener información importante acerca de cómo habilitar y deshabilitar módulos, vea [Acerca de la habilitación y deshabilitación de módulos](#about-enabling-and-disabling-modules).

## Actualizar la base de datos

Si ha activado uno o más módulos, ejecute el siguiente comando para actualizar la base de datos:

```bash
bin/magento setup:upgrade
```

A continuación, limpie la caché:

```bash
bin/magento cache:clean
```

## Acerca de la activación y desactivación de módulos

Adobe Commerce le permite habilitar o deshabilitar los módulos disponibles actualmente; es decir, cualquier módulo proporcionado por el Adobe o cualquier módulo de terceros disponible actualmente.

Algunos módulos dependen de otros módulos, en cuyo caso es posible que no pueda habilitar o deshabilitar un módulo porque depende de otros módulos.

Además, podría haber *módulos en conflicto* que no se pueden habilitar a la vez.

Ejemplos:

* El módulo A depende del módulo B. No puede deshabilitar el Módulo B a menos que deshabilite primero el Módulo A.

* El módulo A depende del módulo B, y ambos están desactivados. Debe habilitar el módulo B para poder habilitar el módulo A.

* El módulo A entra en conflicto con el módulo B. Puede deshabilitar el Módulo A y el Módulo B, o bien puede deshabilitar cualquiera de los módulos, pero *no puede* habilitar el Módulo A y el Módulo B al mismo tiempo.

* Las dependencias se declaran en el campo `require` del archivo de Adobe Commerce `composer.json` para cada módulo. Se declaran conflictos en el campo `conflict` de los archivos `composer.json` de los módulos. Utilizamos esa información para generar un gráfico de dependencias: `A->B` significa que el módulo A depende del módulo B.

* Una *cadena de dependencias* es la ruta de acceso de un módulo a otro. Por ejemplo, si el módulo A depende del módulo B y el módulo B depende del módulo C, la cadena de dependencias es `A->B->C`.

Si intenta habilitar o deshabilitar un módulo que depende de otros módulos, el gráfico de dependencias se muestra en el mensaje de error.

>[!NOTE]
>
>Es posible que el módulo A `composer.json` declare un conflicto con el módulo B, pero no a la inversa.

*Solo línea de comandos:* Para forzar que un módulo se habilite o deshabilite independientemente de sus dependencias, use el argumento `--force` opcional.

>[!NOTE]
>
>Usar `--force` puede deshabilitar su tienda y causar problemas al acceder al administrador.
