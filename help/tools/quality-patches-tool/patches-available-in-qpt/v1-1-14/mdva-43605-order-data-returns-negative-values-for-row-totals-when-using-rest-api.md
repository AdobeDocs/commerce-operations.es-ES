---
title: 'MDVA-43605: Los datos de pedidos devuelven valores negativos para los totales de fila al utilizar la API de REST'
description: El parche MDVA-43605 corrige el problema en el que los datos de pedidos devuelven valores negativos para los totales de filas al utilizar la API de REST. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14. El ID del parche es MDVA-43605. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: REST, Orders
role: Admin
exl-id: f27439a6-eeee-4176-9ac9-98220752db3f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-43605: Los datos de pedidos devuelven valores negativos para los totales de fila al utilizar la API de REST

El parche MDVA-43605 corrige el problema en el que los datos de pedidos devuelven valores negativos para los totales de filas al utilizar la API de REST. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14. El ID del parche es MDVA-43605. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.1 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los datos del pedido devuelven valores negativos para los totales de fila al utilizar la API de REST.

<u>Pasos a seguir</u>:

1. Habilitar el envío gratuito.
1. Vaya a **Configuración** > **Catálogo** > **Precio** > y establezca el ámbito del precio del catálogo = Sitio web.
1. Vaya a **Configuración** > **Ventas** > **Impuestos** y actualice:
   * Clase De Impuesto Para Envío = Productos Imponibles
   * Configuración de cálculo:
      * Precio de catálogo = Impuestos incluidos
      * Precio de envío = Precio incluido
      * Aplicación De Descuentos En Precios = Impuestos Incluidos
   * Configuración de Visualización de Precios: Incluyendo Impuestos (todos los campos)
   * Configuración de visualización del carro de compras: Impuestos incluidos (todos los campos)
   * Pedidos, Facturas, Notas de Abono:
      * Mostrar importe de envío = Impuestos incluidos
1. Cree un tipo impositivo para EE. UU. (Estado = &#39;*&#39;), Porcentaje de tipo = 24,00
1. Cree una regla fiscal con el tipo impositivo anterior.
1. Cree una regla de precio de carro de compras con un cupón específico y Descuento = 50 $ de la Cantidad fija para todo el carro de compras.
1. Cree cuatro productos con los siguientes precios: 8,90, 5,90, 6,90 y 5,95 $.
1. Cree un pedido de administrador que incluya cuatro de estos productos utilizando el código de cupón creado en el paso anterior. Utiliza el envío gratuito.
1. No se requiere el pago, ya que el código de cupón cubre el total del carrito.
1. Recupere el pedido que acaba de crear mediante el punto final de la API de REST:

   ```json
   GET rest/V1/orders/1
   ```

<u>Resultados esperados</u>:

Los valores de `base_row_total` y `base_row_total_incl_tax` en la respuesta son cero.

<u>Resultados reales</u>:

Los campos `base_row_total` y `base_row_total_incl_tax` de la respuesta tienen valores negativos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
