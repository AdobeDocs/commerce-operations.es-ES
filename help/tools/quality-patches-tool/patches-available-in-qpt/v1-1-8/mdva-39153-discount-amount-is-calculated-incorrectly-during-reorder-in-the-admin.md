---
title: 'MDVA-39153: La cantidad de descuento se calcula incorrectamente durante el repedido en el administrador'
description: El parche MDVA-39153 corrige el problema en el que la cantidad de descuento se calcula incorrectamente durante el repedido en el administrador. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8. El ID del parche es MDVA-39153. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: Admin Workspace, Orders, Personalization, Payments
role: Admin
exl-id: e8fe58ca-1218-4e76-b5fb-c7f935029cd2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-39153: La cantidad de descuento se calcula incorrectamente durante el repedido en el administrador

El parche MDVA-39153 corrige el problema en el que la cantidad de descuento se calcula incorrectamente durante el repedido en el administrador. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8. El ID del parche es MDVA-39153. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El importe de descuento se calcula incorrectamente durante el repedido en el administrador.

<u>Pasos a seguir</u>:

1. Vaya a **Administración** > **Tiendas** > **Configuración** > **Ventas** > **Impuestos**.
1. Active el impuesto para el envío mostrando el impuesto en el carro de compras.
1. Habilite y configure el método de envío de tarifa de tabla ($15).
1. Cree una regla fiscal para el tipo impositivo integrado (para CA).
1. Cree una regla de precio de carro de compras con un descuento fijo de 5 $ aplicado a todo el carro de compras y al importe de envío.
1. Añada un producto con un precio de 12 $ al carro de compras y vaya a la página Carro de compras.
1. Aplicar el descuento al carro de compras.
1. Establece el método de envío en la sección &quot;estimaciones&quot; en &quot;tarifa plana&quot;.
1. Continúe con el cierre de compra hasta los pasos de revisión (no realice el pedido).
1. Vaya a la página principal y vuelva al carro de compras.
1. Cambie el método de envío en la sección &quot;estimaciones&quot; a &quot;Tarifa de tabla&quot;.

<u>Resultados esperados</u>:

El descuento sigue siendo el mismo: 5 dólares.

<u>Resultados reales</u>:

El descuento es de $6.31.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
