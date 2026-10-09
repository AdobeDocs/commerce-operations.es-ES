---
title: Quitar o actualizar módulos de datos de ejemplo
description: Siga estos pasos para administrar los módulos de datos de ejemplo de Adobe Commerce.
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%
---
# Quitar o actualizar módulos de datos de ejemplo

En este tema se explica cómo:

* [Quitar módulos de datos de ejemplo](#remove-sample-data-modules) de una instalación de Adobe Commerce `composer.json`. Esta opción *no* quita datos de ejemplo de la base de datos.

* [Prepárese para actualizar los datos de ejemplo](#prepare-to-update-sample-data) (por ejemplo, antes de actualizar la aplicación de Magento).

## Quitar módulos de datos de ejemplo

Introduzca el siguiente comando:

```shell
bin/magento sampledata:remove
```

La lista completa de módulos de datos de ejemplo es la siguiente:

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

## Preparar para actualizar datos de ejemplo

Este comando permite actualizar los datos de ejemplo antes de actualizar Adobe Commerce.

Para preparar los datos de ejemplo para la actualización, introduzca el siguiente comando:

```shell
bin/magento sampledata:reset
```

Después de eso, [actualice la aplicación](../tutorials/uninstall.md#update-the-application).
