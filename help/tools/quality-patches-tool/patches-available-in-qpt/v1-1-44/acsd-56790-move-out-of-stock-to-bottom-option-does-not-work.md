---
title: 'ACSD-56790: **[!UICONTROL move out of stock to bottom]** opción no funciona al ordenar productos en  [!DNL Visual Merchandiser]'
description: Aplique el parche ACSD-56790 para corregir el problema de Adobe Commerce en el que la opción Mover fuera de stock a la parte inferior no funciona al ordenar productos en Visual Merchandiser.
feature: Products, Categories
role: Admin, Developer
exl-id: a5e5f208-793d-45a5-a000-f8ff1c31d049
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-56790: la opción **[!UICONTROL move out of stock to bottom]** no funciona al ordenar productos en [!DNL Visual Merchandiser]

La revisión ACSD-56790 corrige el problema en el que la opción de mover de existencias a la parte inferior no funciona al ordenar productos en [!DNL Visual Merchandiser]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44. El ID del parche es ACSD-56790. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La opción **[!UICONTROL move out of stock to bottom]** no funciona al ordenar productos en [!DNL Visual Merchandiser]

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** y cree los atributos siguientes.
1. Crear un nuevo sitio web: **No principal**.
1. Crear una **tienda que no sea principal** en este nuevo sitio web.
1. Cree dos tiendas:

   * Primero en **Almacén del sitio web principal**.
   * Segundo en **Almacén no principal**.

1. Cree dos fuentes:
   * Cartas.
   * Números.

1. Cree dos existencias:
   * Primer Principal - Canales de ventas: Sitio web principal - Fuentes asignadas: Cartas.
   * Segundo no principal - canales de ventas: no principal - orígenes asignados: números.

1. Cree tres productos simples en ambos sitios web, todos en la categoría predeterminada, todos asignados a ambos orígenes:

   * ProductA: cantidad *10* en letras, cantidad *0* en números.
   * Product1 - Cantidad *0* en letras, Cantidad *10* en números.
   * ProductA1 - Cantidad *10* en letras, Cantidad *10* en números.

1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** y seleccione **[!UICONTROL Default category]**.
1. Cambie el ámbito a **Primero**.
1. Expanda la sección Productos en la categoría.
1. Elija el orden como: **[!UICONTROL move out of stock to bottom]**

<u>Resultados esperados</u>:

La lista de productos con **productos sin existencias** se ha movido a la parte inferior.

<u>Resultados reales</u>:

Los productos no se pueden cargar. Una página redirige al tablero de administración con el mensaje de error: `Invalid security or form key. Please refresh the page`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
