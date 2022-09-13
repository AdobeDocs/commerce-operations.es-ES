---
title: Hardware Recommendations
description: Revise una lista de hardware recomendado relacionado con el rendimiento óptimo de las implementaciones de Adobe Commerce y Magento Open Source.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---


# Recomendaciones de hardware

## CPU

[!DNL Commerce] los nodos web sirven para todas las solicitudes que no se almacenan en caché o que no se pueden almacenar en caché a través de la aplicación. Un núcleo de CPU puede servir alrededor de dos (a veces hasta cuatro) [!DNL Commerce] solicita de forma eficaz. Utilice la siguiente ecuación para determinar cuántos nodos o núcleos web necesita para procesar todas las solicitudes entrantes sin ponerlas en cola:

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

Si espera que la carga de una tienda cambie, puede aumentar manualmente el número de nodos/núcleos web durante un periodo de ventas activo. Alternativamente, se puede utilizar un modelo de escalado automático para ampliar automáticamente los niveles web.

## Memoria

### PHP

Magento tiene diferentes requerimientos de memoria PHP, según la implementación de su sistema.  En general, si está configurando una sola tienda de servidores, le recomendamos que configure la memoria PHP para 2G.  Si está configurando un sitio mediante la implementación de canalización, recomendamos 2 GB en el servidor de compilación y 1 GB en los nodos web.

Escenarios y requisitos de memoria de PHP esperados:

* El nodo web solo sirve para páginas de tienda: 256 MB
* Webnode sirve para páginas de administración con un catálogo grande: 1 GB
* [!DNL Commerce] cron indexando un sitio con un catálogo grande: >256 MB (véase [configuración avanzada](../performance/advanced-setup.md) para optimizar el rendimiento).
* [!DNL Commerce] compilar e implementar recursos estáticos: 756 MB
* [!DNL Commerce] generación de perfiles del kit de herramientas de rendimiento: >1 GB de RAM PHP, >16 MB [!DNL MySQL] Ajustes de TMP_TABLE_SIZE y MAX_HEAP_TABLE_SIZE

### [!DNL MySQL]

La variable [!DNL Commerce] La base de datos (así como cualquier otra base de datos) es sensible a la cantidad de memoria disponible para almacenar datos e índices. Para aprovechar de forma eficaz [!DNL MySQL] la indexación de datos, la cantidad de memoria disponible debe ser, como mínimo, casi la mitad del tamaño de los datos almacenados en la base de datos.

### Cachés

Si va a implementar varias [!DNL Commerce] y utilizando Redis o [!DNL Varnish] para sus cachés, tenga en cuenta los siguientes principios:

* [!DNL Varnish] la invalidación de memoria caché de página completa es efectiva, recomiende suficiente memoria asignada a [!DNL Varnish] para guardar las páginas más populares en la memoria
* La caché de sesión es un buen candidato para configurar para una instancia separada de Redis.  La configuración de memoria para este tipo de caché debe tener en cuenta la estrategia de abandono del carro de compras del sitio y el tiempo que una sesión debe esperar permanecer en la caché
* Redis debería tener suficiente memoria asignada para guardar todas las demás cachés en la memoria para un rendimiento óptimo.  La caché de bloques será el factor clave para determinar la cantidad de memoria que se configurará.  La caché de bloque crece en relación con el número de páginas en un sitio (número de skus x número de vistas de tienda)

## Ancho de banda de la red

El ancho de banda de red suficiente es uno de los requisitos clave para el intercambio de datos entre nodos web, bases de datos, servidores de almacenamiento en caché/sesión y otros servicios. Porque [!DNL Commerce] aprovecha efectivamente el almacenamiento en caché para obtener un alto rendimiento, su sistema puede intercambiar datos activamente con servidores de almacenamiento en caché como Redis. Si Redis está ubicado en un servidor remoto, debe proporcionar un canal de red suficiente entre los nodos web y el servidor caché para evitar cuellos de botella en las operaciones de lectura y escritura.
