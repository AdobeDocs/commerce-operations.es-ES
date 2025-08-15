---
title: 'MDVA-42645: El administrador no puede devolver puntos de recompensa por el crédito de tienda deshabilitado'
description: El parche MDVA-42645 resuelve el problema en el que el administrador no puede devolver puntos de recompensa si la funcionalidad de crédito de la tienda está desactivada. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-42645. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
exl-id: 8053fcc7-d30c-424a-9494-df6e8630b095
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# MDVA-42645: El administrador no puede devolver puntos de recompensa por el crédito de tienda deshabilitado

El parche MDVA-42645 resuelve el problema en el que el administrador no puede devolver puntos de recompensa si la funcionalidad de crédito de la tienda está desactivada. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-42645. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El administrador no puede reembolsar puntos de recompensa si la funcionalidad de crédito de la tienda está desactivada.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Cree una nueva cuenta de cliente y añada algunos puntos de recompensa.
1. Deshabilite la funcionalidad de crédito de tienda yendo a **Tienda** > Configuración > **Configuración** > **Cliente** > **Configuración del cliente** > **Opciones de crédito de tienda**.
1. Inicie sesión como el cliente al que se asignan los puntos de recompensa.
1. Añada un producto al carro de compras y navegue hasta el cierre de compra.
1. Utilice los puntos de recompensa en la sección de pago y realice el pedido.
1. Abra el pedido en el administrador y factura el pedido.
1. Haga clic en el vínculo **Nota de crédito** para crear una nueva nota de crédito.
1. Marque la opción Reembolsar puntos de recompensa en la parte inferior y haga clic en **Reembolsar sin conexión**.

<u>Resultados esperados</u>:

* El abono se ha creado correctamente.
* Los puntos de recompensa se reembolsan correctamente.

<u>Resultados reales</u>:

Recibe el siguiente mensaje de error: *No puede usar más crédito de tienda que el importe del pedido.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
