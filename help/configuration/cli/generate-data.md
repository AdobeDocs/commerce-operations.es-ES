---
title: Generar datos para pruebas de rendimiento
description: Obtenga información sobre cómo generar una gran cantidad de datos para utilizarlos en pruebas de rendimiento.
exl-id: 2f54701d-88c4-464a-b4dc-56db14d54160
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '749'
ht-degree: 8%

---

# Datos de pruebas de rendimiento

Para usar la variable [Performance Toolkit](https://github.com/magento/magento2/blob/2.4/setup/performance-toolkit) Para utilizar otra herramienta para probar el rendimiento, debe generar una gran cantidad de datos, como tiendas, categorías y productos.

{{file-system-owner}}

## Perfiles

Puede ajustar la cantidad de datos que crea mediante _perfiles_ (pequeño, medio, grande y extra grande). Los perfiles se encuentran en `<magento_root>/setup/performance-toolkit/profiles/<ce|ee>` directorio.

Por ejemplo, `/var/www/html/magento2/setup/performance-toolkit/profiles/ce`

La siguiente figura muestra cómo se muestra un producto en la tienda utilizando _pequeño_ perfil:

![Tienda de muestra con datos generados](../../assets/configuration/generate-data.png)

La siguiente tabla proporciona detalles sobre los perfiles del generador de datos: pequeño, mediano, grande y extra grande.

| Parámetro | Perfil pequeño | Perfil medio | Perfil medio de varios sitios | Perfil grande | Perfil extra grande |
| --- | --- | --- | --- | --- | --- |
| `websites` | 1 | 3 | 25 | 5 | 5 |
| `store_groups` | 1 | 3 | 25 | 5 | 5 |
| `store_views` | 1 | 3 | 50 | 5 | 5 |
| `simple_products` | 800 | 24,000 | 4,000 | 300,000 | 600,000 |
| `configurable_products` | 16 con 24 opciones | 640 con 24 opciones | 800 con 24 opciones y 79 con 200 opciones | 8.000 con 24 opciones | 16.000 con 24 opciones |
| `product_images` | 100 imágenes / 3 imágenes por producto | 1000 imágenes / 3 imágenes por producto | 1000 imágenes / 3 imágenes por producto | 2000 imágenes / 3 imágenes por producto | 2000 imágenes / 3 imágenes por producto |
| `categories` | 30 | 300 | 100 | 3,000 | 6,000 |
| `categories_nesting_level` | 3 | 3 | 3 | 5 | 5 |
| `catalog_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `catalog_target_rules` | 5 | 5 | 5 | 5 | 5 |
| `cart_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `cart_price_rules_floor` | 2 | 2 | 2 | 2 | 2 |
| `customers` | 200 | 2,000 | 2,000 | 5,000 | 10,000 |
| `tax rates` | 130 | 40,000 | 40,000 | 40,000 | 40,000 |
| `orders` | 80 | 50,000 | 50,000 | 100,000 | 150,000 |

### Ejecute el generador de datos

>[!WARNING]
>
>Antes de ejecutar el generador de datos, deshabilite todos los trabajos cron que se ejecuten en el servidor. Deshabilitar los trabajos cron impide que el generador de datos realice acciones que entren en conflicto con los trabajos cron activos y evita errores innecesarios.

Ejecute el comando tal como se describe en esta sección. Una vez ejecutado el comando, debe [reindexar todos los indexadores](../cli/manage-indexers.md).

Opciones de comando:

```bash
bin/magento setup:perf:generate-fixtures <path-to-profile>
```

Donde `<path-to-profile>` especifica la ruta absoluta del sistema de archivos y el nombre de un perfil.

Por ejemplo,

```bash
bin/magento setup:perf:generate-fixtures /var/www/html/magento2/setup/performance-toolkit/profiles/ce/small.xml
```

Salida de muestra para el perfil pequeño:

```terminal
Generating profile with following params:
    |- Websites: 1
    |- Store Groups Count: 1
    |- Store Views Count: 1
    |- Categories: 30
    |- Attribute Sets (Default): 3
    |- Attribute Sets (Extra): 10
    |- Simple products: 800
    |- Configurable products: 0
    |--- 5 products for attribute set "Attribute Set 1"
    |--- 5 products for attribute set "Attribute Set 2"
    |--- 5 products for attribute set "Attribute Set 3"
    |--- 40 products for attribute set "Dynamic Attribute Set 1-24"
    |- Product images: 100, 3 per product
    |- Customers: 200
    |- Cart Price Rules: 20
    |- Catalog Price Rules: 20
    |- Catalog Target Rules: 5
    |- Orders: 80
Generating websites, stores and store views...  done in <time>
Generating categories...  done in <time>
Generating attribute sets...  done in <time>
Generating simple products...  done in <time>
... more ...
```

## Extras de rendimiento

### Usuarios administradores

Genera usuarios administradores. Nodo de perfil XML:

```xml
<!-- Number of admin users -->
<admin_users>{int}</admin_users>
```

### Conjuntos de atributos

Genera conjuntos de atributos con la configuración especificada. Nodo de perfil XML:

```xml
<!-- Number of product attribute sets -->
<product_attribute_sets>{int}</product_attribute_sets>

<!-- Number of attributes per set -->
<product_attribute_sets_attributes>{int}</product_attribute_sets_attributes>

<!-- Number of values per attribute -->
<product_attribute_sets_attributes_values>{int}</product_attribute_sets_attributes_values>
```

### Paquete de productos

Genera productos agrupados. Las selecciones de paquetes generadas no se muestran individualmente en el catálogo. Los productos se distribuyen uniformemente por categorías y sitios web. If  `assign_entities_to_all_websites` desde el perfil se establece en `1`. Los productos se asignan a todos los sitios web.

Nodo de perfil XML:

```xml
<!-- Number of products -->
<bundle_products>{int}</bundle_products>

<!-- Number of options per each product -->
<bundle_products_options>{int}</bundle_products_options>

<!-- Number of simple products per each option -->
<bundle_products_variation>{int}</bundle_products_variation>
```

### Reglas de precios del carrito

Genera reglas de precios del carro de compras. Nodo de perfil XML:

```xml
<!-- Number of cart price rules -->
<cart_price_rules>{int}</cart_price_rules>

<!-- Number of conditions per rule -->
<cart_price_rules_floor>{int}</cart_price_rules_floor>
```

### Reglas de precios de catálogo

Genera reglas de precios de catálogo. Nodo de perfil XML:

```xml
<!-- Number of catalog price rules -->
<catalog_price_rules>{int}</catalog_price_rules>
```

### Categorías

Genera categorías. If `assign_entities_to_all_websites` se establece en `0`Sin embargo, todas las categorías se distribuyen uniformemente por categorías raíz; de lo contrario, todas las categorías se asignan a una categoría raíz.

Nodo de perfil XML:

```xml
<!-- Number of categories to generate -->
<categories>{int}</categories>

<!-- Nesting level of categories -->
<categories_nesting_level>{int}</categories_nesting_level>
```

### Configuraciones

Establece los valores de los campos de configuración. Nodo de perfil XML:

```xml
<!-- Config variables and values for change -->
<configs>
    <config>
        <path>{string}</path> <!-- e.g. admin/security/use_form_key -->
        <scope>{string}</scope> <!-- e.g. default -->
        <scopeId>{int}</scopeId>
        <value>{int|string}</value>
    </config>

    <!-- ... more entries ... -->
</configs>
```

### Productos configurables

Genera productos configurables. Las opciones configurables generadas no se muestran individualmente en el catálogo. Los productos se distribuyen uniformemente por categorías y sitios web. If `assign_entities_to_all_websites` se establece en `1`, los productos se asignan a todos los sitios web.

Se admiten los siguientes formatos de nodo XML:

- Distribución por conjuntos de atributos predeterminados y predefinidos:

   ```xml
   <!-- Number of configurable products -->
   <configurable_products>{int}</configurable_products>
   ```

- Genere productos basados en un conjunto de atributos existente:

   ```xml
   <configurable_products>
   
       <config>
               <!-- Existing attribute set name -->
               <attributeSet>{string}</attributeSet>
   
               <!-- Configurable sku pattern with %s -->
               <sku>{string}</sku>
   
               <!-- Number of configurable products -->
               <products>{int}</products>
   
               <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
               <category>[{string}]</category>
   
               <!-- Type of Swatch attribute e.g. color|image -->
               <swatches>{string}</swatches>
       </config>
   
   <!-- ... more entries ... -->
   </configurable_products>
   ```

- Genere productos basados en un conjunto de atributos creado dinámicamente con un número determinado de atributos y opciones:

   ```xml
   <configurable_products>
   
       <config>
           <!-- Number of attributes in configurable product -->
           <attributes>{int}</attributes>
   
           <!-- Number of options per attribute -->
           <options>{int}</options>
   
           <!-- Configurable sku pattern with %s -->
           <sku>{string}</sku>
   
           <!-- Number of configurable products -->
           <products>{int}</products>
   
           <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
           <category>[{string}]</category>
   
           <!-- Type of Swatch attribute e.g. color|image -->
           <swatches>{string}</swatches>
       </config>
   
       <!-- ... more entries ... -->
   </configurable_products>
   ```

- Genere productos basados en un conjunto de atributos creado dinámicamente con una configuración especificada para cada atributo:

   ```xml
   <configurable_products>
   
       <config>
           <attributes>
               <!-- Configuration for a first attribute -->
               <attribute>
                   <!-- Amount of options per attribute -->
                   <options>{int}</options>
   
                   <!-- Type of Swatch attribute -->
                   <swatches>{string}</swatches>
               </attribute>
   
               <!-- Configuration for a second attribute -->
               <attribute>
                   <!-- Amount of options per attribute -->
                   <options>{int}</options>
               </attribute>
           </attributes>
   
           <!-- Configurable sku pattern with %s -->
           <sku>{string}</sku>
   
           <!-- Number of configurable products -->
           <products>{int}</products>
   
           <!-- Category Name. Optional. By default, the category name from Categories fixture will be used -->
           <category>[{string}]</category>
       </config>
   
       <!-- ... more entries ... -->
   </configurable_products>
   ```

### Clientes

Genera clientes. Los clientes tienen una distribución normal en todos los sitios web disponibles. Cada cliente tiene los mismos datos excepto el correo electrónico del cliente, el grupo de clientes y las direcciones de clientes.

Nodo de perfil XML:

```xml
<!-- Number of customers to generate -->
<customers>{int}</customers>
```

Puede utilizar el siguiente XML para cambiar la configuración del cliente:

```xml
<customer-config>
    <!-- Number of addresses per each customer -->
    <addresses-count>{int}</addresses-count>
</customer-config>
```

### Imágenes de productos

Genera imágenes de productos. La generación no incluye el cambio de tamaño.

Nodo de perfil XML:

```xml
<product-images>
    <!-- Number of images to generate -->
    <images-count>{int}</images-count>

    <!-- Number of images to be assigned per each product -->
    <images-per-product>{int}</images-per-product>
</product-images>
```

### Estado de indizadores

Actualiza el estado de los indexadores. Nodo de perfil XML:

```xml
<indexer>
    <!-- Name of indexer (e.g. catalogrule_product) -->
    <id>{string}</id>
    <set_scheduled>{bool}</set_scheduled>
</indexer>
```

### Pedidos

Genera pedidos con un número configurable de diferentes tipos de artículos de pedido. Opcionalmente genera ofertas inactivas para pedidos generados.

Nodo de perfil XML:

```xml
<!-- It is necessary to enable quotes for orders -->
<order_quotes_enable>{bool}</order_quotes_enable>

<!-- Min number of simple products per each order -->
<order_simple_product_count_from>{int}</order_simple_product_count_from>

<!-- Max number of simple products per each order -->
<order_simple_product_count_to>{int}</order_simple_product_count_to>

<!-- Min number of configurable products per each order -->
<order_configurable_product_count_from>{int}</order_configurable_product_count_from>

<!-- Max number of configurable products per each order -->
<order_configurable_product_count_to>{int}</order_configurable_product_count_to>

<!-- Min number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_from>{int}</order_big_configurable_product_count_from>

<!-- Max number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_to>{int}</order_big_configurable_product_count_to>

<!-- Number of orders to generate -->
<orders>{int}</orders>
```

### Productos simples

Genera productos simples. Los productos se distribuyen por conjuntos de atributos predeterminados y predefinidos. Si se especifican conjuntos de atributos adicionales en el perfil como: `<product_attribute_sets>{int}</product_attribute_sets>`, los productos también se distribuyen por conjuntos de atributos adicionales.

Los productos se distribuyen uniformemente por categorías y sitios web. If `assign_entities_to_all_websites` se establece en `1`, los productos se asignan a todos los sitios web.

Nodo de perfil XML:

```xml
<!-- Number of simple products to generate -->
<simple_products>{int}</simple_products>
```

### Sitios web

Genera sitios web. Nodo de perfil XML:

```xml
<!-- Number of websites to be generated -->
<websites>{int}</websites>
```

### Grupos de tienda

Genera grupos de almacenamiento (denominados en el Administrador como _tiendas_). Los grupos de tiendas se distribuyen normalmente entre los sitios web.

Nodo de perfil XML:

```xml
<!-- Number of store groups to be generated -->
<store_groups>{int}</store_groups>
```

### Vistas de tienda

Genera vistas de tienda. Las vistas de tiendas se distribuyen normalmente entre los grupos de tiendas. Nodo de perfil XML:

```xml
<!-- Number of store views to be generated -->
<store_views>{int}</store_views>

<!-- 1 means that all stores will have the same root category, 0 means that all stores will have unique root category -->
<assign_entities_to_all_websites>{0|1}<assign_entities_to_all_websites/>
```

### Tipos impositivos

Genera tasas de impuestos. Nodo de perfil XML:

```xml
<!-- Accepts name of CSV file with tax rates (<path to Commerce folder>/setup/src/Magento/Setup/Fixtures/_files) -->
<tax_rates_file>{CSV file name}</tax_rates_file>
```

## Información adicional de configuración:

- `<Commerce root dir>/setup/performance-toolkit/config/attributeSets.xml`: conjuntos de atributos predeterminados

- `<Commerce root dir>/setup/performance-toolkit/config/customerConfig.xml`: configuración del cliente

- `<Commerce root dir>/setup/performance-toolkit/config/description.xml`—Configuración de la descripción completa del producto

- `<Commerce root dir>/setup/performance-toolkit/config/shortDescription.xml`: configuración de descripción breve del producto

- `<Commerce root dir>/setup/performance-toolkit/config/searchConfig.xml`: configuración para la descripción breve y completa del producto. Esta implementación anterior se proporciona para la compatibilidad con versiones anteriores.

- `<Commerce root dir>/setup/performance-toolkit/config/searchTerms.xml`: pequeño número de términos de búsqueda a en descripciones cortas y completas.

- `<Commerce root dir>/setup/performance-toolkit/config/searchTermsLarge.xml`: mayor número de términos de búsqueda para utilizar en una descripción breve y completa.
