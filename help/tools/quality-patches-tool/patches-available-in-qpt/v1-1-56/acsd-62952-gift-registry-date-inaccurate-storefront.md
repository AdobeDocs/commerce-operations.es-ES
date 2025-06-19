---
title: 'ACSD-62952: la fecha del registro de regalos se muestra de forma inexacta en la tienda'
description: Aplique el parche ACSD-62952 para corregir el problema de Adobe Commerce en el que la fecha del Registro de regalos se muestra de forma inexacta en la tienda.
feature: Gift, Storefront
role: Admin, Developer
exl-id: c11e95ab-775d-4aa7-828b-29ec52685d47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-62952: la fecha del registro de regalos se muestra de forma inexacta en la tienda

El parche ACSD-62952 corrige el problema en el que la fecha del Registro de regalos se muestra de forma inexacta en la tienda. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. El ID del parche es ACSD-62952. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La fecha del evento que se muestra en la tienda de un registro de regalos compartido se muestra incorrectamente como un día antes de la fecha real.

<u>Pasos a seguir</u>:

1. Inicie sesión en el front-end como cliente.
1. En el panel [!UICONTROL My Account], haga clic en **[!UICONTROL Gift Registry]**.
1. Si no existe ningún registro, cree uno y especifique cualquier fecha.
1. Agregue cualquier elemento al carro de compras.
1. En la página del carro de compras, haga clic en **[!UICONTROL Add all items to Gift Registry]**.
1. Compartir el Registro de regalos.

<u>Resultados esperados</u>:

El Registro de regalos muestra la fecha de evento correcta.

<u>Resultados reales</u>:

El Registro de regalos abierto desde el correo electrónico de invitación muestra la fecha del evento como un día antes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura en la nube: Actualizaciones y parches > Aplicar parches en la guía de Commerce en la infraestructura en la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
