---
title: Seguimiento de la migración de datos
description: Obtenga información sobre cómo validar que la migración de datos de Magento 1 a Magento 2 se haya realizado correctamente y que toda la funcionalidad funcione correctamente.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---


# Seguimiento de la migración de datos

Algunos comportamientos y lógicas del Magento 1 se han implementado de forma diferente en el Magento 2. La variable [!DNL Data Migration Tool] se encarga de ello. Hay algunos aspectos de migración que debe conocer y, a veces, debe realizar algunos pasos menores para que algunas funcionalidades funcionen sin problemas después de la migración.

## Información

### Base de datos dividida no admitida

La variable [!DNL Data Migration Tool] no admite bases de datos divididas.

### Precios de grupo convertidos a precios de nivel

Todos los precios de grupo se convierten automáticamente a precios de nivel durante la migración.

### Nueva numeración para entidades de venta

Los números de referencia para Pedidos, Facturas, Envíos, Notas de Crédito y RMA migran tal cual. Después de la migración, se aplican las nuevas reglas de asignación de números del Magento 2. La numeración de las nuevas entidades de venta es diferente.

## Pasos

### Volver a guardar segmentos del cliente [Solo Adobe Commerce]

Después de la migración, los segmentos del cliente deben guardarse del panel de administración para que estén en funcionamiento.

### Configuración de zona horaria

La herramienta no migra la configuración de zona horaria, por lo que debe configurar manualmente la zona horaria después de la migración en **Almacenes** > **Configuración** > **Opciones de configuración regional** > **Zona horaria**.

De forma predeterminada, Magento almacena datos de hora en la zona UTC-0 de la base de datos y los muestra según la configuración de zona horaria actual. Si los datos de hora ya se han guardado en la base de datos en una zona distinta a UTC-0, debe convertir la hora existente a UTC-0 utilizando la variable [!DNL Data Migration Tool]&#39;s `\Migration\Handler\Timezone` controlador.

En el siguiente ejemplo, el Magento 1 ha estado ahorrando tiempo incorrectamente en la zona UTC-7 de la base de datos (por ejemplo, debido a una extensión de terceros defectuosa). Para convertir correctamente el tiempo de creación de cuentas de cliente a la zona UTC-0 tras la migración, siga estos pasos:

1. Copie el `map-customer.xml.dist` archivo de configuración desde el directorio correspondiente del [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>`) en el `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/map-customer.xml` archivo.

1. Actualice el `<customer_map_file>` nodo en `config.xml` y elimine el `.dist` de `map-customer.xml.dist`

1. Agregue la siguiente regla a la `map-customer.xml` archivo:

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
