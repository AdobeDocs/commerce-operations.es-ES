---
title: 'ACSD-65202: la página Mi cuenta no muestra pedidos recientes de otras vistas de tiendas'
description: Aplique el parche ACSD-65202 para solucionar el problema de Adobe Commerce en el que la página Mi cuenta no muestra pedidos recientes de otras vistas de tienda dentro de la misma tienda.
feature: Orders, User Account
role: Admin, Developer
type: Troubleshooting
exl-id: 031f12f2-1b70-4cbc-92a0-8eb561e34067
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-65202: la página [!UICONTROL My Account] no muestra pedidos recientes de otras vistas de tiendas

El parche ACSD-65202 corrige el problema en el que la página **[!UICONTROL My Account]** no muestra pedidos recientes de otras vistas de tienda dentro del mismo almacén. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. El ID del parche es ACSD-65202. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p12

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando va a la página de cuenta de cliente (sección **[!UICONTROL My Account]**), no ve los pedidos recientes realizados en otra vista de tienda. Sin embargo, cuando vaya al historial de pedidos (sección *[!UICONTROL My Orders]*), verá todos los pedidos en ambas vistas de la tienda.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce.
1. En el panel *Administrador*, cree una nueva vista de tienda e introduzca su código como *segundo* para identificar la vista.
1. Cree un producto simple y vuelva a indexar.
1. Cree una cuenta de cliente y haga un pedido en la vista de tienda predeterminada cuyo código es *default*.
1. Vaya a la página **[!UICONTROL My Orders]** y compruebe que el orden es visible en ambas vistas de la tienda, por ejemplo:
1. Predeterminado: https://localhost/pub/default/sales/order/history/
1. Segundo: https://localhost/pub/second/sales/order/history/

1. Ir a la página **[!UICONTROL My Account]** en ambas vistas de la tienda:
1. Predeterminado: https://localhost/pub/default/customer/account/
1. Segundo: https://localhost/pub/second/customer/account/

<u>Resultados esperados</u>:

Puede ver los pedidos de ambas vistas de tienda en la página Pedidos. Es la misma tienda, solo una vista diferente de la tienda.

<u>Resultados reales</u>:

El comportamiento es inconsistente. Los pedidos no aparecen en la vista de la segunda tienda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
