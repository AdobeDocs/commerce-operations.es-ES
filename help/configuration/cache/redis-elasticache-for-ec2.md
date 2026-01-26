---
title: Configuración de Redis con AWS ElastiCache
description: Para instancias de Commerce alojadas en EC2, aprenda a utilizar AWS ElastiCache en lugar de una instancia local de Redis. Descubra la configuración de la línea de comandos, las opciones de configuración y las técnicas de validación.
feature: Configuration, Cache
source-git-commit: b66479ee1350d92c1d59212283222e5068c263a6
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# Configuración de Redis con AWS ElastiCache

A partir de Commerce 2.4.3, las instancias alojadas en Amazon EC2 pueden utilizar una AWS ElastiCache en lugar de una instancia local de Redis.

>[!WARNING]
>
>Esta sección solo es aplicable a las instancias de Commerce que se ejecutan en VPC Amazon EC2. No funciona para instalaciones locales.

## Requisitos previos

- **Crear una caché sin servidor Redis OSS**: desde AWS Management Console, cree la caché Redis en la misma región y VPC de la instancia EC2. Para obtener instrucciones, consulte la [documentación de AWS Elasticache](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html).

- **Compruebe la conexión con su instancia de Commerce EC2**

   - Abra una conexión SSH a la instancia EC2.
   - En la instancia EC2, instale el cliente Redis:

     ```bash
     sudo apt-get install redis
     ```

   - Agregar una regla de entrada al grupo de seguridad EC2: Tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Agregue una regla de entrada al grupo de seguridad de clúster de ElastiCache: Tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Conéctese a la CLI de Redis:

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### Configuración de Commerce para utilizar el clúster

Commerce admite varios tipos de configuraciones de almacenamiento en caché. Por lo general, las configuraciones de almacenamiento en caché se dividen entre front-end y back-end. El almacenamiento en caché de front-end se clasifica como `default` y se usa para cualquier tipo de caché. Puede personalizar o dividir en cachés de nivel inferior para lograr un mejor rendimiento. Una configuración común de Redis es separar la caché predeterminada y la caché de página en su propia base de datos de Redis (RDB).

Ejecute `setup` comandos para especificar los extremos de Redis.

Para configurar Commerce para Redis como almacenamiento en caché predeterminado:

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Para configurar Commerce para el almacenamiento en caché de páginas de Redis:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Para configurar Commerce para que utilice Redis para el almacenamiento de sesión:

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## Verificar conectividad

**Para comprobar que Commerce está hablando con ElastiCache**:

1. Abra una conexión SSH a la instancia de Commerce EC2.
1. Inicie el monitor de Redis.

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Abra una página en la interfaz de usuario de Commerce.
1. Compruebe la [salida de caché](#verify-the-redis-connection) en su terminal.
