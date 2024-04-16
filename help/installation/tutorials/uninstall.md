---
title: Desinstalar o volver a instalar Adobe Commerce
description: Siga estos pasos para desinstalar y reinstalar las instalaciones locales de Adobe Commerce.
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Desinstalar o volver a instalar Adobe Commerce

Antes de utilizar estos comandos, debe [instalar la aplicación](../tutorials/install.md).

## Actualizar la aplicación

Para actualizar la aplicación:

* Si ha instalado el software desde un archivo o si ha utilizado &quot;composer-create-project&quot;, consulte la [Guía de actualización](../../upgrade/overview.md).
* Si es un desarrollador colaborador (es decir, ha utilizado `git clone`), consulte [Actualizar la aplicación](../../upgrade/developer/git-installs.md).

## Vuelva a instalar la aplicación

La forma de reinstalar la aplicación desde la línea de comandos depende de la función:

* Si ha instalado el software desde un archivo o si ha utilizado &#39;composer-create-project&#39;, consulte [Actualizar dependencias de instalación](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* Si es un desarrollador colaborador (es decir, ha empezado a utilizar `git clone`), consulte [Actualizar dependencias de instalación](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Desinstalar la aplicación

Al desinstalar la aplicación, se borra y restaura la base de datos, se quita la configuración de implementación y se borran los directorios de `var`.

Para desinstalar la aplicación, introduzca el siguiente comando:

```bash
bin/magento setup:uninstall
```

El siguiente mensaje se muestra para confirmar que la desinstalación se ha realizado correctamente:

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## Mantener opcionalmente archivos generados

De forma predeterminada, `bin/magento setup:upgrade` borra el código compilado y la caché. Normalmente, se utiliza `bin/magento setup:upgrade` para actualizar componentes y cada componente puede requerir clases compiladas diferentes.

Sin embargo, en algunas situaciones (en particular, en la implementación en producción), es posible que desee evitar borrar el código compilado, ya que puede tardar algún tiempo. (La caché sigue borrándose). Para actualizar el esquema y los datos de la base de datos *sin* borrando código compilado, introduzca:

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>El opcional `--keep-generated` La opción debe ser utilizada en circunstancias limitadas por integradores de sistemas experimentados *solamente*. Esta opción debería *nunca* se utilizará en un entorno de desarrollo. El uso incorrecto de este parámetro opcional puede provocar errores durante la ejecución del código.

## Instalación de la aplicación

* [Instale mediante la línea de comandos](../advanced.md)
