---
title: 'MDVA-41350: Excepción cuando el administrador agrega productos fuera de su acceso'
description: El parche MDVA-41350 corrige el problema en el que se produce un error de excepción en lugar de una notificación de acceso limitado cuando un usuario administrador añade un producto en el pedido por SKU que está fuera de su acceso. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11. El ID del parche es MDVA-41350. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Admin Workspace, Products
role: Admin
exl-id: 4dc5ee5c-bd93-42e1-9c63-93ffb8e5f21c
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-41350: Excepción cuando el administrador agrega productos fuera de su acceso

El parche MDVA-41350 corrige el problema en el que se produce un error de excepción en lugar de una notificación de acceso limitado cuando un usuario administrador añade un producto en el pedido por SKU que está fuera de su acceso. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.11. El ID del parche es MDVA-41350. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando un usuario administrador con acceso restringido añade un producto por SKU fuera de su acceso en el pedido, se produce una excepción en lugar de un mensaje que notifica al usuario su acceso limitado.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador como un usuario con acceso solo a un sitio web específico.
1. Vaya a **Ventas** > **Pedidos** y haga clic en **Crear nuevo pedido**.
1. Seleccione una vista de cliente y otra de tienda.
1. Haz clic en **Agregar productos por SKU**.
1. Busque un SKU que no esté asignado a ningún sitio web o que no esté asignado al sitio web al que tiene acceso.
1. Haga clic en **Agregar a pedido**.

<u>Resultados esperados</u>:

Se muestra un mensaje de error apropiado.

<u>Resultados reales</u>:

Se produce una excepción.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
