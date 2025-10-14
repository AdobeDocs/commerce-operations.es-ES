---
title: 'ACSD-54418: cantidad de descuento fija añadida incorrectamente al producto secundario del paquete de precio dinámico'
description: Aplique el parche ACSD-54418 para corregir el problema de Adobe Commerce en el que la cantidad de descuento fija se aplica incorrectamente a cada producto secundario del paquete de precio dinámico.
feature: Shopping Cart
role: Admin, Developer
exl-id: f7b57361-9056-4eec-a393-dadb65aa595b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-54418: cantidad de descuento fija añadida incorrectamente al producto secundario del paquete de precio dinámico.

El parche ACSD-54418 corrige el problema en el que la cantidad de descuento fija se aplica incorrectamente a cada producto secundario del paquete de precio dinámico. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.42. El ID del parche es ACSD-54418. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El importe de descuento fijo se aplica incorrectamente a cada producto secundario del paquete de precios dinámicos.

<u>Pasos a seguir</u>:

1. Crear un **[!UICONTROL bundle product]** con precios dinámicos y opciones de paquete *2*.
1. Cree un(a) **[!UICONTROL cart price rule]** con un código de cupón específico que solo se aplique al producto agrupado **[!UICONTROL SKU]** y que tenga un descuento fijo.
1. Añadir el producto agrupado al carro de compras.
1. Aplicar **[!UICONTROL coupon code]**.
1. Compruebe el descuento aplicado al carro de compras.

<u>Resultados esperados</u>:

El descuento se aplica solo una vez a todo el producto agrupado.

<u>Resultados reales</u>:

El descuento se aplica a cada paquete de producto secundario.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
