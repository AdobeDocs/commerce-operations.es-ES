---
title: 'ACSD-61785: la actualización del atributo premio_advertencia_notificación no es posible mediante la mutación de GraphQL y las llamadas a la API REST'
description: Aplique el parche ACSD-61785 para solucionar el problema de Adobe Commerce donde la actualización del atributo "premio_advertencia_notificación" no es posible mediante la mutación de GraphQL y las llamadas a la API REST.
feature: REST, GraphQL, Rewards
role: Admin, Developer
exl-id: 41f40452-4240-4b4a-b1bc-0da23139f19f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61785: la actualización del atributo premio_advertencia_notificación no es posible mediante la mutación de GraphQL y las llamadas a la API REST

El parche ACSD-61785 corrige el problema en el cual la actualización del atributo `reward_warning_notification` no es posible mediante la mutación de GraphQL y las llamadas a la API REST. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. El ID del parche es ACSD-61785. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.7-p2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No es posible actualizar el atributo `reward_warning_notification` mediante la mutación de GraphQL y las llamadas a la API REST.

<u>Pasos a seguir</u>:

1. Consulte el esquema/documentación de la API de GraphQL y REST para *Suscribirse a las actualizaciones de saldo* y *Suscribirse a las notificaciones de caducidad de puntos*.

<u>Resultados esperados</u>:

Es posible suscribirse a *Actualizaciones de saldo de recompensas* y a *Notificaciones de caducidad de puntos* mediante GraphQL y la API de REST.

<u>Resultados reales</u>:

GraphQL y la API de REST carecen de esta funcionalidad.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
