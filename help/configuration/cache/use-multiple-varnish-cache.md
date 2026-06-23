---
title: Borrado de caché con varias instancias de barniz
description: Descubra cómo funciona la limpieza de caché con varias instancias de Barniz en Adobe Commerce. Descubra las prácticas recomendadas de configuración y administración.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
badgePaas: label="En las instalaciones" type="Informative" url="https://experienceleague.adobe.com/es/docs/commerce/user-guides/product-solutions" tooltip="Solo se aplica a los proyectos locales de Adobe Commerce."
autotag-review: '2026-06-22T22:16:50.500Z'
TQID: 'https://experienceleague.adobe.com/GeX8wkpM1rLLWM7jMhP2r-SJ8uV-x7fLXC8WEazZQDo'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 206
ht-degree: 0%

---

# Borrado de caché con varias instancias de barniz

Adobe Commerce admite varias instancias de Barniz de forma predeterminada.

En este tema se muestran los conceptos básicos para configurar varias instancias de Varnish con Commerce.

{{varnish-config-cloud}}

## Configuración para depurar varias instancias de Barniz

Commerce purga los hosts de Varnish después de configurar los hosts de Varnish mediante el comando [`magento setup:config:set`](../../installation/tutorials/deployment.md).

Debe usar el parámetro `--http-cache-hosts` para especificar una lista separada por comas de hosts de Varnish y puertos de escucha. (No separe los hosts con caracteres de espacio.)

El formato del parámetro debe ser `<hostname or ip>:<listen port>`, donde puede omitir `<listen port>` si es el puerto 80.

Por ejemplo,

```shell
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

A continuación, puede purgar todos los hosts de Varnish cuando actualice la caché de Commerce (también conocida como _limpieza_ de la caché) en Admin o mediante la línea de comandos.

Para actualizar la caché con el Administrador, haga clic en **SISTEMA** > Herramientas > **Administración de caché** y, a continuación, haga clic en **Vaciar caché de Magento** en la parte superior de la página. (También puede actualizar tipos de caché individuales).

Para actualizar la caché de varias instancias de Varnish desde cli, use el comando [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) como [propietario del sistema de archivos](../../installation/prerequisites/file-system/overview.md).
