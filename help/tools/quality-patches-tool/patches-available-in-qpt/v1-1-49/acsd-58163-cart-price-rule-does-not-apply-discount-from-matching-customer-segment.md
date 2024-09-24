---
title: "ACSD-58163: [!UICONTROL Cart Price Rule] no aplica descuento del carro de compras [!UICONTROL Customer Segment] coincidente sin código de cupón"
description: Aplique el parche ACSD-58163 para corregir el problema de Adobe Commerce en el cual [!UICONTROL Cart Price Rule] no aplica un descuento a un invitado del carro de compras [!UICONTROL Customer Segment] coincidente sin un código de cupón.
feature: Products
role: Admin, Developer
source-git-commit: 52742cbc2098958f8e4cddf8534e0c2bf79d5c3e
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# ACSD-58163: [!UICONTROL Cart Price Rule] no aplica descuento del carro de compras [!UICONTROL Customer Segment] coincidente sin código de cupón

El parche ACSD-58163 corrige el problema en el cual [!UICONTROL Cart Price Rule] no aplica un descuento del carro de compras [!UICONTROL Customer Segment] coincidente sin un código de cupón. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49. El ID del parche es ACSD-58163. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

[!UICONTROL Cart Price Rule] no aplica ningún descuento a un invitado del carro de compras [!UICONTROL Customer Segment] que corresponda sin un código de cupón.

<u>Pasos a seguir</u>:

1. Crear segmento de cliente:
   * Para visitantes.
   * Con la condición de tener un producto en el carro de compras.

1. Crear un *[!UICONTROL Cart Price Rule]*:
   * Sin código de cupón.
   * Con la condición para que coincida con el segmento del cliente visitante.

1. Cree un producto sencillo.
1. Abre la tienda como invitado.
1. Añadir un producto simple al carro de compras.
1. Vaya al carro de compras.

<u>Resultados esperados</u>:

Se ha aplicado un descuento de *[!UICONTROL Cart Price Rule]*.

<u>Resultados reales</u>:

*[!UICONTROL Cart Price Rule]* descuento no aplicado.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
