---
title: 'ACSD-55238: Guardar la metadescripción vacía del producto'
description: Aplique el parche ACSD-55238 para corregir el problema de Adobe Commerce donde siempre se muestra en la metadescripción una descripción de producto que contiene código de HTML generado por  [!DNL Page Builder] u otro editor de HTML y no hay forma de establecerla en empty.
feature: Products, Page Builder, Page Content
role: Admin, Developer
exl-id: 39ccf1bb-a71a-47a0-b252-e6331e2df9b0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-55238: Guardar la metadescripción vacía del producto

El parche ACSD-55238 corrige el problema de que siempre se muestra en la metadescripción una descripción de producto que contiene código HTML generado por un editor de HTML. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42. El ID del parche es ACSD-55238. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

En la metadescripción siempre aparece una descripción de producto que contiene código HTML generado por [!DNL Page Builder] u otro editor de HTML, y no hay forma de establecerlo como vacío.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** y cree un nuevo bloque con cualquier contenido.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** y cree un nuevo producto. Establezca la metadescripción en empty.
1. Agregue el bloque creado anteriormente con *[!DNL Page Builder]* en la pestaña *[!UICONTROL Content]* y guarde el producto.
1. Abra el producto en la tienda y compruebe su elemento doc `meta name = "description"`.

<u>Resultados esperados</u>:

La metadescripción está vacía.

<u>Resultados reales</u>:

Cuando un producto tiene un bloque en su descripción, se utiliza para la metadescripción del producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
