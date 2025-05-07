---
title: 'ACSD-64523: el extremo REST no puede validar los campos obligatorios'
description: Aplique el parche ACSD-64523 para corregir el problema en el que el extremo REST "[V1/import/csv]" no valida los campos obligatorios, lo que permite la creación de productos sin proporcionar los campos obligatorios requeridos.
feature: REST, Products, Admin Workspace
role: Admin, Developer
source-git-commit: 4bf9a5eb2e423f5981ee9234be57230a6dff3913
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---


# ACSD-64523: el extremo REST no puede validar los campos obligatorios

El parche ACSD-64523 corrige un problema en el que el extremo REST [V1/import/csv] no valida los campos obligatorios, lo que permite la creación de productos sin los datos necesarios. Para resolver esto, actualice el encabezado Autorización. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El extremo REST `[V1/import/csv]` no puede validar los campos obligatorios, lo que permite la creación de productos sin proporcionar estos campos obligatorios.

<u>Pasos a seguir</u>:

1. Ejecute la siguiente carga útil (actualice el encabezado Autorización):

   ```
   curl --location 'http://<domain>/rest/default/V1/import/json' \
   --header 'Content-Type: application/json' \
   --header 'Authorization: Bearer xxxxx' \
   --data '{
       "source": {
           "locale": "en_AU",
           "entity": "catalog_product",
           "behavior": "append",
           "validation_strategy": "validation-stop-on-errors",
           "allowed_error_count": 0,
           "items": [
               {
                   "sku": "product_sku",
                   "product_online": "no",
                   "attribute_set_code": "Default",
                   "product_type": "configurable",
                   "product_websites": "base",
                   "store_view_code": "default",
                   "name": null,
                   "description": null,
                   "short_description": null,
                   "weight": null,
                   "tax_class_name": null,
                   "visibility": null,
                   "price": null,
                   "url_key": null,
                   "cost": null,
                   "additional_attributes": {
                       "special_price": "",
                       "retail_price": ""
                   },
                   "configurable_variations": []
               }
           ]
       }
   }'
   ```

<u>Resultados esperados</u>:

La aplicación debe evitar guardar un producto sin campos obligatorios.

<u>Resultados reales</u>:

El producto se ha guardado correctamente sin especificar el nombre del producto, que es un atributo obligatorio. Como resultado, no podemos acceder a la cuadrícula de productos del back-end y arroja el siguiente error.

`Warning: Undefined array key "name" in /app/code/Magento/Catalog/Ui/Component/Listing/Columns/Thumbnail.php on line 91`

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
