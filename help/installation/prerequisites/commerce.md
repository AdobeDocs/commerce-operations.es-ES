---
title: Obtener el software de Adobe Commerce
description: Aprenda a descargar el software de Adobe Systems Commerce.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Obtenga el software Adobe Systems Commerce

Usted se encuentra entre los 240.000 comerciantes de todo el mundo que confían en nuestro software comercio electrónico. Hemos recopilado información para ayudarle a empezar con su instalación.

## Cómo obtener el software

Compruebe la disponibilidad de nuevas y emocionantes funciones y versiones, y descubra cómo obtenerlas en nuestra [página de disponibilidad del producto](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

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
        <td><ol><li>Crea un proyecto</em> de Composer <em>que contiene los lista de componentes que se van a utilizar.</li>
            <li>Usa el Compositor para actualizar las dependencias del paquete; usa <code>composer create-project</code> para obtener el metapaquete del Compositor.</li>
            <li>Instala la aplicación mediante la <a href="../advanced.md">línea de comandos</a>.</li>
        <li>Actualiza la aplicación y las extensiones mediante la <a href="../../upgrade/implementation/perform-upgrade.md">línea de comandos</a>.</li></ol></td>
        <td><p><a href="../composer.md">Obtenga el metapaquete</a></p></td>
    </tr>
    <tr>
        <td><p>Desarrollador colaborador</p></td>
        <td><p>Contribuye al código base del Magento Open Source, archiva errores y personaliza la aplicación. Muy técnico, tiene su propio servidor de desarrollo, comprende Composer y GitHub.</p>
            <p>Usted <em>no puede</em> usar la aplicación en un entorno de producción.</p>
      <p>Debe actualizar usando <a href="../../upgrade/developer/git-installs.md">comandos Composer y Git</a>.</p></td>
        <td><ol><li>Clona el repositorio de GitHub.</li>
            <li>Utiliza Composer para actualizar las dependencias de los paquetes.</li>
            <li>Instala el aplicación mediante <a href="../advanced.md">la línea de comandos</a>.</li>
            <li>Actualiza la aplicación con <a href="../../upgrade/developer/git-installs.md">comandos Composer y Git</a>.</li>
            <li>Personaliza el código en el directorio <code>app/code</code>.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Clone el repositorio de GitHub</a></p></td>
    </tr>
    </tbody>
</table>

## Información útil

Utilice los vínculos de la parte izquierda de la página para desplazarse por los temas de cada parte de la instalación.

## Permisos de servidor requeridos

Los sistemas UNIX requieren `root` privilegios para instalar y configurar software gustar un servidor web, PHP. Si necesita instalar este software, asegúrese de tener `root` acceso.

No ** instale el aplicación en el servidor web docroot como el `root` usuario porque es posible que el servidor web no pueda interactuar con esos archivos.

Necesita `root` privilegios para crear el sistema de [archivos propietario](file-system/overview.md) y agregar ese propietario al grupo del servidor web. Utilice el sistema de archivos propietario para ejecutar `bin/magento` comandos desde la línea de comandos y para configurar trabajos cron, que programan tareas por usted.
