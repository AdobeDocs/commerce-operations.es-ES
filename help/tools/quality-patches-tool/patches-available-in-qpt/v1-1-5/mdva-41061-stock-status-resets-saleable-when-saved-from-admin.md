---
title: 'MDVA-41061: El estado de las existencias se restablece como vendible cuando el producto se guarda desde el administrador'
description: El parche MDVA-41061 corrige el problema en el que el estado de las existencias se restablece como comercializable cuando el producto se guarda desde el administrador. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. El ID del parche es MDVA-41061. La última versión del parche está disponible en QPT 1.1.15 con ID de parche MDVA-41061-V3. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.4.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: ddbc30ef-bc88-4878-8bd8-6880823819a2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# MDVA-41061: El estado de las existencias se restablece como vendible cuando el producto se guarda desde el administrador

El parche MDVA-41061 corrige el problema en el que el estado de las existencias se restablece como comercializable cuando el producto se guarda desde el administrador. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. El ID del parche es MDVA-41061. La última versión del parche está disponible en QPT 1.1.15 con ID de parche MDVA-41061-V3. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.2-p2, 2.4.3 - 2.4.3-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El estado de stock se restablece como comercializable cuando el producto se guarda desde el administrador.

<u>Requisitos previos</u>:

Módulos de inventario instalados.

<u>Pasos a seguir</u>:

1. Cree un producto simple con Cantidad = 1.
1. Realice un pedido utilizando el producto creado en el paso 1.
1. Ejecutar cron: asegúrese de que se ejecuta la cola `inventory.reservations.updateSalabilityStatus` y de que el estado de las existencias del producto se ha cambiado a cero en la tabla `cataloginventory_stock_status`.
1. Compruebe el producto en el front-end. Debe marcarse como **Agotado**.
1. Guarde el producto en Admin sin ningún cambio.

<u>Resultados esperados</u>:

* El estado de las existencias no debe actualizarse.
* El producto debería estar **Agotado** en el front-end.

<u>Resultados reales</u>:

* El producto simple está marcado como **En existencia** en el front-end.
* Los usuarios reciben *El mensaje de cantidad solicitada no está disponible* al intentar agregarlo al carro de compras.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
