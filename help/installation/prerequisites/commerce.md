---
title: Obtenga el software de Adobe Commerce
description: Obtenga información sobre cómo descargar el software de Adobe Commerce y Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---


# Obtenga el software de Adobe Commerce

Usted está entre los 240.000 comerciantes de todo el mundo que depositan su confianza en nuestro software de comercio electrónico. Hemos reunido información para ayudarle a empezar con su instalación.

## Cómo obtener el software

Compruebe la disponibilidad de las nuevas y emocionantes funciones y versiones, y aprenda cómo puede utilizarlas en nuestra [página de disponibilidad del producto](https://devdocs.magento.com/release/availability.html).

Consulte la siguiente tabla para empezar a instalar Adobe Commerce o Magento Open Source.

<table>
    <tbody>
        <tr>
            <th>Necesidades de usuario</th>
            <th>Descripción</th>
            <th>Pasos de instalación y actualización de alto nivel</th>
            <th>Vínculo de introducción</th>
        </tr>
    <tr>
        <td><p>Integrator, empaquetador</p></td>
        <td><p>Quiere tener control total sobre todos los componentes instalados, tiene acceso al servidor de aplicaciones, altamente técnico, puede volver a empaquetar el Magento Open Source con otros componentes.</p>
        </td>
        <td><ol><li>Crea un Compositor <em>proyecto</em> que contiene la lista de componentes que se van a utilizar.</li>
            <li>Utiliza Composer para actualizar las dependencias de los paquetes; uses <code>composer create-project</code> para obtener el metapaquete del Compositor.</li>
            <li>Instala la aplicación utilizando la variable <a href="../advanced.md">línea de comandos</a>.</li>
        <li>Actualiza la aplicación y las extensiones utilizando el  <a href="../../upgrade/implementation/perform-upgrade.md">línea de comandos</a>.</li></ol></td>
        <td><p><a href="../composer.md">Obtener el metapackage</a></p></td>
    </tr>
    <tr>
        <td><p>Desarrollador colaborador</p></td>
        <td><p>Contribuye a la base de código del Magento Open Source, a los errores de archivos y personaliza la aplicación. Muy técnico, tiene su propio servidor de desarrollo, comprende Composer y GitHub.</p>
            <p>You <em>cannot</em> utilice la aplicación en un entorno de producción.</p>
      <p>Debe actualizar con <a href="../../upgrade/developer/git-installs.md">Compositor y comandos Git</a>.</p></td>
        <td><ol><li>Clona el repositorio de GitHub.</li>
            <li>Utiliza el Compositor para actualizar las dependencias del paquete.</li>
            <li>Instala la aplicación utilizando <a href="../advanced.md">línea de comandos</a>.</li>
            <li>Actualiza la aplicación utilizando <a href="../../upgrade/developer/git-installs.md">Compositor y comandos Git</a>.</li>
            <li>Personaliza el código en la variable <code>app/code</code> directorio.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Clonar el repositorio de GitHub</a></p></td>
    </tr>
    </tbody>
</table>

## Información útil

Utilice los vínculos del lado izquierdo de la página para navegar por los temas de cada parte de la instalación.

## Permisos necesarios del servidor

Los sistemas UNIX requieren `root` privilegios para instalar y configurar software como un servidor web, PHP. Si necesita instalar este software, asegúrese de que tiene `root` acceso.

Do *not* instale la aplicación en el servidor web docroot como el `root` porque es posible que el servidor web no pueda interactuar con esos archivos.

Necesita `root` privilegios para crear la variable [propietario del sistema de archivos](file-system/overview.md) y agregue ese propietario al grupo del servidor web. Utilice la variable [propietario del sistema de archivos](https://glossary.magento.com/magento-file-system-owner) para ejecutar `bin/magento` comandos de la línea de comandos y para configurar trabajos cron, que programan tareas para usted.
