---
title: 'ACSD-63329: los atributos de fecha y hora no se establecen al crear productos con la API de REST'
description: Aplique el parche ACSD-63329 para corregir el problema de Adobe Commerce en el que los valores predeterminados no están establecidos para los campos de fecha y hora al crear productos con la API de REST.
feature: REST
Role: Admin, Developers
exl-id: d8e7917b-07a5-465b-944b-fd6168dea63c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63329: los valores predeterminados de los campos de fecha y hora no se establecen al crear productos con la API de REST

La revisión ACSD-63329 corrige el problema por el que no se establecían valores predeterminados para los campos de fecha y hora al crear un nuevo producto mediante la API de REST: `/rest/default/V1/products`. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. El ID del parche es ACSD-63329. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se han establecido valores predeterminados para los campos de fecha y hora al crear productos con la API de REST: `/rest/default/V1/products`

<u>Pasos a seguir</u>:

1. Cree un atributo **[!UICONTROL Product]**, establezca su valor predeterminado en `12/31/2020` y establezca **[!UICONTROL Catalog Input Type for Store Owner]** en ***[!UICONTROL Date]*** o ***[!UICONTROL Date and Time]***.
1. Cree otro atributo de tipo text y establezca el valor predeterminado en ***test value***.
1. Cree un nuevo producto mediante una solicitud POST de API de REST a `/rest/all/V1/products/`.

   ```
       {
           "product": {
               "sku": "testsku2",
               "name": "Test Api Product 2",
               "attribute_set_id": 4,
               "price": 100,
               "status": 1,
               "visibility": 4,
               "type_id": "simple",
               "weight": 20,
               "extension_attributes": {
                   "website_ids": [
                       1
                   ]
               }
           }
       }
   ```

1. Compruebe los valores guardados para los atributos mencionados anteriormente.

<u>Resultados esperados</u>:

El valor predeterminado debe guardarse en atributos de tipo **[!UICONTROL Date/Datetime]** al crear un producto mediante la API.

<u>Resultados reales</u>:

El valor predeterminado se guarda para el atributo **[!UICONTROL Text]**, pero no para el atributo **[!UICONTROL Date type]**. El valor del atributo **[!UICONTROL Date]** está vacío.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
