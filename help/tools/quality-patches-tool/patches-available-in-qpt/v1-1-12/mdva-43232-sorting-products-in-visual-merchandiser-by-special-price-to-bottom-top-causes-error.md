---
title: 'MDVA-43232: La ordenación de productos en el comerciante visual por precio especial a superior (o inferior) causa un error'
description: El parche de MDVA-43232 soluciona el problema de que la clasificación de productos en Visual Merchandiser por Precio especial al principio (o al final) provoca un error al guardar la categoría. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-43232. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Categories, Merchandising, Orders, Personalization, Products
role: Admin
exl-id: c977bec8-f99c-4799-abce-26aad49b77e8
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 58c984c2-e237-5c50-9718-500e40d1e82c
    internal-label: Merchandising
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: f37757d8-3174-5335-b977-1161792f965d
    internal-label: Personalization
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%
---
# MDVA-43232: La ordenación de productos en el comerciante visual por precio especial a superior (o inferior) causa un error

El parche de MDVA-43232 soluciona el problema de que la clasificación de productos en Visual Merchandiser por Precio especial al principio (o al final) provoca un error al guardar la categoría. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.12. El ID del parche es MDVA-43232. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.4 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La ordenación de productos en el comerciante visual por Precio especial al principio (o al final) provoca un error al guardar la categoría.

<u>Pasos a seguir</u>:

1. Asegúrese de que haya dos sitios web.
1. Vaya a **Tiendas** > **Configuración** > **Catálogo** > **Precio** y establezca el ámbito del precio del catálogo = Sitio web.
1. De nuevo, vaya a **Tiendas** > **Configuración** > **Catálogo** > **Comerciante visual** > **Atributos visibles para reglas de categoría** > y agregue Precio especial.
1. Cree un producto sencillo y asígnelo a ambos sitios web.
1. Agregue un precio especial al ámbito predeterminado del producto.
1. Cambie al ámbito de la otra tienda y anule el precio y el precio especial de ese producto.
1. Realice un reindexado de `catalog_product_price`.
1. Vaya a **Catálogo** > **Categorías** y cree una nueva categoría.
1. Añada una regla de categoría para filtrar los productos que tienen un precio especial.
1. Guarde la categoría.
1. En la sección Productos en categoría, establezca Orden = Precio especial en Superior (o Inferior).
1. Vuelva a guardar la categoría.

<u>Resultados esperados</u>:

La categoría se guarda sin errores.

<u>Resultados reales</u>:

Se genera una excepción:

```php
[2022-02-07T05:58:46.297621+00:00] report.CRITICAL: Exception: Item (Magento\Catalog\Model\Product\Interceptor) with the same ID "1" already exists. in /lib/internal/Magento/Framework/Data/Collection.php:407
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
