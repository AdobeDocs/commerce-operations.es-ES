---
title: 'ACSD-47875: no se puede agregar un producto al carro para el ámbito de vista de tienda con la administración de inventario'
description: Aplique el parche ACSD-47875 para corregir el problema de Adobe Commerce en el que un producto no se puede agregar a un carro de compras de clientes desde el administrador para un ámbito de vista de tienda determinado con administración de inventario.
feature: Inventory, Shopping Cart, Products
role: Admin, Developer
exl-id: 10862e09-d561-4ed5-ab6f-cf002fae6850
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# ACSD-47875: no se puede agregar un producto al carro para el ámbito de vista de tienda con la administración de inventario

El parche ACSD-47875 corrige el problema en el que un producto no se puede agregar al carro de compras de un cliente desde el administrador para un ámbito de vista de tienda en particular con administración de inventario. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.36. El ID del parche es ACSD-47875. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios administradores no pueden agregar un producto al carro de compras de un cliente mediante la característica **[!UICONTROL Manage Shopping Cart]** en el Administrador para un ámbito de vista de tienda determinado con MSI instalado.

<u>Requisitos previos</u>:

Los módulos [!DNL Adobe Commerce Inventory Management (MSI)] están instalados y habilitados.

<u>Pasos a seguir</u>:

1. Crear un sitio web, una tienda y una vista de tienda.
1. Crear un origen adicional que no sea *Predeterminado*.
1. Cree un nuevo inventario de stock y asígnelo al nuevo sitio web y al nuevo origen.
1. Cree un nuevo cliente para el nuevo sitio web.
1. Asignar un producto solo al nuevo sitio web; anular la asignación del sitio web predeterminado.

   * Asigne el nuevo origen y establezca la cantidad *por encima de 0* para el nuevo origen y *0* para el origen predeterminado.

1. Vaya a la página **[!UICONTROL Customer Edit]** en el Administrador. Haga clic en **[!UICONTROL Manage Shopping Cart]**.
1. Cambie el ámbito de la vista de tienda a la nueva vista de tienda.
1. Vaya a la sección **[!UICONTROL Products]** y busque el producto.
1. Seleccione el producto y haga clic en **[!UICONTROL Add selections to my cart]**.

<u>Resultados esperados</u>:

El producto se agrega al carro de compras.

<u>Resultados reales</u>:

* Se genera el siguiente error: *El producto que intenta agregar no está disponible.*
* El producto no se agrega al carro de compras.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
