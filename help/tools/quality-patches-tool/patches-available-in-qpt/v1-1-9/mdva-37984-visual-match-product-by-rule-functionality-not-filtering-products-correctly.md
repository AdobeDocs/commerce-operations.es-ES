---
title: 'MDVA-37984: Visual Merchandiser no funciona correctamente cuando se aplican actualizaciones de ensayo'
description: El parche MDVA-37984 resuelve el problema en el que la funcionalidad "Coincidir producto por regla" de Visual Merchandiser no filtra los productos correctamente cuando se aplican actualizaciones de ensayo. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9. El ID del parche es MDVA-37984. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Categories, Merchandising, Products, Staging
role: Admin
exl-id: 3aeb74a4-b6f7-453a-a8f6-45a345aaa74f
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# MDVA-37984: Visual Merchandiser no funciona correctamente cuando se aplican actualizaciones de ensayo

El parche MDVA-37984 resuelve el problema en el que la funcionalidad &quot;Coincidir producto por regla&quot; de Visual Merchandiser no filtra los productos correctamente cuando se aplican actualizaciones de ensayo. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9. El ID del parche es MDVA-37984. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La funcionalidad &quot;Hacer coincidir producto por regla&quot; de Visual Merchandiser no filtra los productos correctamente cuando se aplican las actualizaciones de ensayo.

<u>Pasos a seguir</u>:

1. Cree una actualización de programación para cualquier producto existente.
   * Establecer valores diferentes para `entity_id` y `row_id`.
1. Cree un nuevo producto configurable y, a continuación, un producto simple (por lo que el nuevo producto `entity_id` y `row_ids` también son diferentes).
   * Para facilitar la réplica del problema, establezca un valor de cantidad distinguible para el producto simple; por ejemplo, 5000.
1. Vaya a una categoría > **Productos de la categoría** y habilite **Hacer coincidir productos por regla**.
1. Ahora seleccione &quot;Cantidad&quot; como atributo, &quot;Mayor&quot; como operador y &quot;4500&quot; como valor.
1. Haga clic en **guardar**.

<u>Resultados esperados</u>:

Se muestra el producto configurable recién creado.

<u>Resultados reales</u>:

No aparece el producto configurable recién creado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
