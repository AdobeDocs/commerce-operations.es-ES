---
title: 'MDVA-41399: No se puede acceder a Administrar carro de compras si un cliente agrega un producto a la lista de deseos'
description: El parche MDVA-41399 resuelve el problema en el que los usuarios administradores no pueden acceder a la página Administrar carro de compras si un cliente agrega un producto a la lista de deseos. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6. El ID del parche es MDVA-41399. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: 81a128b5-0c38-4f8f-b297-1f264952d431
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-41399: No se puede acceder a Administrar carro de compras si un cliente agrega un producto a la lista de deseos

El parche MDVA-41399 resuelve el problema en el que los usuarios administradores no pueden acceder a la página Administrar carro de compras si un cliente agrega un producto a la lista de deseos. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6. El ID del parche es MDVA-41399. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios administradores no pueden acceder a la página Administrar carro de compras si un cliente añade un producto a la lista de deseos.

<u>Requisitos previos</u>:

1. Cree dos o más productos.
1. Crear un cliente.
1. Active el modo de desarrollador.

<u>Pasos a seguir</u>:

1. Vaya a Storefront e inicie sesión como cliente desde las condiciones previas.
1. Añadir un producto a la lista de deseos.
1. Vaya al panel de administración, navegue hasta la página de edición del cliente creada y haga clic en el botón **Administrar carro de compras**.

<u>Resultados esperados</u>:

El usuario administrador puede administrar el carro de compras.

<u>Resultados reales</u>:

El usuario administrador recibe un mensaje de error: *Se produjo un error. Consulte el registro de errores para obtener detalles.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
