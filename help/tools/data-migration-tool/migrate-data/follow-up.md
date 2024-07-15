---
title: Seguimiento de la migración de datos
description: Aprenda a validar que la migración de datos de Magento 1 a Magento 2 se realizó correctamente y que todas las funcionalidades funcionan según lo esperado.
exl-id: a55f357b-6c95-49d6-b2f1-c2e403a8c85f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Seguimiento de la migración de datos

Algunas conductas y lógicas del Magento 1 se han implementado de forma diferente en el Magento 2. [!DNL Data Migration Tool] se encarga de ello. Hay algunos aspectos de la migración que debe conocer y, a veces, debe realizar pasos menores para que algunas funcionalidades funcionen sin problemas después de la migración.

## Información

### Base de datos dividida no admitida

[!DNL Data Migration Tool] no admite bases de datos divididas.

### Precios de grupo convertidos en precios de nivel

Todos los precios de grupo se convierten automáticamente a precios de nivel durante la migración.

### Nueva numeración para entidades de ventas

Los números de referencia de pedidos, facturas, envíos, notas de abono y autorizaciones de devolución de material migran tal cual. Después de la migración, se aplican las nuevas reglas de asignación de números de Magento 2. La numeración de las nuevas entidades de ventas es diferente.

## Pasos

### Volver a guardar segmentos de clientes [solo Adobe Commerce]

Después de la migración, los segmentos del cliente deben volver a guardarse desde el panel de administración para ponerlos en marcha.

### Configurar zona horaria

La herramienta no migra la configuración de zona horaria, por lo que debe configurarla manualmente después de la migración en **Tiendas** > **Configuración** > **Opciones de configuración regional** > **Zona horaria**.

De forma predeterminada, Magento almacena los datos de hora en la zona UTC-0 de la base de datos y los muestra según la configuración de zona horaria actual. Si los datos de tiempo ya se han guardado en la base de datos en una zona distinta de UTC-0, debe convertir la hora existente a UTC-0 mediante el controlador `\Migration\Handler\Timezone` de [!DNL Data Migration Tool].

En el siguiente ejemplo, el Magento 1 ha estado ahorrando tiempo de forma incorrecta en la zona UTC-7 de la base de datos (por ejemplo, debido a una extensión de terceros defectuosa). Para convertir correctamente la hora de creación de la cuenta del cliente a la zona UTC-0 tras la migración, siga estos pasos:

1. Copie el archivo de configuración `map-customer.xml.dist` del directorio apropiado de [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) en el archivo `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml`.

1. Actualice el nodo `<customer_map_file>` en `config.xml` y quite la extensión `.dist` de `map-customer.xml.dist`

1. Agregue la siguiente regla al archivo `map-customer.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="../map.xsd">
  <!--...-->
  <destination>
      <field_rules>
          <!--...-->
          <transform>
              <field>customer_entity.created_at</field>
              <handler class="\Migration\Handler\Timezone">
                  <param name="offset" value="-7" />
              </handler>
          </transform>
      </field_rules>
  </destination>
</map>
```
