---
title: 'ACSD-56447: Añadir el mismo producto al carro de compras mediante la API de REST web paralela resulta en dos elementos independientes en el carro de compras'
description: Aplique el parche ACSD-56447 para corregir el problema de Adobe Commerce, donde al agregar el mismo producto al carro de compras a través de solicitudes de API de REST web paralelas, se generan dos elementos independientes en el carro de compras.
feature: Shopping Cart, REST
role: Admin, Developer
exl-id: ef0b2ce7-74f5-47b6-a44c-bda898c444b2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-56447: Añadir el mismo producto al carro de compras mediante la API de REST web paralela resulta en dos elementos independientes en el carro de compras

El parche ACSD-56447 corrige el problema de que, al agregar el mismo producto al carro de compras mediante solicitudes de API de REST web paralelas, se generan dos elementos independientes en el carro de compras. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45. El ID del parche es ACSD-56447. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Añadir el mismo producto al carro de compras mediante solicitudes de API de REST web paralelas resulta en dos elementos independientes en el carro de compras.

<u>Pasos a seguir</u>:

1. Genere un token de cliente para realizar la solicitud de llamadas a la API de REST usando [!DNL Postman].
1. Cree un carro de compras para el cliente.
1. Utilice el token generado anteriormente para crear un carro de compras vacío para el cliente.
1. Use CURL para hacer dos solicitudes `AddProductsToCart` que se ejecuten en paralelo. Siga las instrucciones del [tutorial de procesamiento de pedidos](https://developer.adobe.com/commerce/webapi/rest/tutorials/orders/) de la documentación para desarrolladores.

<u>Resultados esperados</u>:

Los artículos con varias cantidades se muestran en una línea.

<u>Resultados reales</u>:

Los mismos SKU se muestran en elementos de varias líneas.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
