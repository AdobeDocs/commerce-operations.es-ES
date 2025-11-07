---
title: Obtener el software de Adobe Commerce
description: Obtenga información sobre cómo descargar el software de Adobe Commerce.
exl-id: 7a769d5b-5397-4572-8db5-7602068e6aad
source-git-commit: 0659c19e24e90ca4e3a7ac1c04914bda82b766dd
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Obtener el software de Adobe Commerce

Usted está entre los 240.000 comerciantes de todo el mundo que confían en nuestro software de comercio electrónico. Hemos recopilado información para ayudarle a empezar con su instalación.

## Cómo obtener el software

Compruebe la disponibilidad y compatibilidad de las extensiones creadas por Adobe y los servicios de Commerce para Adobe Commerce y Magento Open Source en nuestra [página de disponibilidad del producto](https://experienceleague.adobe.com/es/docs/commerce-operations/release/product-availability).

>[!NOTE]
>
>Los códigos base de Adobe Commerce ahora se distribuyen exclusivamente a través de Composer debido a cambios en las políticas. Use Composer para descargar cualquiera de las versiones de Adobe Commerce enumeradas, ya que el código base ya no está disponible en la sección Descargas.
>
>Para obtener más información, consulte [No se puede acceder al extracto de facturación y descargar el código de base en Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/es/docs/experience-cloud-kcs/kbarticles/ka-26611)

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
        <td><p>Quiere tener control total sobre todos los componentes instalados, tiene acceso al servidor de aplicaciones y es muy técnico, por lo que podría volver a empaquetar Magento Open Source con otros componentes.</p>
        </td>
        <td><ol><li>Crea un Compositor <em>proyecto</em> que contiene la lista de componentes que se van a utilizar.</li>
            <li>Usa el Compositor para actualizar las dependencias del paquete; usa <code>composer create-project</code> para obtener el metapaquete del Compositor.</li>
            <li>Instala la aplicación mediante la <a href="../advanced.md">línea de comandos</a>.</li>
        <li>Actualiza la aplicación y las extensiones mediante la <a href="../../upgrade/implementation/perform-upgrade.md">línea de comandos</a>.</li></ol></td>
        <td><p><a href="../composer.md">Obtenga el metapaquete</a></p></td>
    </tr>
    <tr>
        <td><p>Desarrollador colaborador</p></td>
        <td><p>Contribuye a la base de código de Magento Open Source, archiva errores y personaliza la aplicación. Muy técnico, tiene su propio servidor de desarrollo, comprende Composer y GitHub.</p>
            <p>Usted <em>no puede</em> usar la aplicación en un entorno de producción.</p>
      <p>Debe actualizar usando <a href="../../upgrade/developer/git-installs.md">comandos Composer y Git</a>.</p></td>
        <td><ol><li>Clona el repositorio de GitHub.</li>
            <li>Utiliza el Compositor para actualizar las dependencias del paquete.</li>
            <li>Instala la aplicación mediante <a href="../advanced.md">línea de comandos</a>.</li>
            <li>Actualiza la aplicación con <a href="../../upgrade/developer/git-installs.md">comandos Composer y Git</a>.</li>
            <li>Personaliza el código en el directorio <code>app/code</code>.</li></ol></td>
        <td><p><a href="https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/">Clone el repositorio de GitHub</a></p></td>
    </tr>
    </tbody>
</table>

## Información útil

Utilice los vínculos de la parte izquierda de la página para desplazarse por los temas de cada parte de la instalación.

## Permisos de servidor requeridos

Los sistemas UNIX requieren privilegios de `root` para instalar y configurar software como un servidor web o PHP. Si necesita instalar este software, asegúrese de que tiene acceso de `root`.

No instale *not* la aplicación en el servidor web docroot como usuario de `root`, ya que es posible que el servidor web no pueda interactuar con esos archivos.

Necesita privilegios de `root` para crear el [propietario del sistema de archivos](file-system/overview.md) y agregar ese propietario al grupo del servidor web. El propietario del sistema de archivos se usa para ejecutar comandos de `bin/magento` desde la línea de comandos y para configurar trabajos cron, que programan tareas automáticamente.
