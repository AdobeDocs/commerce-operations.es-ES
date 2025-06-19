---
title: 'MDVA-38728: Cambiar la visibilidad del producto crea una reescritura de URL para el sitio web principal'
description: El parche MDVA-38728 resuelve el problema de que, al cambiar la visibilidad del producto del segundo sitio web, se crea una reescritura de URL para el sitio web principal. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. El ID del parche es MDVA-38728. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Products
role: Admin
exl-id: c9dfa386-6327-43b6-a977-a29178c64b89
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-38728: Cambiar la visibilidad del producto crea una reescritura de URL para el sitio web principal

El parche MDVA-38728 resuelve el problema de que, al cambiar la visibilidad del producto del segundo sitio web, se crea una reescritura de URL para el sitio web principal. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. El ID del parche es MDVA-38728. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al cambiar la visibilidad del producto del segundo sitio web, se crea una reescritura de URL para el sitio web principal.

<u>Pasos a seguir</u>:

1. Cree un sitio web, una tienda y una vista de tienda adicionales.
1. Cree un producto sencillo.
1. Establezca la visibilidad en **No visible individualmente**.
1. Asigne el producto únicamente al segundo sitio web.
1. Rellene todos los demás campos obligatorios.
1. Guarde el producto.
1. Iniciar colas MySQL:

   ```mysql
   bin/magento queue:consumers:start product_action_attribute.update &
   bin/magento queue:consumers:start product_action_attribute.website.update &
   ```

1. Ir a la lista de productos.
1. Seleccione el producto creado y actualice el atributo de visibilidad mediante la actualización masiva a Catálogo y Buscar.
1. Compruebe la reescritura de la URL.

<u>Resultados esperados</u>:

La reescritura se crea para el segundo sitio web en el que se asigna el producto.

<u>Resultados reales</u>:

La reescritura se crea para el sitio web principal.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
