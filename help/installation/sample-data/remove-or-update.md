---
title: Quitar o actualizar módulos de datos de ejemplo
description: Siga estos pasos para administrar los módulos de datos de ejemplo de Adobe Commerce y Magento Open Source.
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Quitar o actualizar módulos de datos de ejemplo

En este tema se explica cómo:

* [Quitar módulos de datos de ejemplo](#remove-sample-data-modules) desde una instalación de Adobe Commerce o Magento Open Source `composer.json`. Esta opción hace lo siguiente *no* quitar datos de ejemplo de la base de datos.

* [Preparar para actualizar datos de ejemplo](#prepare-to-update-sample-data) (por ejemplo, antes de actualizar la aplicación de Magento).

## Quitar módulos de datos de ejemplo

Introduzca el siguiente comando:

```bash
bin/magento sampledata:remove
```

La lista completa de módulos de datos de ejemplo es la siguiente:

Adobe Commerce y Magento Open Source:

* `magento/module-bundle-sample-data`
* `magento/module-catalog-rule-sample-data`
* `magento/module-catalog-sample-data`
* `magento/module-cms-sample-data`
* `magento/module-configurable-sample-data`
* `magento/module-customer-sample-data`
* `magento/module-downloadable-sample-data`
* `magento/module-grouped-product-sample-data`
* `magento/module-msrp-sample-data`
* `magento/module-offline-shipping-sample-data`
* `magento/module-product-links-sample-data`
* `magento/module-review-sample-data`
* `magento/module-sales-rule-sample-data`
* `magento/module-sales-sample-data`
* `magento/module-sample-data`
* `magento/module-swatches-sample-data`
* `magento/module-tax-sample-data`
* `magento/module-theme-sample-data`
* `magento/module-widget-sample-data`
* `magento/module-wishlist-sample-data`
* `magento/sample-data-media`

Solo Adobe Commerce:

* `magento/module-customer-balance-sample-data`
* `magento/module-gift-card-sample-data`
* `magento/module-gift-registry-sample-data`
* `magento/module-multiple-wishlist-sample-data`
* `magento/module-target-rule-sample-data`

## Preparar para actualizar datos de ejemplo

Este comando permite actualizar los datos de ejemplo antes de actualizar Adobe Commerce o Magento Open Source.

Para preparar los datos de ejemplo para la actualización, introduzca el siguiente comando:

```bash
bin/magento sampledata:reset
```

Después de eso, [actualizar la aplicación](../tutorials/uninstall.md#update-the-application).
