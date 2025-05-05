---
title: "ACSD-48204: La regla de precios de catálogo creada en función del atributo *Sí/No* no tiene en cuenta el ámbito seleccionado"
description: Aplique el parche ACSD-48204 para corregir el problema de Adobe Commerce en el que la regla de precios de catálogo creada en función del atributo *Sí/No* no tiene en cuenta el ámbito seleccionado.
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# ACSD-48204: La regla de precios de catálogo creada en función del atributo *Yes/No* no tiene en cuenta el ámbito seleccionado

El parche ACSD-48204 corrige el problema en el que la regla de precios de catálogo creada en función del atributo *Yes/No* no tiene en cuenta el ámbito seleccionado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28. El ID del parche es ACSD-48204. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La regla de precios de catálogo creada basada en el atributo *Yes/No* no tiene en cuenta el ámbito seleccionado.

<u>Pasos a seguir</u>:

1. Crear dos sitios web (Predeterminado y W2).
1. Crear un atributo de producto de tipo *Sí/No*.
   * Conjunto [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Cree un producto configurable basado en cualquier atributo con dos variaciones (V1 y V2).
   * Agregue el atributo *Yes/No* al conjunto de atributos de variaciones configurables
   * Para una de las variaciones (V1), establezca el valor en *[!UICONTROL Yes]* en el sitio web no predeterminado (W2)
1. Crear una regla de catálogo:
   * Se aplica a ambos sitios web
   * Condición: *Sí/No* valor de atributo es *[!UICONTROL Yes]*
   * Descuento = 50 %
1. Abra el producto configurable en el sitio web no predeterminado (W2).
1. Compruebe que la variación V1 tenga el descuento del 50 % aplicado.
1. Abra la variación V1 en el Administrador de Adobe Commerce.
   * Cambiar al sitio web predeterminado
   * No realice cambios y guarde el producto
1. Actualice la página de tienda de productos configurable.

<u>Resultados esperados</u>:

La variación V1 sigue teniendo el descuento del 50 % aplicado, ya que no se han realizado cambios.

<u>Resultados reales</u>:

El descuento desaparece.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
