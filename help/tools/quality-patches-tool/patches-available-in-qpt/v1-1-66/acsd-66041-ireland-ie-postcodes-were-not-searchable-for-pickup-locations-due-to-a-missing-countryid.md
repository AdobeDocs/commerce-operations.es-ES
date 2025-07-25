---
title: 'ACSD-66041: Los códigos postales de Irlanda (IE) no se pueden buscar en ubicaciones de recogida debido a la falta de CountryID'
description: Aplique el parche ACSD-66041 para corregir el problema de Adobe Commerce en el que los códigos postales de Irlanda (IE) no se podían buscar en ubicaciones de recogida debido a la falta de un CountryID.
feature: Shipping/Delivery, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: b1f69d00e0ad0caf15643d0c218e1a2c264d3ad4
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---


# ACSD-66041: no se pueden buscar ubicaciones de recogida en los códigos postales de Irlanda (IE) porque faltan `CountryID`

El parche ACSD-66041 corrige el problema en el que los códigos postales de Irlanda (IE) no se pueden buscar en ubicaciones de recogida debido a que falta `CountryID`. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. El ID del parche es ACSD-66041. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p5

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los códigos postales de Irlanda (IE) no se pueden buscar en ubicaciones de recogida debido a que falta `CountryID`.

<u>Pasos a seguir</u>:

1. Ejecute la siguiente consulta de GraphQL:

   ```graphql
   query getStoresTestError($term: String!, $radius: Int!) {
       pickupLocations(
           sort: { distance: ASC }
           area: { radius: $radius, search_term: $term }
       ) {
           items {
                   pickup_location_code
                   name
                   description
   		    latitude
   		    longitude
   		    country_id
   		    region
   		    city
   		    street
   		    postcode
   		    phone
           }
       }
   }
   ```

1. Utilice las siguientes variables:

   ```
   {
       "radius": 81,
       "term": "dublin:IE"
   }
   ```

<u>Resultados esperados</u>:

Los códigos postales de Irlanda están disponibles para buscar ubicaciones de recogida.

<u>Resultados reales</u>:

* Se devolvió un *error interno del servidor*.
* `var/log/exception.log` contiene el siguiente error:

  ```
  report.ERROR: Provided countryId does not exist.  {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Provided countryId does not exist.
  ```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
