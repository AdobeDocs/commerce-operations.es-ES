---
title: 'ACSD-63406: Las comillas persistentes caducadas no se borran cuando se ejecuta el trabajo cron persistent_clear_expire'
description: Aplique el parche ACSD-63406 para corregir el problema de Adobe Commerce en el que ningún trabajo cron borra las comillas persistentes caducadas cuando se ejecuta el trabajo cron persistent_clear_expire.
feature: Quotes, Shopping Cart
role: Admin, Developer
exl-id: 795d1ddf-0d5b-406c-870b-36cb92cf07fa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-63406: las comillas persistentes caducadas no se borran cuando se ejecuta el trabajo cron de `persistent_clear_expired`

El parche ACSD-63406 corrige el problema en el que las comillas persistentes caducadas no son borradas por ningún trabajo cron cuando se ejecuta el trabajo cron `persistent_clear_expired`. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62. El ID del parche es ACSD-63406. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.7-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Ningún trabajo cron borra las comillas persistentes caducadas cuando se ejecuta el trabajo cron `persistent_clear_expired`.

<u>Pasos a seguir</u>:

1. Cree una categoría y un producto.
1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]**.
   1. Establecer todas las opciones en *Sí*.
   1. Establezca **[!UICONTROL Persistence Lifetime (seconds)]** en *60*.
1. Cree una cuenta de cliente en la tienda e inicie sesión.
1. Añadir un producto al carro de compras.
1. Cierre la sesión, espere 60 segundos y vuelva a iniciarla.

<u>Resultados esperados</u>:

El trabajo cron `persistent_clear_expired` debe eliminar comillas persistentes en función de la configuración de duración de persistencia de la configuración.

<u>Resultados reales</u>:

El valor `is_persistent` de la cotización de cliente permanece *1* en la tabla de cotización.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
