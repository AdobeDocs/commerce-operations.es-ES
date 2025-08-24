---
title: 'ACSD-67347: El pedido falla con el error "No se puede adquirir un bloqueo" al utilizar códigos de cupones'
description: Aplique el parche ACSD-67347 al problema de Adobe Commerce donde los pedidos fallan con el error "No se puede adquirir un bloqueo" cuando los códigos de cupones contienen caracteres especiales (por ejemplo, BIT/123456) y el bloqueo de archivos está habilitado.
feature: Checkout, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 1a48428efbb022b53320370f68691eaed44809b3
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# ACSD-67347: el pedido falla con *No se puede adquirir un error lock* al usar códigos de cupones

El parche ACSD-67347 corrige el problema en el que los pedidos fallan con un error *No se puede adquirir un bloqueo* cuando los códigos de cupones contienen caracteres especiales (por ejemplo, BIT/123456) y el bloqueo de archivos está habilitado. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACSD-67347. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p12

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p11 - 2.4.5-p13

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los pedidos fallan con el error *No se puede adquirir un bloqueo* cuando se usan cupones con caracteres especiales y el bloqueo de archivos está habilitado.

<u>Pasos a seguir</u>:

1. Instalar 2.4-desarrollar.
1. Establecer la configuración de bloqueo de archivos en el archivo `env.php`:

   ```
   'lock' => [
           'provider' => 'file',
           'config' => [
               'path' => '/Users/awijesooriya/sites/acsd15194dev/locks'
           ]
       ],
   ```

1. Cree una regla de carro de compras con un cupón usando el formato de código de cupón: *BIT/123456*.
1. Cree un producto sencillo.
1. Añadir el producto al carro de compras y aplicar el código de cupón.
1. Continúe con el cierre de compra y realice el pedido.

<u>Resultados esperados</u>:

Los pedidos se realizan correctamente porque no hay restricciones en la creación de códigos de cupones.

<u>Resultados reales</u>:

No se puede realizar el pedido. Aparece el siguiente error: *No se puede adquirir el bloqueo.*

```
File "/Users/test/sites/test/locks/coupon_code_123/abc" cannot be opened Warning!fopen(/Users/test/sites/test/locks/coupon_code_123/abc): Failed to open stream: No such file or directory
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
