---
title: 'ACSD-48417: Error SQL después de crear un cambio de programación'
description: Aplique el parche ACSD-48417 para corregir el problema de Adobe Commerce en el que aparece un error SQL después de crear un cambio de programación para un producto y guardar otro.
feature: Storage
role: Admin
exl-id: c8e7c7aa-ac53-4218-8c3c-ea2240af17c9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-48417: Error SQL después de crear un cambio de programación

El parche ACSD-48417 corrige el problema en el que aparece un error SQL después de crear un cambio de programación para un producto y guardar otro. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26. El ID del parche es ACSD-48417. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Aparece un error de SQL después de crear un cambio de programación para un producto y guardar otro producto.

<u>Pasos a seguir</u>:

1. Instale Magento 2.4: desarrolle EE + datos de muestra.
1. Vaya al panel de administración > **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Edite cualquier producto (por ejemplo, la bolsa de lona Joust [SKU: 24-MB01]).
1. Programar una nueva actualización:
   * Seleccionar **[!UICONTROL Save as a New Update]**
   * Nombre de la actualización: &quot;Update 1&quot;
   * Fecha de inicio: hora actual +1 min
   * Fecha de finalización: hora actual +1 hora
   * Modificar el nombre del producto a: &quot;Joust Duffle Bag 2&quot;
   * Guarde el producto.
1. Vaya a CLI y ejecute cron y espere hasta que se aplique la programación.

   ```
   bin/magento cron:run && bin/magento cron:run
   ```

1. De nuevo, ve a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y edita cualquier producto configurable (por ejemplo, Chaz Kangeroo Hoodie [SKU: MH01]).

   * Deshabilite todas las variantes. Vaya a la columna Acciones > **[!UICONTROL Select]** > **[!UICONTROL Disable Product]**.
   * Guarde el configurable.

<u>Resultados esperados</u>:

No se produce ningún error al guardar el producto.

<u>Resultados reales</u>:

Se produce el siguiente error:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
