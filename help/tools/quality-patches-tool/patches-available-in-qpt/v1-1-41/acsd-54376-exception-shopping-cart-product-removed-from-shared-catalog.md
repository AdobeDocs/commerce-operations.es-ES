---
title: 'ACSD-54376: excepción en el carro de compras al eliminar el producto de [!UICONTROL shared catalog]'
description: Aplique el parche ACSD-54376 para corregir el problema de Adobe Commerce en el que se produce una excepción en el carro de compras cuando se elimina un producto de [!UICONTROL shared catalog] después de agregarlo al carro de compras.
feature: Shopping Cart, B2B
role: Admin, Developer
exl-id: 59047ccb-d434-46cd-8d2f-ceb0c85a785a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-54376: excepción en el carro de compras al eliminar el producto de [!UICONTROL shared catalog]

El parche ACSD-54376 corrige el problema en el que se produce una excepción en el carro de compras cuando se elimina un producto de [!UICONTROL shared catalog] después de agregarlo al carro de compras. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.41. El ID del parche es ACSD-54376. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce una excepción en el carro de compras cuando se quita un producto de [!UICONTROL shared catalog] después de agregarlo al carro de compras.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce con B2B.
1. Habilitar [!UICONTROL shared catalog].
1. Crear un producto y asignarlo al predeterminado [!UICONTROL shared catalog].
1. Agregar un producto al carro de compras desde la tienda.
1. Quitar el producto de [!UICONTROL shared catalog].
1. Vaya a la página de cierre de compra mediante la lista desplegable de minicarro.

<u>Resultados esperados</u>:

Las excepciones se gestionan y no se muestran al usuario.

<u>Resultados reales</u>:

Se muestra una excepción no controlada en la página de cierre de compra.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
