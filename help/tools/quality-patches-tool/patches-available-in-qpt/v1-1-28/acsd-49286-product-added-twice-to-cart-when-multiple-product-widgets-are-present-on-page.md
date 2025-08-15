---
title: 'ACSD-49286: producto añadido dos veces al carro de compras cuando hay varios widgets de producto presentes.'
description: Aplique el parche ACSD-49286 para corregir el problema de Adobe Commerce por el que el producto se agrega dos veces al carro de compras cuando hay varios widgets de producto en la página.
feature: Admin Workspace, Orders, Products, Shopping Cart
role: Admin
exl-id: 03fdaafe-5566-4b75-a0eb-e0cba3dad3e7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49286: producto añadido dos veces al carro de compras cuando hay varios widgets de producto presentes.

El parche ACSD-49286 corrige el problema de que el producto se agrega dos veces al carro de compras cuando hay varios widgets de producto en la página. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.28. El ID del parche es ACSD-49286. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El producto se agrega dos veces a un carro de compras cuando hay varios widgets de producto en la página.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador y vaya a **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Page]** > **[!UICONTROL Home Page]**
1. En la sección de contenido, haga clic en **[!UICONTROL Edit]** con [!DNL Page Builder].
1. Agregar dos elementos de fila a **[!UICONTROL Content]**.
1. Agregue productos a ambos elementos de fila.
1. En la primera fila, establezca el aspecto del producto como [!UICONTROL Product Grid] y seleccione cualquier categoría que desee mostrar.
1. En la segunda fila, establezca el aspecto del producto como [!UICONTROL Product Carousel] y seleccione cualquier otra categoría que desee mostrar.
1. Vaya a la tienda **[!UICONTROL Home Page]** y agregue un producto desde la cuadrícula de productos.
1. Agregar otro producto de [!UICONTROL Product Carousel].

<u>Resultados esperados</u>:

La cantidad de productos no debe duplicarse después de agregar un producto al carro de compras de [!UICONTROL Product Grid].

<u>Resultados reales</u>:

La cantidad de productos se duplica después de agregar un producto al carro de compras desde [!UICONTROL Product Grid].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube. 

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
