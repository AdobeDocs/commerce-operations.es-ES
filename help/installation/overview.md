---
title: Información general sobre la instalación local
description: Obtenga información sobre el proceso de instalación para implementaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---


# Información general sobre la instalación local

>[!NOTE]
>
>El diagrama siguiente proporciona información general de alto nivel sobre _**local**_ instalaciones de Adobe Commerce y Magento Open Source:

![Funcionamiento de la instalación](../assets/installation/install-diagram-24.svg)

El flujo general de instalación es el siguiente:

1. Configure el entorno del servidor.

   Instale el software de requisitos previos, incluyendo PHP, Apache, MySQL y el motor de búsqueda. Consulte la [requisitos del sistema](system-requirements.md) para obtener más información.

1. Get [claves de autenticación](prerequisites/authentication-keys.md) al repositorio de Commerce Composer.

1. Obtenga el software de Adobe Commerce o Magento Open Source.

   * (Recomendado) Obtenga la variable [Paquete de metapástasis del Compositor](composer.md) para administrar módulos y sus dependencias.

   * Si desea contribuir al código de base del Magento Open Source o personalizar la aplicación, [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) el repositorio de GitHub. Este método requiere estar familiarizado con GitHub y con Composer.

1. Instale la aplicación utilizando la línea de comandos.

   Si el paso falla porque el software de requisitos previos no está configurado correctamente, revise la [requisitos previos](prerequisites/overview.md).

1. [Verificar](next-steps/verify.md) la instalación consultando su tienda y el administrador.

