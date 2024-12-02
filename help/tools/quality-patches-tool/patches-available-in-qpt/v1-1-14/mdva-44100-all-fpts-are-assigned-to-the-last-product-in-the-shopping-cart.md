---
title: 'MDVA-44100: todos los FTP se asignan al último producto del carro de compras'
description: El parche MDVA-44100 resuelve el problema de asignación de todos los FTP al último producto del carro de compras. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14. El ID del parche es MDVA-44100. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: b370dcbb-cbe9-4f5d-9b8f-1722ab521fcb
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-44100: todos los FTP se asignan al último producto del carro de compras

El parche MDVA-44100 resuelve el problema de asignación de todos los FTP al último producto del carro de compras. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14. El ID del parche es MDVA-44100. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Todos los FTP se asignan al último producto del carro de compras y se restablecen los valores FTP del resto de los productos.

<u>Pasos a seguir</u>:

1. Vaya a **Tiendas** > **Configuración** > **Ventas** > **Impuestos** y establezca:
   * Activar FTP = Sí
   * Aplicar Impuesto a FTP = Sí
   * Incluir FTP en el subtotal = Sí
1. Vaya a **Tiendas** > **Atributo** > **Producto** y cree un nuevo atributo con el tipo = Impuesto sobre productos fijos.
1. Agregue el atributo a un conjunto de atributos.
1. Cree dos productos a partir del conjunto de atributos y configure el atributo FTP para su país y estado.
1. Añada ambos elementos al pedido.
1. Escriba una dirección que requiera que se pague el FTP.
1. Realice el pedido.
1. Compruebe la lista de artículos en el pedido.

<u>Resultados esperados</u>:

Los FTP se muestran debajo de cada producto.

<u>Resultados reales</u>:

Los valores de FTP de ambos elementos se muestran debajo del segundo elemento.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
