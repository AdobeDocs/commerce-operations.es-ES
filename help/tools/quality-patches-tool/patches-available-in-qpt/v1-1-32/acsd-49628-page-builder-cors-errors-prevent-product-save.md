---
title: 'ACSD-49628:  [!DNL Page Builder] Los errores de CORS impiden el guardado del producto'
description: Aplique el parche ACSD-49628 para corregir el problema de Adobe Commerce donde los errores  [!DNL Page Builder] CORS impiden el guardado del producto.
feature: Categories, Page Builder, Products
role: Admin
exl-id: 5bceddfa-5fbf-4ebe-a233-de7720764849
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-49628: [!DNL Page Builder] errores CORS impiden el guardado del producto

La revisión ACSD-49628 corrige el problema en el cual [!DNL Page Builder] errores CORS impiden que un administrador guarde un producto. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.32. El ID del parche es ACSD-49628. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!DNL Page Builder] errores CORS impiden guardar un producto.

<u>Pasos a seguir</u>:

1. Inicie sesión como administrador.
1. Cree una función de usuario con los siguientes permisos:

   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Products]**.
   * **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Categories]**.

1. No agregue ningún permiso de *[!UICONTROL Content]*.
1. Cree otro usuario administrador y asigne las funciones creadas anteriormente a este usuario.
1. Cree un producto y cierre la sesión.
1. Inicie sesión como segundo administrador.
1. Intente editar y guardar el producto.

<u>Resultados esperados</u>:

El segundo administrador puede guardar el producto, pero el botón **[!UICONTROL Edit with Page Builder]** no se muestra al administrador sin los permisos de *[!UICONTROL Content]*.

<u>Resultados reales</u>:

El segundo administrador no pudo guardar el producto debido a varios errores de [!DNL Page Builder].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
