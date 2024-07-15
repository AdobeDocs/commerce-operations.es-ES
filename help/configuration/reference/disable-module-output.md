---
title: Deshabilitar salida del módulo
description: Obtenga información sobre cómo deshabilitar la salida del módulo.
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Deshabilitar salida del módulo

De forma predeterminada, todos los módulos se configuran para que la salida del módulo se pueda escribir en una vista. La desactivación de la salida ofrece una forma de deshabilitar esencialmente un módulo que no se puede deshabilitar debido a las dependencias del hardware.

Por ejemplo, el módulo `Customer` depende del módulo `Review`, por lo que el módulo `Review` no se puede deshabilitar. Sin embargo, si no desea que los clientes proporcionen revisiones, puede desactivar el resultado del módulo `Review`.

>[!INFO]
>
>Si un comerciante utilizó el administrador para deshabilitar la salida del módulo en una versión anterior, debe configurar manualmente el sistema para migrar esta configuración.

La deshabilitación de Output se realiza en las siguientes clases:

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>Al deshabilitar la salida del módulo no se deshabilita el módulo. El módulo permanece habilitado y en funcionamiento, pero no se procesa ningún bloque, página o campo en el front-end o back-end.

## Deshabilitar la salida del módulo en una implementación de canalización

Para deshabilitar los resultados de los módulos en la implementación de la canalización o en cualquier otra implementación, con varias instancias de la aplicación de Commerce:

1. Edite el archivo `config.xml` del módulo `Backend`.
1. Exporte los cambios de configuración.

### Editar el archivo `config.xml` del módulo `Backend`

1. Archivar el archivo `config.xml` original.
1. Agregue líneas similares a las siguientes al archivo `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml`, directamente debajo del elemento `<default>`:

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
   - `1` es el indicador que deshabilita la salida para el módulo `Magento_Newsletter`.

Como resultado de esta configuración, los clientes ya no pueden suscribirse para recibir boletines.

### Exportar los cambios de configuración

Ejecute el siguiente comando para exportar los cambios de configuración:

```bash
bin/magento app:config:dump
```

Los resultados se escriben en el archivo `<Magento_install_dir>/app/etc/config.php`.

A continuación, borre la caché para habilitar la nueva configuración:

```bash
bin/magento cache:clean config
```

Consulte [Exportar la configuración](../cli/export-configuration.md).

## Deshabilitar la salida del módulo en una implementación simple

El procedimiento para deshabilitar la salida del módulo en una sola instancia de Commerce es más sencillo porque los cambios no tienen que distribuirse.

1. Archivar el archivo `<Magento_install_dir>/app/etc/config.php` original.
1. Agregue las secciones `advanced` y `modules_disable_output` al archivo `config.php` (si no existen):

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

En este ejemplo, la salida del módulo `Magento_Review` se ha deshabilitado y los clientes ya no pueden revisar los productos.
Para volver a habilitar la salida, establezca el valor en `0`.
