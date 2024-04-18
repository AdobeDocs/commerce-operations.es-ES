---
title: Obtener el software de Adobe Commerce
description: Obtenga información sobre cómo descargar el software de Adobe Commerce.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Obtener el software de Adobe Commerce

Usted está entre los 240.000 comerciantes de todo el mundo que confían en nuestro software de comercio electrónico. Hemos recopilado información para ayudarle a empezar con su instalación.

## Cómo obtener el software

Compruebe la disponibilidad de nuevas e interesantes funciones y versiones, y descubra cómo puede aprovecharlas en nuestra [página de disponibilidad del producto](https://devdocs.magento.com/release/availability.html).

Consulte la siguiente tabla para empezar a instalar Adobe Commerce.

<table>
    <tbody>
        <tr>
            <th>Necesidades del usuario</th>
            <th>Descripción</th>
            <th>Pasos de instalación y actualización de alto nivel</th>
            <th>Vínculo de introducción</th>
        </tr>
    <tr>
        <td><p>Integrador, empaquetador</p></td>
        <td><p>Quiere un control total de todos los componentes instalados, tiene acceso al servidor de aplicaciones, es muy técnico y puede volver a empaquetar el Magento Open Source con otros componentes.</p>
        </td>
        <td><ol><li>Crea un compositor <em>proyecto</em> que contiene la lista de componentes que se van a utilizar.</li>
            <li>Utiliza el Compositor para actualizar las dependencias del paquete; utiliza el <code>composer create-project</code> para obtener el metapaquete Composer.</li>
            <li>Instala la aplicación utilizando <a href="../advanced.md">línea de comandos</a>.</li>
        <li>Actualiza la aplicación y las extensiones utilizando  <a href="../../upgrade/implementation/perform-upgrade.md">línea de comandos</a>.</li></ol></td>
        <td><p><a href="../composer.md">Obtenga el metapaquete</a></p></td>
    </tr>
    <tr>
        <td><p>Desarrollador colaborador</p></td>
        <td><p>Contribuye al código base del Magento Open Source, archiva errores y personaliza la aplicación. Muy técnico, tiene su propio servidor de desarrollo, comprende Composer y GitHub.</p>
            <p>Usted <em>no puede</em> utilice la aplicación en un entorno de producción.</p>
      <p>Debe actualizar mediante <a href="../../upgrade/developer/git-installs.md">Comandos Composer y Git</a>.</p></td>
        <td><ol><li>Clona el repositorio de GitHub.</li>
            <li>Utiliza el Compositor para actualizar las dependencias del paquete.</li>
            <li>Instala la aplicación mediante <a href="../advanced.md">línea de comandos</a>.</li>
            <li>Actualiza la aplicación mediante <a href="../../upgrade/developer/git-installs.md">Comandos Composer y Git</a>.</li>
            <li>Personaliza el código en <code>app/code</code> directorio.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Clone el repositorio de GitHub</a></p></td>
    </tr>
    </tbody>
</table>

## Información útil

Utilice los vínculos de la parte izquierda de la página para desplazarse por los temas de cada parte de la instalación.

## Permisos de servidor requeridos

Los sistemas UNIX requieren `root` privilegios para instalar y configurar software como un servidor web, PHP. Si necesita instalar este software, asegúrese de que tiene `root` acceso.

Hacer *no* instale la aplicación en el servidor web docroot como `root` porque el servidor web podría no poder interactuar con esos archivos.

Usted necesita `root` privilegios para crear el [propietario del sistema de archivos](file-system/overview.md) y agregue ese propietario al grupo del servidor web. Utilice el propietario del sistema de archivos para ejecutar `bin/magento` comandos desde la línea de comandos y para configurar trabajos cron, que programan tareas automáticamente.
