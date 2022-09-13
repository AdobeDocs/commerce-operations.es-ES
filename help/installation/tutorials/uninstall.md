---
title: Desinstalación o reinstalación de Adobe Commerce
description: Siga estos pasos para desinstalar y volver a instalar las instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---


# Desinstalación o reinstalación de Adobe Commerce

Antes de utilizar estos comandos, debe [instalar la aplicación](../tutorials/install.md).

## Actualizar la aplicación

Para actualizar la aplicación:

* Si ha instalado el software de un archivo o si ha utilizado &#39;composer-create-project&#39;, consulte la [Guía de actualización](../../upgrade/overview.md).
* Si es un desarrollador colaborador (es decir, ha utilizado `git clone`), consulte [Actualizar la aplicación](../../upgrade/developer/git-installs.md).

## Vuelva a instalar la aplicación

La forma de reinstalar la aplicación desde la línea de comandos depende de su función:

* Si ha instalado el software de un archivo o si ha utilizado &#39;composer-create-project&#39;, consulte [Actualización de dependencias de instalación](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* Si es un desarrollador colaborador (es decir, ha empezado a usar `git clone`), consulte [Actualización de dependencias de instalación](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Desinstalar la aplicación

La desinstalación de la aplicación descarta y restaura la base de datos, elimina la configuración de implementación y borra los directorios de `var`.

Para desinstalar la aplicación, escriba el siguiente comando:

```bash
bin/magento setup:uninstall
```

Se muestra el siguiente mensaje para confirmar que la desinstalación se ha realizado correctamente:

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## Mantener archivos generados de forma opcional

De forma predeterminada, `bin/magento setup:upgrade` borra el código compilado y la caché. Normalmente, se usa `bin/magento setup:upgrade` para actualizar componentes y cada componente puede requerir diferentes clases compiladas.

Sin embargo, en algunas situaciones (especialmente, la implementación en producción), es posible que desee evitar borrar el código compilado, ya que puede tardar algún tiempo. (El [cache](https://glossary.magento.com/cache) sigue borrado). Para actualizar el [esquema de base de datos](https://glossary.magento.com/database-schema) y datos *without* borrando código compilado, escriba:

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>La opción `--keep-generated` debe utilizarla en circunstancias limitadas integradores de sistemas experimentados *only*. Esta opción debería *never* se utilizará en un entorno de desarrollo. El uso incorrecto de este parámetro opcional puede provocar errores durante la ejecución del código.

## Instalación de la aplicación

* [Instalación mediante la línea de comandos](../advanced.md)
