---
title: Deshabilitar salida de módulo
description: Aprenda a desactivar la salida del módulo.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---


# Deshabilitar salida de módulo

De forma predeterminada, todos los módulos están configurados para que la salida del módulo se pueda escribir en una vista. Desactivar salida ofrece una forma de deshabilitar esencialmente un módulo que no se puede deshabilitar debido a dependencias difíciles.

Por ejemplo, la variable `Customer` depende del `Review` módulo, por lo que la variable `Review` no se puede deshabilitar. Sin embargo, si no desea que los clientes proporcionen revisiones, puede desactivar el resultado de la `Review` módulo.

>[!INFO]
>
>Si un comerciante utilizó el administrador para deshabilitar la salida del módulo en una versión anterior, debe configurar manualmente el sistema para migrar estos ajustes.

La desactivación de la salida se realiza en las siguientes clases:

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>Al desactivar la salida del módulo, no se desactiva el módulo. El módulo permanece habilitado y en funcionamiento, pero no se procesa ningún bloque, página o campo en el front-end o en el backend.

## Desactivación de la salida del módulo en una implementación de canalización

Para deshabilitar la salida del módulo en la implementación de la canalización o en cualquier otra implementación, con varias instancias de la aplicación Commerce:

1. Edite el `Backend` módulo `config.xml` archivo.
1. Exporte los cambios de configuración.

### Edite el `Backend` módulo `config.xml` file

1. Archivar el original `config.xml` archivo.
1. Añada líneas similares a las siguientes al `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` directamente en la sección `<default>` elemento:

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   Aquí:

   - `<modules_disable_output>` contiene una lista de módulos.
   - `<Magento_Newsletter></Magento_Newsletter>` especifica para qué módulo deshabilitar la salida.
   - `1` es el indicador que deshabilita la salida para la variable `Magento_Newsletter` módulo.

Como resultado de esta configuración, los clientes ya no pueden registrarse para recibir boletines informativos.

### Exportar los cambios de configuración

Ejecute el siguiente comando para exportar los cambios de configuración:

```bash
bin/magento app:config:dump
```

Los resultados se escriben en la variable `<Magento_install_dir>/app/etc/config.php` archivo.

A continuación, borre la caché para habilitar la nueva configuración:

```bash
bin/magento cache:clean config
```

Consulte [Exportar la configuración](../cli/export-configuration.md).

## Desactivación de la salida del módulo en una implementación simple

El procedimiento para desactivar la salida del módulo en una sola instancia de Commerce es más fácil porque no es necesario distribuir los cambios.

1. Archivar el original `<Magento_install_dir>/app/etc/config.php` archivo.
1. Agregue la variable `advanced` y `modules_disable_output` a `config.php` (si no existen):

   ```php
   'system' =>
     array (
       'websites' =>
       array (
         'base' =>
         array (
           'advanced' =>
           array (
             'modules_disable_output' =>
             array (
               'Magento_Review' => '1',
             ),
           ),
         ),
       ),
     ),
   ```

En este ejemplo, la salida para la variable `Magento_Review` se ha deshabilitado y los clientes ya no pueden revisar los productos.
Para volver a habilitar la salida, establezca el valor en `0`.
