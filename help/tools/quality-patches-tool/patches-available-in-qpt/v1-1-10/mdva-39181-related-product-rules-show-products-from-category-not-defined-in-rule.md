---
title: "MDVA-39181: Las reglas de producto relacionadas muestran productos de la categoría sin definir en la regla"
description: El parche MDVA-39181 resuelve el problema en el que las reglas de producto relacionadas muestran productos de una categoría no definida en la regla. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10. El ID del parche es MDVA-39181. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Categories, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-39181: Las reglas de producto relacionadas muestran productos de la categoría sin definir en la regla

El parche MDVA-39181 resuelve el problema en el que las reglas de producto relacionadas muestran productos de una categoría no definida en la regla. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10. El ID del parche es MDVA-39181. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las reglas de productos relacionadas muestran productos de categorías no definidas en la regla.

<u>Requisitos previos</u>:

Instalar datos de ejemplo.

<u>Pasos a seguir</u>:

1. Cree una marca de atributo y agréguela al conjunto de atributos **Tops**.
1. Elige las chaquetas **Josie**, **Augusta** e **Ingrid** para agregarlas al Brand Kitty desde **Mujer** > **Tops** > **Chaquetas de la categoría**.
1. Elige las chaquetas **Beaumont**, **Hyperion** y **Kenobi** para añadirlas a Brand Kitty desde **Hombres** > **Tops** > **Categoría de chaqueta**.
1. Crear un producto relacionado con:

   ```markdown
   Apply To: Related Products
   Customer Segments: All
   ```

   * Productos para hacer coincidir:

   ```markdown
   If ALL of these conditions are TRUE
     Category is {}
     Brand is {}
   ```

   * Productos para mostrar:

   ```markdown
   If ALL of these conditions are TRUE
      Product Category is the same as Matched Product Category
      Product brand is Matched Product Brand
   ```

1. Abra el SKU WJ04 en la parte frontal y compruebe los productos relacionados.
1. Actualice el identificador de categoría de **Mujeres** > **Tops** > **Chaquetas** en caso de que sea diferente a esto.

<u>Resultados esperados</u>:

En los productos relacionados solo se muestran los productos de la misma marca y la misma categoría secundaria.

<u>Resultados reales</u>:

Los productos relacionados se muestran de la misma marca pero de una categoría principal aleatoria.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
