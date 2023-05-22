---
title: Almacenamiento remoto para Commerce en la infraestructura en la nube
description: Consulte las instrucciones sobre cómo configurar el almacenamiento remoto para Adobe Commerce en la infraestructura en la nube.
feature: Configuration, Cloud, Storage
exl-id: da352466-13f2-42e4-a589-3b0a89728467
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Configuración del almacenamiento remoto para Commerce en la infraestructura de Cloud

Comenzando por `ece-tools` paquete 2002.1.5, puede utilizar una variable de entorno para habilitar el módulo Almacenamiento remoto; sin embargo, el módulo Almacenamiento remoto tiene _limitado_ compatibilidad con Adobe Commerce en la infraestructura en la nube. El Adobe no puede solucionar por completo el problema del servicio del adaptador de almacenamiento de terceros.

## Variable de entorno

El `REMOTE_STORAGE` se utiliza durante la [fase de implementación](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html) de un proyecto de infraestructura en la nube.

### `REMOTE_STORAGE`

- **Predeterminado**—_Sin configurar_
- **Versión**—Commerce 2.4.2 y posterior

Configurar un _adaptador de almacenamiento_ para almacenar archivos multimedia en un contenedor de almacenamiento remoto persistente mediante un servicio de almacenamiento, como AWS S3. Habilite el módulo Almacenamiento remoto para mejorar el rendimiento en proyectos en la nube con configuraciones complejas de varios servidores que deben compartir recursos. A continuación se muestra un ejemplo de configuración de almacenamiento remoto mediante el `.magento.env.yaml` archivo:

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

Configure las variables `REMOTE_STORAGE` como una variable [variable de nivel de entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html) para que los archivos no se compartan entre los entornos Producción, Ensayo e Integración. La configuración de las variables en el nivel de entorno ofrece la flexibilidad de utilizar únicamente el almacenamiento remoto en entornos seleccionados, como la exclusión del uso del entorno de integración del almacenamiento remoto.

**Para agregar la variable de almacenamiento remoto mediante la CLI de la nube**:

```bash
magento-cloud variable:create --level environment --name REMOTE_STORAGE --json true --inheritable false --value '{"driver":"aws-s3","prefix":"uat","config":{"bucket":"aws-bucket-id","region":"eu-west-1","key":"optional-key","secret":"optional-secret"}}'
```

Esto crea un `REMOTE_STORAGE` con la configuración JSON especificada. El `REMOTE_STORAGE` toma una cadena JSON para configurar el almacenamiento remoto. A continuación se muestra un ejemplo de configuración de JSON:

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

**Para agregar la variable de almacenamiento remoto mediante la interfaz Web de Project**:

1. En el _Interfaz web de Project_, seleccione el entorno de la izquierda.

1. Haga clic en **Configurar el entorno** icono.

1. En el _Configurar entorno_ , haga clic en el **Variables** pestaña.

1. Clic **Agregar variable**.

1. En el _Nombre_ , introduzca `REMOTE_STORAGE`

1. En el _Valor_ , agregue la configuración JSON.

1. Seleccionar **Valor JSON** y **Sensible**; anular selección **Heredado por entornos secundarios**.

1. Clic **Agregar variable**.

### Utilizar autenticación opcional

El `key` y `secret` son opcionales. Cuando cree la variable, puede ocultar las variables `key` y `secret` seleccionando la opción `sensitive` opción. Con esta configuración, los valores no son visibles en la interfaz web. Consulte [Visibilidad variable](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/variable-levels.html#visibility) en el _Guía de Commerce en infraestructura en la nube_.

Si desea utilizar un método de autenticación diferente, omita el `key` y `secret` en la configuración JSON,. Configure el método de autenticación alternativo y verifique que el servidor esté autorizado para el compartimento S3.

### Sincronizar el almacenamiento remoto

Después de habilitar el módulo Almacenamiento remoto, sincronice los archivos multimedia actuales con la ubicación del almacén remoto.

**Para iniciar la sincronización**:

1. Utilice SSH para iniciar sesión en el entorno remoto con el almacenamiento remoto configurado.

1. Inicie la sincronización.

```bash
bin/magento remote-storage:sync 
```

## Configuración rápida

Si decide utilizar la solución de almacenamiento remoto con un proyecto de infraestructura en la nube de Adobe Commerce, utilice el [Amazon S3](https://docs.fastly.com/en/guides/amazon-s3) directrices en la _Rápido_ documentación para garantizar que Fastly Image Optimization funciona con AWS S3.

Prepárese con su [Credenciales de Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html#get-fastly-credentials). En proyectos Pro, utilice SSH para conectarse a su servidor y obtener las credenciales de Fastly desde el `/mnt/shared/fastly_tokens.txt` archivo. Los entornos de ensayo y producción tienen credenciales únicas. Debe obtener las credenciales de cada entorno.

Siga configurando el almacenamiento remoto para proyectos en la nube con las siguientes tareas:

1. Configurar un [Integración de back-end rápida](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/Edge-Modules/EDGE-MODULE-OTHER-CMS-INTEGRATION.md).

1. Crear lógica VCL para [Autenticación de AWS S3](https://docs.fastly.com/en/guides/amazon-s3#using-an-amazon-s3-private-bucket).

1. Crear lógica VCL para [solicitudes back-end al bloque de AWS S3](https://developer.fastly.com/reference/vcl/variables/backend-connection/req-backend/).
