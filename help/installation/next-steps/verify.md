---
title: Verifique la instalación
description: Siga estos pasos para confirmar que la instalación de Adobe Commerce o Magento Open Source local se ha realizado correctamente.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---


# Verifique la instalación

Vaya a la [storefront](https://glossary.magento.com/storefront) en un explorador web. Por ejemplo, si la base de la instalación [URL](https://glossary.magento.com/url) es `http://www.example.com`, indíquela en la dirección del navegador o en la barra de ubicación.

La siguiente figura muestra una página de tienda de muestra. Si se muestra de la siguiente manera, la instalación se ha realizado correctamente.

![Tienda con el tema de Luma](../../assets/installation/install-success_store-luma.png)

## Verificar la tienda (sin datos de ejemplo)

Vaya a la tienda en un navegador web. Por ejemplo, si la URL base de la instalación es `http://www.example.com`, indíquela en la dirección del navegador o en la barra de ubicación.

La siguiente figura muestra una página de tienda de muestra. Si se muestra de la siguiente manera, la instalación se ha realizado correctamente.

![Tienda que comprueba una instalación correcta](../../assets/installation/install-success_store.png)

Si la página muestra una `404 (Not Found)` error o no muestra estilos, consulte [resolución de problemas](https://support.magento.com/hc/en-us/articles/360032994352).

## Verificar el administrador

Vaya a la [Administrador](https://glossary.magento.com/magento-admin) en un explorador web. Por ejemplo, si la URL base de la instalación es `http://www.example.com`y el URI de administrador es `admin_au1nT`, introduzca `http://www.example.com/admin_au1nT` en la dirección o barra de ubicación del explorador.

(El [Administrador](https://glossary.magento.com/admin) El URI se especifica mediante el valor de la variable `backend-frontname` parámetro de instalación).

Cuando se le solicite, inicie sesión como administrador.

La siguiente figura muestra una página de administración. Si se muestra de la siguiente manera, la instalación se ha realizado correctamente.

![Administrador que comprueba una instalación correcta](../../assets/installation/install_success_admin.png)

Si la página no muestra estilos, consulte [solución de problemas](https://support.magento.com/hc/en-us/articles/360032994352).

Si aparece un error 404 (No encontrado) similar al siguiente, consulte [Error de versión PHP o 404 al acceder a Adobe Commerce en el explorador](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
