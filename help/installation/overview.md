---
title: Información general sobre la instalación local
description: Obtenga información acerca del proceso de instalación para implementaciones locales de Adobe Commerce.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Información general sobre la instalación local

>[!NOTE]
>
>En el diagrama siguiente se proporciona información general de alto nivel sobre _**local**_ instalaciones de Adobe Commerce:

![Funcionamiento de la instalación](../assets/installation/install-diagram-24.svg)

El flujo de instalación general es el siguiente:

1. Configure el entorno del servidor.

   Instale el software necesario, incluidos PHP, Apache, MySQL y el motor de búsqueda. Consulte la [requisitos del sistema](system-requirements.md) para obtener más información.

1. Obtener [claves de autenticación](prerequisites/authentication-keys.md) al repositorio del Compositor de Commerce.

1. Obtenga el software Adobe Commerce o de Magento Open Source.

   * (Recomendado) Obtenga la [Metapaquete del Compositor](composer.md) para administrar módulos y sus dependencias.

   * Si desea contribuir al código base del Magento Open Source o personalizar la aplicación, [clonar](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) el repositorio de GitHub. Este método requiere estar familiarizado con GitHub y Composer.

1. Instale la aplicación mediante la línea de comandos.

   Si el paso falla porque el software necesario no está configurado correctamente, revise el [requisitos previos](prerequisites/overview.md).

1. [Verificar](next-steps/verify.md) Para la instalación, consulte su tienda y el administrador.
