---
title: 'MDVA-44703: Los totales de pedidos en el informe Pedidos se calculan de forma incorrecta'
description: El parche MDVA-44703 corrige el problema en el que los totales de pedidos del informe Pedidos se calculan de forma incorrecta para el usuario administrador restringido. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16. El ID del parche es MDVA-44703. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
feature: Orders
role: Admin
exl-id: bdd38ba6-f282-4026-8f65-b76543859123
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44703: Los totales de pedidos en el informe Pedidos se calculan de forma incorrecta

El parche MDVA-44703 corrige el problema en el que los totales de pedidos del informe Pedidos se calculan de forma incorrecta para el usuario administrador restringido. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16. El ID del parche es MDVA-44703. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los totales de pedidos del informe Pedidos se calculan de forma incorrecta para el usuario administrador restringido.

<u>Pasos a seguir</u>:

1. Cree un sitio web adicional con dos tiendas.
1. Cree un usuario administrador restringido con acceso solo al nuevo sitio web.
1. Inicie sesión como usuario administrador restringido.
1. Cree dos pedidos con totales diferentes, uno para cada tienda nueva.
1. Cree facturas para los pedidos.
1. Vaya a **Informes** > **Ventas** y abra **Informe de pedidos**.
1. Actualizar estadísticas.
1. Consulte el informe de cada tienda.

<u>Resultados esperados</u>:

Los totales de ventas corresponden al importe del pedido de cada tienda.

<u>Resultados reales</u>:

Se muestra el total de ventas agregado de todo el sitio web de cada tienda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
