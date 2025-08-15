---
title: Almacenamiento remoto para Commerce en la infraestructura en la nube
description: Consulte las instrucciones sobre cómo configurar el almacenamiento remoto para Adobe Commerce en la infraestructura en la nube.
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Configuración del almacenamiento remoto para Commerce en la infraestructura en la nube

A partir del paquete 2002.1.5 de `ece-tools`, puede utilizar una variable de entorno para habilitar el módulo Almacenamiento remoto; sin embargo, el módulo Almacenamiento remoto tiene compatibilidad de _limitada_ en Adobe Commerce en la infraestructura en la nube. Adobe no puede solucionar por completo los problemas del servicio del adaptador de almacenamiento de terceros.

## Variable de entorno

La variable `REMOTE_STORAGE` se usa durante la [fase de implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) de un proyecto de infraestructura en la nube.

### `REMOTE_STORAGE`

- **Predeterminado**—_No establecido_
- **Versión**: Commerce 2.4.2 y posterior

Configure un _adaptador de almacenamiento_ para almacenar archivos multimedia en un contenedor de almacenamiento remoto persistente mediante un servicio de almacenamiento, como AWS S3. Habilite el módulo Almacenamiento remoto para mejorar el rendimiento en proyectos en la nube con configuraciones complejas de varios servidores que deben compartir recursos. El siguiente es un ejemplo de configuración de almacenamiento remoto que utiliza el archivo `.magento.env.yaml`:

```yaml
stage:
  deploy:
    REMOTE_STORAGE:
      driver: aws-s3 # Required
      prefix: cloud # Optional
      config:
        bucket: my-bucket # Required
        region: my-region # Required
        key: my-key # Optional
        secret: my-secret-key # Optional
```

### Establecer variable con CLI de nube

Establezca la variable `REMOTE_STORAGE` como una [variable de nivel de entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) para que los archivos no se compartan entre los entornos Producción, Ensayo e Integración. La configuración de las variables en el nivel de entorno ofrece la flexibilidad de utilizar únicamente el almacenamiento remoto en entornos seleccionados, como la exclusión del uso del entorno de integración del almacenamiento remoto.

**Para agregar la variable de almacenamiento remoto mediante la CLI de nube**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

Esto crea una variable `REMOTE_STORAGE` con la configuración JSON especificada. La variable `REMOTE_STORAGE` toma una cadena JSON para configurar el almacenamiento remoto. A continuación se muestra un ejemplo de configuración de JSON:

```json
{
  "driver": "aws-s3",
  "prefix": "uat",
  "config": {
    "bucket": "aws-bucket-id",
    "region": "aws-region-id",
    "key": "optional-key",
    "secret": "optional-secret"
  }
}
```

Después de crear la configuración e implementar, los registros de implementación deben incluir información sobre la configuración del almacenamiento remoto, por ejemplo `INFO: Remote storage driver set to: "aws-s3"`

### Establecer variable con la interfaz Web de Project

También puede utilizar la interfaz Web de Project para agregar la variable al entorno adecuado.

**Para agregar la variable de almacenamiento remoto mediante la interfaz web de Project**:

1. En la _Interfaz web de proyectos_, seleccione el entorno de la izquierda.

1. Haga clic en el icono **Configurar entorno**.

1. En la vista _Configurar entorno_, haga clic en la ficha **Variables**.

1. Haga clic en **Agregar variable**.

1. En el campo _Nombre_, escriba `REMOTE_STORAGE`

1. En el campo _Value_, agregue la configuración JSON.

1. Seleccione **valor JSON** y **Sensible**; anule la selección de **Heredado por entornos secundarios**.

1. Haga clic en **Agregar variable**.

### Utilizar autenticación opcional

`key` y `secret` son opcionales. Cuando cree la variable, puede ocultar `key` y `secret` si selecciona la opción `sensitive`. Con esta configuración, los valores no son visibles en la interfaz web. Consulte [Visibilidad variable](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) en la guía de _Commerce en infraestructura de nube_.

Si desea utilizar un método de autenticación diferente, omita `key` y `secret` de la configuración JSON,. Configure el método de autenticación alternativo y verifique que el servidor esté autorizado para el compartimento S3.

### Sincronizar el almacenamiento remoto

Después de habilitar el módulo Almacenamiento remoto, sincronice los archivos multimedia actuales con la ubicación del almacén remoto.

**Para iniciar la sincronización**:

1. Utilice SSH para iniciar sesión en el entorno remoto con el almacenamiento remoto configurado.

1. Inicie la sincronización.

```bash
bin/magento remote-storage:sync 
```

## Configuración rápida

Si decide utilizar la solución de almacenamiento remoto con un proyecto de infraestructura en la nube de Adobe Commerce, use las directrices de [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) de la documentación de _Fastly_ para asegurarse de que Fastly Image Optimization funciona con AWS S3.

Prepárese con sus [credenciales de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). En proyectos Pro, use SSH para conectarse a su servidor y obtener las credenciales de Fastly del archivo `/mnt/shared/fastly_tokens.txt`. Los entornos de ensayo y producción tienen credenciales únicas. Debe obtener las credenciales de cada entorno.

Siga configurando el almacenamiento remoto para proyectos en la nube con las siguientes tareas:

1. Configure una [integración back-end de Fastly](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Crear lógica VCL para [autenticación de AWS S3](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Cree la lógica VCL para [solicitudes de servidor al bloque AWS S3](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
