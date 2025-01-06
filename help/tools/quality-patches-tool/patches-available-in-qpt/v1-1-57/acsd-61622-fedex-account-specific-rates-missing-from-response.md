---
title: 'ACSD-61622: faltan  [!DNL FedEx] tasas específicas de cuenta en la respuesta de API de REST'
description: Aplique el parche ACSD-61622 para corregir el problema de Adobe Commerce donde faltan  [!DNL FedEx] tasas específicas de la cuenta en la respuesta de la API de REST.
feature: Shipping/Delivery
role: Admin, Developer
source-git-commit: 24acc5f369e0001c8aeab3f81a2e1b51bc523333
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-61622: faltan [!DNL FedEx] tasas específicas de la cuenta en la respuesta de la API de REST

El parche ACSD-61622 resuelve el problema en el que faltan [!DNL FedEx's] tasas específicas de la cuenta en la respuesta de la API de REST. Agrega el tipo de solicitud de tasa `ACCOUNT` a la solicitud de API de REST enviada desde Adobe Commerce SOAP a [!DNL FedEx], lo que devuelve una respuesta similar a la respuesta de API de la. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. El ID del parche es ACSD-61622. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Faltan tasas específicas de la cuenta [!DNL FedEx's] en la respuesta de la API de REST.

<u>Pasos a seguir</u>:

1. Instale una instancia de Adobe Commerce limpia.
1. Crea un producto sencillo con un peso de 5 libras.
1. Configure [!DNL FedEx] para la API de REST.
1. Habilite el método de envío [!DNL FedEx] y borre la caché.
1. Iniciar la observación del archivo de registro: `var/log/shipping.log`
1. Añade un producto simple al carro de compras y ve a la página de envío al finalizar la compra. Ejemplo de datos de clientes:

   * Código postal: 58601
   * Nombres: John Doe
   * Dirección: 196 Eulalia Burg
   * País: EE. UU.
   * Estado: Dakota del Norte
   * Número de teléfono: 187-563-3627

<u>Resultados esperados</u>:

SOAP Las tasas de `PAYOR_ACCOUNT_PACKAGE` están disponibles en la respuesta de la API de REST, de forma similar a las respuestas de la API de.

<u>Resultados reales</u>:

Solo están disponibles las tasas de `PAYOR_LIST_PACKAGE` en la respuesta, lo que significa que no hay tasas (de cuenta) negociadas de [!DNL FedEx].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
