---
title: 'MDVA-31763: Las reglas de precios de catálogo se revierten hasta la reindexación manual'
description: El parche MDVA-31763 resuelve el problema en el que las reglas de precios de catálogo se revierten hasta la reindexación manual. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. El ID del parche es MDVA-31763. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: Catalog Management, Orders, Price Rules
role: Admin
exl-id: 1d144bfc-c26b-43d0-a80c-26a9c2d8ef32
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: a507b1ed-4937-53da-97ae-57d36bd5b9e0
    internal-label: Price Rules
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '520'
ht-degree: 0%
---
# MDVA-31763: Las reglas de precios de catálogo se revierten hasta la reindexación manual

El parche MDVA-31763 resuelve el problema en el que las reglas de precios de catálogo se revierten hasta la reindexación manual. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.5. El ID del parche es MDVA-31763. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se ejecuta el indexador parcial `catalogrule_product` en productos configurables, las reglas del catálogo desaparecen.

<u>Pasos a seguir</u>:

1. Inicie sesión en el servidor de administración.
1. Vaya a **Tiendas** > **Atributos** > **Producto** y busque el atributo &quot;fabricante&quot;.
   * Agregue algunas opciones y establezca &quot;Usar para condiciones de regla de promoción&quot; en *Sí*.
1. Vaya a **Tiendas** > **Atributos** > **Conjuntos de atributos**.
   * Seleccione el conjunto de atributos predeterminado y agréguele el atributo &quot;manufacturer&quot;.
1. Cree un producto configurable con un par de variaciones.
1. Establezca el valor de atributo &quot;fabricante&quot; para el producto configurable creado anteriormente.
1. Crear reglas de catálogo:
   * Activo = Sí
   * Sitios web = Sitio web principal
   * Grupos de clientes = SIN SESIÓN INICIADA
   * Condiciones: fabricante = \&lt;valor seleccionado para el producto configurable>
   * Acciones: cualquier descuento
1. Haga un índice completo.
1. Compruebe el precio del producto en PDP y asegúrese de que el precio es correcto.
1. Actualice el atributo &quot;weight&quot; del producto configurable creado.
1. Compruebe el precio del producto en PDP.

<u>Resultados esperados</u>:

Las reglas de precios de catálogo establecidas en los productos configurables no se eliminan durante el reindexado parcial.

<u>Resultados reales</u>:

Las reglas de precios de catálogo establecidas en los productos configurables desaparecen durante el reindexado parcial.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
