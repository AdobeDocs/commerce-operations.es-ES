---
title: Hardware Recommendations
description: Revise una lista de hardware recomendado relacionado con el rendimiento óptimo de las implementaciones de Adobe Commerce.
feature: Best Practices, Install
exl-id: ab548c4b-6f56-4409-a4ed-5c959939e04b
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Recomendaciones de hardware

## CPU

[!DNL Commerce] los nodos web sirven a todas las solicitudes que no se almacenan en caché o que no se pueden almacenar en caché a través de la aplicación. Un núcleo de CPU puede servir alrededor de dos (a veces hasta cuatro) [!DNL Commerce] solicitudes de forma eficaz. Utilice la siguiente ecuación para determinar cuántos nodos/núcleos web necesita para procesar todas las solicitudes entrantes sin ponerlas en cola:

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

Si espera que cambie la carga de una tienda, puede aumentar manualmente el número de nodos/núcleos web durante un periodo de ventas activo. Alternativamente, se puede utilizar un modelo de escalado automático para ampliar automáticamente los niveles web.

## Memoria

### PHP

El Magento tiene diferentes requisitos de memoria PHP, basados en la implementación de su sistema.  En general, si está configurando un único almacén de servidores, le recomendamos que configure la memoria PHP para 2G.  Si va a configurar un sitio mediante la implementación de canalización, le recomendamos 2 GB en el servidor de compilación y 1 GB en los nodos web.

Escenarios y requisitos de memoria PHP esperados:

* Nodo web que solo sirve páginas de tienda: 256 MB
* Nodo web que sirve páginas de administración con un catálogo grande: 1 GB
* [!DNL Commerce] cron indexando un sitio con un catálogo grande: >256 MB (Consulte [de configuración avanzada](../performance/advanced-setup.md) para optimizar el rendimiento).
* [!DNL Commerce] compilación e implementación de recursos estáticos: 756 MB
* [!DNL Commerce] Generación de perfiles de rendimiento: >1 GB PHP RAM, >16 MB [!DNL MySQL] Configuración de TMP_TABLE_SIZE y MAX_HEAP_TABLE_SIZE

### [!DNL MySQL]

El [!DNL Commerce] La base de datos de (así como cualquier otra base de datos) es sensible a la cantidad de memoria disponible para almacenar datos e índices. Para aprovechar de forma eficaz [!DNL MySQL] indexación de datos, la cantidad de memoria disponible debe ser, como mínimo, cercana a la mitad del tamaño de los datos almacenados en la base de datos.

### Cachés

Si va a implementar varias [!DNL Commerce] y usar Redis o [!DNL Varnish] para sus cachés, tenga en cuenta los siguientes principios:

* [!DNL Varnish] la invalidación de la memoria caché de la página completa es efectiva, se recomienda asignar suficiente memoria a [!DNL Varnish] para guardar las páginas más populares en la memoria
* La caché de sesión es un buen candidato para configurar para una instancia independiente de Redis.  La configuración de memoria para este tipo de caché debe tener en cuenta la estrategia de abandono del carro de compras del sitio y el tiempo que una sesión debería esperar permanecer en la caché
* Redis debería tener suficiente memoria asignada para guardar todas las demás cachés en la memoria para un rendimiento óptimo.  La caché de bloques será el factor clave para determinar la cantidad de memoria que se va a configurar.  La caché de bloques aumenta en relación con el número de páginas de un sitio (número de SKU x número de vistas de tiendas)

## Ancho de banda de red

Un ancho de banda de red suficiente es uno de los requisitos clave para el intercambio de datos entre nodos web, bases de datos, servidores de almacenamiento en caché/sesión y otros servicios. Porque [!DNL Commerce] aprovecha eficazmente el almacenamiento en caché para obtener un alto rendimiento, su sistema puede intercambiar datos de forma activa con servidores de almacenamiento en caché como Redis. Si Redis se encuentra en un servidor remoto, debe proporcionar un canal de red suficiente entre los nodos web y el servidor de almacenamiento en caché para evitar cuellos de botella en las operaciones de lectura y escritura.
