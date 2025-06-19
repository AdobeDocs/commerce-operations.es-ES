---
title: 'MDVA-43824: La acción de cancelación del pedido falló con el error "No ha cancelado el artículo"'
description: 'El parche de MDVA-43824 soluciona el problema en el que la acción de cancelación del pedido fallaba con el siguiente error: *No has cancelado el artículo*. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. El ID del parche es MDVA-43824. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.'
feature: Orders
role: Admin
exl-id: 8c2d15a0-2f53-4583-bdf2-86746f61160f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-43824: La acción de cancelación del pedido falló con el error &quot;No ha cancelado el artículo&quot;

El parche de MDVA-43824 resuelve el problema en el que la acción de cancelación del pedido falló con el error: *No ha cancelado el elemento*. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. El ID del parche es MDVA-43824. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.6 - 2.3.7-p3, 2.4.1 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se puede cancelar el pedido realizado por un cliente que ha iniciado sesión. Error en la acción de cancelación del pedido:

```
Zend_Db_Statement_Exception: SQLSTATE[23000]: Integrity constraint violation: 1452 Cannot add or update a child row: a foreign key constraint fails (`mer33515_ee24developpbdevelop`.`salesrule_customer`, CONSTRAINT `SALESRULE_CUSTOMER_RULE_ID_SEQUENCE_SALESRULE_SEQUENCE_VALUE` FOREIGN KEY (`rule_id`) REFERENCES `sequence_salesrule` (`sequen), query was: INSERT INTO `salesrule_customer` () VALUES (){code}
```

<u>Pasos a seguir</u>:

1. Cree una regla de ventas (el tipo de cupón es &quot;Cupón específico&quot; o &quot;Sin cupón&quot;).
1. Vaya a la tienda, inicie sesión como cliente y añada un producto al carro de compras.
1. Vaya al carro de compras y aplique la regla de precio si la regla tiene un cupón como &quot;Cupón específico&quot;. La regla de precios del carro de compras debe aplicarse correctamente.
1. Vaya a Pago y envío y haga el pedido con cualquier forma de pago.
1. Vaya a Commerce Admin > **Ventas** > **Pedidos**.
1. Abra el pedido realizado en el paso 4.
1. Haga clic en el botón **Cancelar**.

<u>Resultados esperados</u>:

El pedido se cancela correctamente sin ningún error.

<u>Resultados reales</u>:

Error en la acción de cancelación del pedido: *No ha cancelado el elemento.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
