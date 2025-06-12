---
title: 'ACSD-54966: Corrección para reutilizar códigos de cupones después de pedidos fallidos'
description: Aplique el parche ACSD-54966 para corregir el problema de Adobe Commerce que impide la reutilización de códigos de cupones limitados por promociones y carro de compras después de un pedido fallido anteriormente.
feature: Promotions/Events, Shopping Cart, Orders
role: Admin, Developer
exl-id: e08062e5-62ff-4da6-918f-896af36edccc
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-54966: Corrección para reutilizar códigos de cupones después de pedidos fallidos

El parche ACSD-54966 corrige el problema que impide la reutilización de códigos de cupones limitados por cliente después de un pedido fallido anteriormente. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42. El ID del parche es ACSD-54966. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1
* Adobe Commerce 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.5-p10, 2.4.6 - 2.4.6-p8
* Adobe Commerce: 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un código de cupón, limitado para un solo uso por cliente, no se puede reutilizar después de un pedido anterior fallido.

<u>Pasos a seguir</u>:

1. Configurar una regla de precio de carro de compras con *[!UICONTROL Uses per Customer]* = *1*.
1. Realice una compra utilizando el código de cupón asignado.
1. Cancele la solicitud desde el panel de administración o ejecútela con un error de pago.
1. Ejecute el comando: `bin/magento queue:consumers:start sales.rule.update.coupon.usage`
1. Intente realizar un pedido posterior utilizando el mismo código de cupón para el mismo cliente.

<u>Resultados esperados</u>:

Después de cancelar el pedido o de encontrar un error en el pago, el cliente puede reutilizar correctamente el código de cupón para una nueva compra.

<u>Resultados reales</u>:

El cliente no puede reutilizar el código de cupón.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
