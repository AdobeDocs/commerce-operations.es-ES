---
title: Configuración de Redis con AWS ElastiCache
description: Aprenda a utilizar AWS ElastiCache como backend de Redis para Adobe Commerce en EC2. Descubra la instalación, configuración y validación desde la línea de comandos.
feature: Configuration, Cache
autotag-review: '2026-06-22T21:54:39.355Z'
TQID: 'https://experienceleague.adobe.com/p4-Pyc3yWwokyFOAyAjN3r1Ic26brx83bPf-GZQNSN8'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: fbb1d92d5f8537e6f1436cd985af120114883df6
workflow-type: tm+mt
source-wordcount: 289
ht-degree: 0%

---


# Configuración de Redis con AWS ElastiCache

A partir de Commerce 2.4.3, las instancias alojadas en Amazon EC2 pueden utilizar una AWS ElastiCache en lugar de una instancia local de Redis.

>[!WARNING]
>
>Esta sección solo es aplicable a las instancias de Commerce que se ejecutan en VPC Amazon EC2.

## Requisitos previos

- **Crear una caché sin servidor Redis OSS**: desde AWS Management Console, cree la caché Redis en la misma región y VPC de la instancia EC2. Para obtener instrucciones, consulte la [documentación de AWS Elasticache](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html).

- **Compruebe la conexión con su instancia de Commerce EC2**

   - Abra una conexión SSH a la instancia EC2.
   - En la instancia EC2, instale el cliente Redis:

     ```shell
     sudo apt-get install redis
     ```

   - Agregar una regla de entrada al grupo de seguridad EC2: Tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Agregue una regla de entrada al grupo de seguridad de clúster de ElastiCache: Tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Conéctese a la CLI de Redis:

     ```shell
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### Configuración de Commerce para utilizar el clúster

Commerce admite varios tipos de configuraciones de almacenamiento en caché. Por lo general, las configuraciones de almacenamiento en caché se dividen entre front-end y back-end. El almacenamiento en caché de front-end se clasifica como `default` y se usa para cualquier tipo de caché. Puede personalizar o dividir en cachés de nivel inferior para lograr un mejor rendimiento. Una configuración común de Redis es separar la caché predeterminada y la caché de página en su propia base de datos de Redis (RDB).

Ejecute `setup` comandos para especificar los extremos de Redis.

Para configurar Commerce para Redis como almacenamiento en caché predeterminado:

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Para configurar Commerce para el almacenamiento en caché de páginas de Redis:

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Para configurar Commerce para que utilice Redis para el almacenamiento de sesión:

```shell
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## Verificar conectividad

**Para comprobar que Commerce está hablando con ElastiCache**:

1. Abra una conexión SSH a la instancia de Commerce EC2.
1. Inicie el monitor de Redis.

   ```shell
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Abra una página en la interfaz de usuario de Commerce.
1. Compruebe la [salida de caché](#verify-connectivity) en su terminal.
