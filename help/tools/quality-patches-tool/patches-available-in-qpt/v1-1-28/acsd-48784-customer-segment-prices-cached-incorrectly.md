---
title: 'ACSD-48784: precios de segmentos de clientes almacenados en caché incorrectamente entre grupos de clientes'
description: Aplique el parche ACSD-48784 para corregir el problema de Adobe Commerce en el que los precios de los segmentos del cliente se almacenan incorrectamente en caché entre grupos de clientes.
feature: Admin Workspace, Cache, Customer Service, Orders
role: Admin
exl-id: a691c61c-fdba-4d6a-8314-095dfb0ba4a1
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-48784: precios de segmentos de clientes almacenados en caché incorrectamente entre grupos de clientes

El parche ACSD-48784 corrige el problema de que los precios de los segmentos de los clientes se almacenan incorrectamente en caché entre grupos de clientes. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28. El ID del parche es ACSD-48784. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los precios de los segmentos del cliente se almacenan incorrectamente en caché entre grupos de clientes.

<u>Requisitos previos</u>:

Configure [!DNL Varnish] o [!DNL Fastly].

<u>Pasos a seguir</u>:

1. Habilite el almacenamiento en caché de páginas completas en su tienda.
1. Inicie sesión en el sitio como usuario con precios especiales para grupos de clientes.
1. Vaya a una página de producto para un producto con precios especiales para grupos de clientes. Observe el *precio especial*.
1. En un explorador independiente, abra la misma página de producto que un usuario invitado sin iniciar sesión. Observe el precio normal.
1. Acceda a la interfaz administrativa de Adobe Commerce y borre la caché de Adobe Commerce y [!DNL Fastly] de este almacén.
1. En el explorador que inició sesión, quite la cookie `X-Magento-Vary`.
1. En el explorador que ha iniciado sesión, vuelva a cargar la misma página de producto varias veces hasta que el almacenamiento en caché se vacíe por completo.
1. En el explorador sin sesión iniciada, vuelva a cargar la página del producto para ver los precios del grupo de clientes.

<u>Resultados esperados</u>:

La página de productos muestra el precio correcto para grupos de clientes específicos.

<u>Resultados reales</u>:

* Los usuarios invitados ven el precio especial de usuario que ha iniciado sesión.
* El minicarrito muestra el precio correcto una vez que se le agrega el producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
