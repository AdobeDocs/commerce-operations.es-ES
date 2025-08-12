---
title: 'ACSD-66301: al mover productos de un pedido al carro de compras en Commerce Admin, la cantidad no coincide'
description: Aplique el parche ACSD-66301 para solucionar el problema de Adobe Commerce en el que, al crear una solicitud desde el panel de administración, los productos del carro de compras del cliente no se eliminan después de agregarse al pedido.
feature: Orders, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9a4224c02634514a9428dc6b0daf4c1d5f5c7c43
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# ACSD-66301: al mover productos de un pedido al carro de compras en el administrador de Commerce, la cantidad no coincide

El parche de ACSD-66301 corrige el problema en el que el traslado de productos de un pedido de vuelta al carro de compras en el administrador produce una discrepancia de cantidades. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. El ID del parche es ACSD-66301. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p10, 2.4.7-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p9 - 2.4.6-p11, 2.4.7-p4 - 2.4.7-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Si se devuelven productos de un pedido al carro de compras en el Administrador de Commerce, la cantidad no coincide.

<u>Pasos a seguir</u>:

1. Cree un usuario a través de la tienda.
2. Agregar un producto al carro de compras con cantidad = *5*.
3. Vaya al panel de administración y abra la cuenta de usuario en la que se añadió el producto.
4. Haga clic en **[!UICONTROL Create Order]**.
5. En el panel izquierdo, puede ver las actividades del cliente, incluidos el producto y la cantidad añadida.
6. Añada el producto al pedido.
7. Actualice la cantidad = *4* en la sección de pedido principal.
8. Haga clic en el botón **[!UICONTROL Update Items and Quantities]**.
9. Transfiera los artículos seleccionados del pedido al carro de compras del cliente.

<u>Resultados esperados</u>:

Producto agregado al carro de compras con la nueva cantidad = *4*.

<u>Resultados reales</u>:

Producto agregado al carro de compras con la cantidad antigua = *5*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
