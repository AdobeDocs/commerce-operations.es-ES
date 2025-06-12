---
title: 'ACSD-45754: puntos de recompensa no añadidos después de aplicar un cupón al carro de compras'
description: El parche ACSD-45754 resuelve el problema en el que no se añaden puntos de recompensa después de aplicar un cupón al carro de compras. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18. El ID del parche es ACSD-45754. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
feature: Orders, Rewards, Shopping Cart
role: Admin
exl-id: 02f3bfc4-440b-4d77-adf5-0824d1b21073
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# ACSD-45754: puntos de recompensa no añadidos después de aplicar un cupón al carro de compras

El parche ACSD-45754 resuelve el problema en el que no se añaden puntos de recompensa después de aplicar un cupón al carro de compras. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18. El ID del parche es ACSD-45754. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.1 - 2.4.5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los puntos de recompensa no se añaden después de aplicar un cupón al carro de compras.

<u>Requisitos previos</u>:

El método de pago de PayPal está configurado.

<u>Pasos a seguir</u>:

1. Para crear tasas de cambio de puntos de recompensa, ve a **Tienda** > **Otras configuraciones** > **Tasas de cambio de recompensas**.
1. Cree una regla de precio de carro de compras con un código de cupón para aplicar 100 puntos de recompensa a los clientes que iniciaron sesión.
1. Descubre un producto como cliente conectado con PayPal y el código de cupón.
1. Consulte el historial de puntos de recompensa en la cuenta de cliente en el administrador.

<u>Resultados esperados</u>:

Los puntos de recompensa se añaden al cliente según la regla de precio.

<u>Resultados reales</u>:

No se añaden puntos de recompensa al cliente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
