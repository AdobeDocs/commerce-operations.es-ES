---
title: "ACSD-45241: La cantidad de stock del producto virtual no se ha calculado correctamente"
description: El parche ACSD-45241 corrige el problema en el que la cantidad de existencias del producto virtual se calcula de forma incorrecta después de crear un abono. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17. El ID del parche es ACSD-45241. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.4.
feature: Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# ACSD-45241: la cantidad de existencias del producto virtual se ha calculado incorrectamente

El parche ACSD-45241 corrige el problema en el que la cantidad de existencias del producto virtual se calcula de forma incorrecta después de crear un abono. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17. El ID del parche es ACSD-45241. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cantidad de stock de un producto virtual se calcula incorrectamente después de crear una nota de abono.

<u>Pasos a seguir</u>:

1. Cree un producto configurable con un producto virtual como producto secundario en el administrador de Commerce.
1. Asegúrese de que ambos productos creados en el paso uno estén en stock.
1. Marque la cantidad del producto virtual creado en el paso uno como 100 y mantenga también la cantidad vendible como 100.
1. Añadir el producto al carro de compras.
1. Realice un pedido con el producto virtual creado en el paso uno.
1. Mantenga el estado del pedido como Pendiente. No es necesario procesar el pago.
1. Registro `order_created` creado en `inventory_reservation`. La cantidad de producto virtual muestra 100 con una cantidad vendible de 99.
1. Abra el pedido y vaya a **Factura** > **Enviar factura**.
1. Registro `invoice_created` creado en `inventory_reservation`. La cantidad de producto virtual es ahora 99, y la cantidad vendible también es 99.
1. Crear un abono sin seleccionar **Volver a Stock**.

<u>Resultados esperados</u>:

No se crea ningún registro nuevo en `inventory_reservation` y la cantidad de existencias del producto virtual no se modifica.

<u>Resultados reales</u>:

Se crea un registro `creditmemo_created` en `inventory_reservation` y la cantidad de existencias del producto virtual se ajusta a 98 con la cantidad vendible como 99.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
