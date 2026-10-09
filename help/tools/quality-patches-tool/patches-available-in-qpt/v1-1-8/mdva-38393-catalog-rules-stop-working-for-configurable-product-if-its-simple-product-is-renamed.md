---
title: 'MDVA-38393: Las reglas de catálogo dejan de funcionar para productos configurables si se cambia el nombre de su producto simple'
description: El parche de MDVA-38393 corrige el problema de que las reglas de catálogo dejan de funcionar para un producto configurable si se cambia el nombre de su producto simple. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8. El ID del parche es MDVA-38393. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: Catalog Management, Categories, Configuration, Products
role: Admin
exl-id: 3d98671c-6ee7-4fe8-80d9-67fa697cae75
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '517'
ht-degree: 0%
---
# MDVA-38393: Las reglas de catálogo dejan de funcionar para productos configurables si se cambia el nombre de su producto simple

El parche de MDVA-38393 corrige el problema de que las reglas de catálogo dejan de funcionar para un producto configurable si se cambia el nombre de su producto simple. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.8. El ID del parche es MDVA-38393. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las reglas de catálogo dejan de funcionar para un producto configurable si se cambia el nombre de su producto simple.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con un producto simple asociado.
1. Cree una categoría.
1. Asigne únicamente el producto configurable a la nueva categoría.
1. Crear nuevas reglas de catálogo:
   * Condición = La categoría contiene \&lt;nuevo ID de categoría>
   * Acción = 50 % de descuento
   * Activo = Sí
1. Realice una reindexación.
1. Compruebe el producto configurable en el front-end (se debe aplicar el descuento).
1. Compruebe la tabla `catalogrule_product` (el producto simple debería tener un descuento).
1. Vaya al Administrador y cambie el nombre del producto simple. Esto agregaría un registro a la tabla `catalogrule_product_cl`.
1. Ejecute el cron o el comando `bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1`.
1. Compruebe la tabla `catalogrule_product`.

<u>Resultados esperados</u>:

El producto configurable tiene un descuento.

<u>Resultados reales</u>:

* Faltan los registros de descuento creados para los productos simples en la tabla `catalogrule_product`.
* El producto configurable en el front-end tiene el precio original completo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
