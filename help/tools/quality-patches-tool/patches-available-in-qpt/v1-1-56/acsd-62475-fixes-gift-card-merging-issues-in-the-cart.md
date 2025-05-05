---
title: 'ACSD-62475: corrige los problemas de combinación de tarjetas de regalo en el carro de compras'
description: Aplique el parche ACSD-62475 para solucionar el problema de Adobe Commerce, donde los productos de tarjetas de regalo con diferentes detalles se combinan incorrectamente en un solo elemento de línea del carro de compras.
feature: Shopping Cart, Quotes
role: Admin, Developer
source-git-commit: 7c35c245d6a464f7758053bd8aa1854c8fe8a5f2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62475: corrige los problemas de combinación de tarjetas de regalo en el carro de compras

El parche ACSD-62475 corrige el problema en el que los productos de tarjetas de regalo con diferentes detalles se combinan incorrectamente en un solo elemento de línea en el carro de compras. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. El ID del parche es ACSD-62475. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los productos de tarjeta de regalo agregados al carro de compras con detalles únicos de remitente o destinatario se combinan incorrectamente en un solo elemento de línea, lo que resulta en incoherencias en los datos.

<u>Pasos a seguir</u>:

1. Crear un producto [!UICONTROL Gift Card] con la siguiente configuración:
   * **[!UICONTROL Card Type]**: [!UICONTROL Virtual]
   * **[!UICONTROL Amount]**: 10

1. En la tienda, cree un nuevo usuario e inicie sesión.

1. Añada el producto Tarjeta de regalo al carro de compras con los siguientes detalles:
   * **[!UICONTROL Sender Name]**: Remitente 1
   * **[!UICONTROL Sender Email**]: sender1@test.com
   * **[!UICONTROL Recipient Name**]: Destinatario 1
   * **[!UICONTROL Recipient Email**]: recipient1@test.com


1. Cerrar sesión

1. Añada el mismo producto Tarjeta de regalo al carro de compras con los siguientes detalles:
   * **[!UICONTROL Sender Name]**: Remitente 2
   * **[!UICONTROL Sender Email**]: sender2@test.com
   * **[!UICONTROL Recipient Name**]: Destinatario 2
   * **[!UICONTROL Recipient Email**]: recipient2@test.com

1. Vuelva a iniciar sesión y compruebe el carro de compras.

<u>Resultados esperados</u>:

Ambas tarjetas de regalo deben aparecer como dos elementos de línea independientes con sus respectivos detalles.

<u>Resultados reales</u>:

Las Tarjetas de regalo se combinan en un artículo de línea con una cantidad de 2, conservando los detalles de la primera Tarjeta de regalo.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
