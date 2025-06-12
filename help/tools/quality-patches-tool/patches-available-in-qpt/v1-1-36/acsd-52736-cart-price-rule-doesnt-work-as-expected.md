---
title: 'ACSD-52736: [!UICONTROL Cart Price Rule] no funciona como se esperaba'
description: Aplique el parche ACSD-52736 para solucionar el problema de Adobe Commerce donde un [!UICONTROL Cart Price Rule] que incluye los requisitos para la cantidad de productos configurables no funciona como se esperaba.
feature: Shopping Cart, Products
role: Admin, Developer
exl-id: 80c3b14e-62ce-4cfc-b1ff-968e70e3a6f8
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-52736: [!UICONTROL Cart Price Rule] no funciona como se esperaba

El parche ACSD-52736 corrige el problema en el que un [!UICONTROL Cart Price Rule] que incluye los requisitos para la cantidad de productos configurables no funciona como se esperaba. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.36. El ID del parche es ACSD-52736. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un(a) [!UICONTROL Cart Price Rule] que incluye los requisitos para la cantidad de productos configurables no funciona como se esperaba.

<u>Pasos a seguir</u>:

1. Crear una regla de carro de compras:
   * [!UICONTROL Apply] = Porcentaje de descuento en el precio del producto
   * [!UICONTROL Discount Amount] = 60
   * [!UICONTROL Maximum Qty Discount is Applied to] = 1
   * [!UICONTROL Discount Qty Step (Buy X)] = 1
   * Aplicar la regla solo a los artículos del carro que cumplan las siguientes condiciones: La cantidad del carro es 1
2. Agregar un producto con [!UICONTROL Qty] = 2 al carro de compras.
3. Comprobar precios del carro de compras.

<u>Resultados esperados</u>:

La regla no se aplica porque la cantidad de productos en el carro es *2*.

<u>Resultados reales</u>:

Se aplica el descuento.

<u> Pasos adicionales necesarios después de la instalación del parche</u>:

Después de aplicar el parche, las condiciones de la regla de carro de compras que utilizan el atributo *Quantity* deben eliminarse y agregarse de nuevo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
