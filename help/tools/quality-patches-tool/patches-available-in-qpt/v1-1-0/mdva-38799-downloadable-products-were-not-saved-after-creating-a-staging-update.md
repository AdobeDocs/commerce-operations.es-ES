---
title: 'MDVA-38799: Los productos descargables no se guardan después de crear una actualización de ensayo'
description: El parche MDVA-38799 resuelve el problema de que los productos descargables no se guardan después de crear una actualización de ensayo. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0. El ID del parche es MDVA-38799. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.
feature: Products, Staging
role: Admin
exl-id: 0ae665a8-cda2-4340-91e7-5b9b969a6607
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---

# MDVA-38799: Los productos descargables no se guardan después de crear una actualización de ensayo

El parche MDVA-38799 resuelve el problema de que los productos descargables no se guardan después de crear una actualización de ensayo. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0. El ID del parche es MDVA-38799. Tenga en cuenta que el problema se corrigió en la versión 2.4.3 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce en la infraestructura en la nube 2.4.1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0-2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos descargables no se guardan después de crear una actualización de ensayo. Los usuarios reciben el mensaje de error: *La muestra descargable no está relacionada con el producto. Compruebe el vínculo e inténtelo de nuevo*.

<u>Pasos a seguir</u>:

1. Vaya a **Catálogo** > **Productos**.
1. Haga clic en el menú desplegable situado junto a Añadir producto y seleccione Producto descargable.
   * Rellene el nombre, SKU, precio y cantidad del producto.
1. Desplácese hacia abajo hasta la página Información descargable.
1. En Ejemplos, haga clic en **Agregar vínculo**.
   * Rellene el Título, Cargar archivo (el tipo de archivo no importa).
1. Haga clic en **Guardar**. Recibirá el siguiente mensaje: *Ha guardado el producto*.
1. Haga clic en **Programar nueva actualización** en la parte superior de la página.
   * Complete el Nombre de la actualización y una Fecha de inicio y una Fecha de finalización legales.
1. Haga clic en **Guardar** en la actualización de ensayo.
1. Haz clic en **Guardar** en el producto.

<u>Resultados esperados</u>:

El producto se guarda sin ningún error.

<u>Resultados reales</u>:

Recibe el mensaje de error: *La muestra descargable no está relacionada con el producto. Compruebe el vínculo e inténtelo de nuevo*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
