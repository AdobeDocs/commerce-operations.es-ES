---
title: "MDVA-39923: la búsqueda por SKU en la funcionalidad de pedido rápido B2B distingue entre mayúsculas y minúsculas"
description: El parche de MDVA-39923 soluciona el problema en el que los clientes obtienen un error cuando buscan el pedido por SKU en la funcionalidad de pedido rápido B2B con un caso diferente al del caso con el que se guarda el nombre. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2. El ID del parche es MDVA-39923. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39923: la búsqueda por SKU en la funcionalidad de pedido rápido B2B distingue entre mayúsculas y minúsculas

El parche de MDVA-39923 soluciona el problema en el que los clientes obtienen un error cuando buscan el pedido por SKU en la funcionalidad de pedido rápido B2B con un caso diferente al del caso con el que se guarda el nombre. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2. El ID del parche es MDVA-39923. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.1-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La búsqueda por SKU en la funcionalidad de pedido rápido B2B distingue entre mayúsculas y minúsculas y muestra un error cuando se utiliza un caso diferente al con el que se guarda el SKU.

<u>Requisitos previos</u>:

Los módulos B2B están instalados.

<u>Pasos a seguir</u>:

1. Inicie sesión en el administrador y vaya a **Tiendas** > **Configuración** > **B2B**.
1. Habilitar **catálogo compartido** y **pedido rápido**.
1. Cree un producto con SKU en mayúsculas, por ejemplo, TEST20-1234
1. Asignar el producto creado al **catálogo compartido**.
1. Inicie sesión como cliente y haga clic en **Pedido rápido**.
1. Introduzca el SKU en minúsculas; por ejemplo, test20-1234.

<u>Resultados esperados</u>:

El producto debe encontrarse independientemente de la caja utilizada.

<u>Resultados reales</u>:

Se recibió el siguiente mensaje de error: *1 producto(s) requiere(n) su atención*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
