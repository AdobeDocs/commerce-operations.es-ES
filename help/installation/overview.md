---
title: Información general sobre la instalación local
description: Obtenga información sobre el proceso de instalación para implementaciones locales de Adobe Commerce y Magento Open Source.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 7%

---

# Información general sobre la instalación local

>[!NOTE]
>
>El diagrama siguiente proporciona información general de alto nivel sobre _&#x200B;**instalaciones locales**&#x200B;_ de Adobe Commerce:

![Funcionamiento de la instalación](../assets/installation/install-diagram-24.svg)

El flujo de instalación general es el siguiente:

1. Configure el entorno del servidor.

   Instale el software necesario, incluidos PHP, Apache, MySQL y el motor de búsqueda. Consulte los [requisitos del sistema](system-requirements.md) para obtener más información.

1. Obtenga [claves de autenticación](prerequisites/authentication-keys.md) en el repositorio del Compositor de Commerce.

1. Obtenga el software de Adobe Commerce.

   * (Recomendado) Obtenga [Composer metapackage](composer.md) para administrar módulos y sus dependencias.

   * Si desea contribuir al código base del Magento Open Source o personalizar la aplicación, [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) el repositorio de GitHub. Este método requiere estar familiarizado con GitHub y Composer.

1. Instale la aplicación mediante la línea de comandos.

   Si el paso falla porque el software necesario no está configurado correctamente, revise los [requisitos previos](prerequisites/overview.md).

1. [Comprueba](next-steps/verify.md) la instalación consultando tu tienda y el administrador.
