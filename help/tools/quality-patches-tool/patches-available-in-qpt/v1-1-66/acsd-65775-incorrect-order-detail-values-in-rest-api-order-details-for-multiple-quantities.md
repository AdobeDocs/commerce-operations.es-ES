---
title: 'ACSD-65775: valores "base_row_total" y "row_total" incorrectos en los detalles de pedido de la API de REST para varias cantidades'
description: Aplique el parche ACSD-65775 para corregir el problema de Adobe Commerce en el que los detalles del pedido de la API de REST devuelven valores "base_row_total" y "row_total" incorrectos cuando se piden varias cantidades del mismo artículo.
feature: REST
role: Admin, Developer
type: Troubleshooting
source-git-commit: 23c78abaf28f64baf0e91bcaf89bd0e34b5bf78a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# ACSD-65775: valores `base_row_total` y `row_total` incorrectos en los detalles de pedido de la API REST para varias cantidades

El parche ACSD-65775 corrige el problema en el que los detalles del pedido de la API REST devuelven valores `base_row_total` y `row_total` incorrectos cuando se solicitan varias cantidades del mismo artículo. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. El ID del parche es ACSD-65775. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

`base_row_total` y `row_total` en la respuesta de API de REST de detalles del pedido muestran el precio unitario en lugar del precio total cuando se solicitan varias cantidades del mismo artículo.

<u>Pasos a seguir</u>:

1. Cree dos productos simples: simple1 con un precio de 10 $ y simple2 con un precio de 15 $.
1. Cree una nueva cuenta de cliente.
1. Agregue simple1 al carro de compras con la cantidad 2 y simple2 con la cantidad 3.
1. Realice el pedido utilizando la cuenta de cliente.
1. Obtenga un token de administrador enviando una solicitud de POST a `/rest/V1/integration/admin/token` con la siguiente carga útil:

   ```
   {
     "username": "admin",
     "password": "password"
   }
   ```

1. Recupere los detalles del pedido mediante una petición GET a `/rest/default/V1/orders/1`.

<u>Resultados esperados</u>:

`base_row_total` y `row_total` deben reflejar el precio total calculado como cantidad multiplicada por el precio del artículo (por ejemplo, 2 × 10 $ = 20 $ para simple1).

<u>Resultados reales</u>:

`base_row_total` y `row_total` solo devuelven el precio unitario (por ejemplo, 10 $ para simple1 en lugar de 20 $).

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
