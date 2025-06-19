---
title: 'ACSD-60804: La edición de un cliente asociado con una empresa eliminada provoca un error'
description: Aplique el parche ACSD-60804 para solucionar el problema de Adobe Commerce en el que la edición de un cliente asociado con una empresa eliminada provoca un error *La llamada a una función de miembro getSuperUserId() es nula*.
feature: Companies, Customers, B2B
role: Admin, Developer
exl-id: 09241160-f5ed-41f8-8bb6-2bb8ed5cccd5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-60804: La edición de un cliente asociado con una empresa eliminada provoca un error

El parche ACSD-60804 corrige el problema en el que al editar un cliente asociado con una compañía eliminada se produce un error *La llamada a una función de miembro getSuperUserId() se produce en null*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53. El ID del parche es ACSD-60804. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La edición de un cliente asociado con una compañía eliminada causa un error *Llamada a una función de miembro getSuperUserId() en null*.

<u>Requisitos previos:</u>:

Instale y habilite los módulos B2B de Adobe Commerce.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Settings]** > **[!UICONTROL B2B]** > **[!UICONTROL Enable Company]**.
1. Vaya a **[!UICONTROL Customers]** > **[!UICONTROL Company]** > **[!UICONTROL Create New Company]**.
1. Inicie sesión en `mysql` para la instancia.
1. Elimine la compañía donde `entity_id` = *1*.
1. Ir a **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.
1. Edite el cliente que se creó automáticamente cuando creó la compañía.

<u>Resultados esperados</u>:

El cliente se edita sin que se produzca un error de excepción.

<u>Resultados reales</u>:

Se produce un error: *Llame a una función miembro getSuperUserId() en null* si ninguna compañía está asociada con el cliente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
