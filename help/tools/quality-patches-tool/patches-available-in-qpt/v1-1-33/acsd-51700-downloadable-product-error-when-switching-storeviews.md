---
title: 'ACSD-51700: Error al cambiar las vistas de tienda en la página de edición descargable del producto'
description: Aplique el parche ACSD-51700 para corregir el problema de Adobe Commerce donde se produce un error al cambiar de vista de tienda en una página de edición de producto descargable en el administrador.
feature: Products
role: Admin
exl-id: dd3da026-ac72-440c-8632-8a3ca27fc134
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%
---
# ACSD-51700: Error al cambiar las vistas de tienda en la página de edición descargable del producto

El parche de ACSD-51700 corrige el problema en el que se produce un error al cambiar de vista de tienda en una página de edición de producto descargable en el administrador. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.33. El ID del parche es ACSD-51700. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p1

## Problema

Se produce un error al cambiar las vistas de la tienda en una página de edición de productos descargable en el administrador.

<u>Pasos a seguir</u>:

1. Cree un producto descargable con el nombre [!DNL SKU] y el precio. No añada ningún vínculo y guarde el producto.
1. Cambie de todas las vistas de tienda a la vista de tienda predeterminada.
1. Cree un vínculo para el producto descargable y guárdelo.
1. Cambie de la vista de tienda predeterminada a todas las vistas de tienda.

<u>Resultados esperados</u>:

Los productos vinculados están visibles.

<u>Resultados reales</u>:

Se muestra el siguiente error:

*Funcionalidad obsoleta: number_format(): Pasar nulo al parámetro #1 ($num) del tipo float está obsoleto en vendor/magento/module-downloadable/Ui/DataProvider/Product/Form/Modifier/Data/Links.php en la línea 228*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
