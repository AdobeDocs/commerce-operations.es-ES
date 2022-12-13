---
title: Almacenamiento remoto para comercio en infraestructura en la nube
description: Consulte las instrucciones sobre cómo configurar el almacenamiento remoto para Adobe Commerce en la infraestructura de la nube.
source-git-commit: 2080950852e3c4e6da556733e56f68e0e8005530
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---


# Configuración del almacenamiento remoto para Commerce en la infraestructura de Cloud

Comenzando por el `ece-tools` paquete 2002.1.5, puede utilizar una variable de entorno para habilitar el módulo Almacenamiento remoto; sin embargo, el módulo Almacenamiento remoto tiene _limited_ compatibilidad con Adobe Commerce en infraestructura de nube. Adobe no puede solucionar problemas del servicio del adaptador de almacenamiento de terceros.

## Variable de entorno

La variable `REMOTE_STORAGE` se usa durante el [fase de implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) de un proyecto de infraestructura de nube.

### `REMOTE_STORAGE`

- **Predeterminado**—_Sin configurar_
- **Versión**—Commerce 2.4.2 y posteriores

Configure un _adaptador de almacenamiento_ para almacenar archivos multimedia en un contenedor de almacenamiento remoto y persistente mediante un servicio de almacenamiento, como AWS S3. Habilite el módulo Almacenamiento remoto para mejorar el rendimiento en proyectos en la nube con configuraciones complejas de varios servidores que deben compartir recursos. A continuación se muestra un ejemplo de configuración de almacenamiento remoto mediante el uso de `.magento.env.yaml` archivo:

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

### Establecer variable con la CLI de Cloud

Configure las variables `REMOTE_STORAGE` como [variable de nivel de entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) para que los archivos no se compartan entre los entornos de producción, ensayo e integración. La configuración de las variables a nivel de entorno ofrece la flexibilidad de usar únicamente almacenamiento remoto en entornos seleccionados, como excluir el uso del entorno de integración del almacenamiento remoto.

**Para agregar la variable de almacenamiento remoto mediante la CLI de Cloud**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

Esto crea un `REMOTE_STORAGE` con la configuración JSON especificada. La variable `REMOTE_STORAGE` toma una cadena JSON para configurar el almacenamiento remoto. El siguiente es un ejemplo de configuración JSON:

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

Después de crear la configuración y la implementación, los registros de implementación deben incluir información sobre la configuración del almacenamiento remoto, por ejemplo `INFO: Remote storage driver set to: "aws-s3"`

### Establecer variable con la interfaz web del proyecto

Como alternativa, puede utilizar la interfaz web del proyecto para agregar la variable al entorno adecuado.

**Para agregar la variable de almacenamiento remoto mediante la interfaz Web del proyecto**:

1. En el _Interfaz web del proyecto_, seleccione el entorno de la izquierda.

1. Haga clic en el **Configuración del entorno** icono.

1. En el _Configurar entorno_ haga clic en la **Variables** pestaña .

1. Haga clic en **Agregar variable**.

1. En el _Nombre_ , introduzca `env:REMOTE_STORAGE`

1. En el _Valor_ , añada la configuración JSON.

1. Select **Valor JSON** y **Sensible**; anular selección **Heredado por entornos secundarios**.

1. Haga clic en **Agregar variable**.

### Usar autenticación opcional

La variable `key` y `secret` son opcionales. Al crear la variable , puede ocultar la variable `key` y `secret` seleccionando `sensitive` . Con esta configuración, los valores no son visibles en la interfaz web. Consulte [Visibilidad de las variables](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) en el _Guía de Commerce on Cloud Infrastructure_.

Si desea utilizar un método de autenticación diferente, omita el `key` y `secret` desde la configuración JSON, Configure el método de autenticación alternativo y verifique que el servidor esté autorizado para el compartimento S3.

### Sincronizar el almacenamiento remoto

Después de habilitar el módulo Almacenamiento remoto, sincronice los archivos de medios actuales con la ubicación del almacén remoto.

**Para iniciar la sincronización**:

1. Utilice SSH para iniciar sesión en el entorno remoto con el almacenamiento remoto configurado.

1. Inicie la sincronización.

```bash
bin/magento remote-storage:sync 
```

## Configuración rápida

Si decide utilizar la solución de almacenamiento remoto con un proyecto de infraestructura en la nube de Adobe Commerce, use la variable [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) en la sección _Fly_ documentación para asegurarse de que la Optimización de imágenes Fough funciona con AWS S3.

Prepárese con su [Credenciales de formato](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). En los proyectos Pro, utilice SSH para conectarse al servidor y obtener las credenciales de la variable `/mnt/shared/fastly_tokens.txt` archivo. Los entornos de ensayo y producción tienen credenciales únicas. Debe obtener las credenciales de cada entorno.

Continúe configurando el almacenamiento remoto para proyectos en la nube con las siguientes tareas:

1. Configure un [Integración de back-end más rápida](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Crear lógica de VCL para [Autenticación de AWS S3](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Crear lógica de VCL para [solicitudes de back-end al compartimento de AWS S3](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
