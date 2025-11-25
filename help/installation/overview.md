---
title: Información general sobre la instalación local
description: Obtenga información acerca del proceso de instalación local de Adobe Commerce. Descubra los requisitos del servidor, los pasos de configuración y las prácticas recomendadas de implementación.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---


# Información general sobre la instalación local

Esta página proporciona información general sobre la instalación de Adobe Commerce en su propia infraestructura. El proceso de instalación implica la configuración del entorno del servidor, la obtención del software y las credenciales necesarios y la ejecución del comando de instalación.

Puede instalar el software local de Adobe Commerce en aproximadamente 30 a 60 minutos. Sin embargo, el tiempo necesario para configurar el entorno del servidor antes de la instalación varía en función de la experiencia y las tecnologías que seleccione.

>[!TIP]
>
>Debe tener conocimientos técnicos intermedios y acceso al servidor para continuar correctamente.

La instalación crea una tienda Adobe Commerce completamente funcional con [tienda orientada al cliente](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront) y [panel administrativo](https://experienceleague.adobe.com/en/docs/commerce-admin/start/admin/admin). Debe tener listas las credenciales de la base de datos, la información de dominio y las claves de autenticación antes de comenzar el proceso.

## Responsabilidades del comerciante

Con Adobe Commerce local, puede alojar y administrar su propia infraestructura, incluidos servidores, entornos de alojamiento y mantenimiento del sistema. Adobe proporciona asistencia específica para la aplicación principal de Commerce, que incluye:

- Acceso a actualizaciones y correcciones de productos
- Parches de seguridad para abordar vulnerabilidades
- Documentación completa para ayudarle a administrar y optimizar su solución autoalojada

Tiene control total sobre su entorno, lo que permite una mayor personalización y flexibilidad, pero es usted el responsable de garantizar el rendimiento, la seguridad y la escalabilidad de la infraestructura. Por ejemplo, usted es responsable de lo siguiente:

- El diseño, la implementación, la configuración, el mantenimiento, la resolución de problemas y las pruebas de rendimiento de todos los sistemas locales de Adobe Commerce.
   - Servidores, sistema operativo, bases de datos, [!DNL PHP], búsqueda, almacenamiento en caché, caché de página completa y red de distribución de contenido. Los temas comunes pueden incluir (entre otros) [!DNL Nginx/Apache], [!DNL PHP], [!DNL MySQL/MariaDB], [!DNL Redis], [!DNL Elasticsearch/OpenSearch], [!DNL RabbitMQ], [!DNL Varnish], [!DNL DNS], [!DNL SSL/TLS certificates] y cualquier [!DNL CDN] usado.
- Planificación de la capacidad, escalado automático, agrupación en clúster, backups, recuperación ante desastres
- Todos los datos de productos y clientes, diseño, configuración y configuración, mantenimiento de aplicaciones y bases de datos, implementación de código, actualizaciones de versiones y aplicación de parches
- Supervisión y alertas mediante APM/registro/alertas (por ejemplo, [!DNL New Relic], [!DNL Datadog], [!DNL ELK])
- Parches de seguridad para el sistema operativo, [!DNL PHP], base de datos, protección del middleware y actualizaciones

## Flujo de trabajo

El diagrama siguiente ilustra los pasos principales involucrados en la instalación de Adobe Commerce para entornos locales:

![Funcionamiento de la instalación](../assets/installation/on-premises-install.drawio.svg)

### Configuración del entorno del servidor

Instale y configure PHP, servidor web, base de datos y motor de búsqueda según los [requisitos previos](prerequisites/overview.md).

### Obtener claves de autenticación

Genere [claves de autenticación](prerequisites/authentication-keys.md) nuevas (o copie las claves existentes) desde Commerce Marketplace para acceder a los paquetes de Adobe Commerce Composer.

### Obtener el software de Adobe Commerce

Descargue con [Composer](prerequisites/commerce.md) (recomendado) o clone desde GitHub para contribuciones de desarrollo.

Si desea contribuir al código base de Magento Open Source o personalizar la aplicación, [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository) el repositorio de GitHub. Este método requiere estar familiarizado con GitHub y Composer.

### Instalación de la aplicación

Ejecute el comando de instalación con la configuración específica. Consulte [inicio rápido](composer.md) para ver ejemplos completos.

>[!NOTE]
>
>Si los pasos fallan porque el software necesario no está configurado correctamente, revise los [requisitos previos](prerequisites/overview.md).

### Compruebe la instalación

[Pruebe](next-steps/verify.md) tu tienda y el panel de administración para asegurarte de que todo funcione correctamente.

## Problemas comunes de instalación

- **Errores de permisos**: Asegúrese de que la propiedad y los permisos del sistema de archivos son correctos
- **Errores en la conexión a la base de datos**: Compruebe las credenciales de la base de datos y la conectividad de red
- **Errores en la clave de autenticación**: confirme que las claves de Commerce Marketplace son válidas y están activas
- **Límites de memoria**: Asegure una asignación de memoria PHP suficiente (se recomiendan un mínimo de 2 GB)
