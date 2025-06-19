---
title: 'ACSD-51528: Diferentes comportamientos en el formato snake_case'
description: Aplique el parche ACSD-51528 para corregir el problema de Adobe Commerce donde haya diferentes comportamientos en el formato snake_case.
feature: Variables
role: Admin
exl-id: 5f2add4b-8209-47a7-bfbd-cc434a050f0f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-51528: Diferentes comportamientos en el formato snake_case

El parche ACSD-51528 corrige diferentes comportamientos en el formato snake_case. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.32. El ID del parche es ACSD-51528. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los diferentes comportamientos sobre el formato snake_case.

<u>Pasos a seguir</u>:

1. Pruebe la función `\Magento\Framework\Api\DataObjectHelper::populateWithArray` con distintos nombres de propiedades.
1. Las propiedades con nombres como *NewPName* deben transformarse en *new_p_name*; en cambio, se están transformando en *new_pname*.
1. Además, al usar la función *getNewPName* en el objeto, se devolverá *null* porque el *modelo abstracto* transformará correctamente la llamada a *new_p_name*, por lo que ambas funciones serán incompatibles entre sí.

<u>Resultados esperados</u>

La función **[!UICONTROL populateWithArray]** debe transformar correctamente las propiedades del objeto a snake_case, de modo que sea compatible con **[!DNL AbstractModel's]** `Getters` y `Setters`.

<u>Resultados reales</u>

Al utilizar la función **[!UICONTROL populateWithArray]**, cualquier propiedad de objeto que contenga dos o más mayúsculas en una fila en su nombre hará que la transformación snake_case sea incorrecta en la matriz de datos final.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
