---
title: 'ACSD-60344: duplicar correos electrónicos de confirmación de pedido al usar [!UICONTROL Purchase Order] con aprobación automática'
description: Aplique el parche ACSD-60344 para corregir el problema de Adobe Commerce en el que se envían correos electrónicos de confirmación de pedidos duplicados al utilizar [!UICONTROL Purchase Order] con aprobación automática.
feature: Purchase Orders
role: Admin, Developer
source-git-commit: afa03b31e4af0be1ebc0d12aabd4f9d8be17d1fe
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# ACSD-60344: duplicar correos electrónicos de confirmación de pedido al usar *[!UICONTROL Purchase Order]* con aprobación automática

El parche ACSD-60344 corrige el problema por el que se envían correos electrónicos de confirmación de pedidos duplicados al usar un *[!UICONTROL Purchase Order]* con aprobación automática. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. El ID del parche es ACSD-60344. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6-p4

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se envían correos electrónicos de confirmación de pedido duplicados al usar *[!UICONTROL Purchase Order]* con aprobación automática.

<u>Requisitos previos</u>

Habilitar módulos B2B y *[!UICONTROL Purchase Order]*.

<u>Pasos a seguir</u>:

1. Cree una cuenta de compañía y habilite *[!UICONTROL Purchase Order]* para ella.
1. Cree una cuenta de usuario normal y añádala a la cuenta de la empresa como usuario de la empresa.
1. Realice un pedido con esta cuenta.
1. Ejecute cron y compruebe los correos electrónicos.

<u>Resultados esperados</u>:

Solo se recibe un correo electrónico de confirmación de pedido por pedido.

<u>Resultados reales</u>:

Se reciben dos correos electrónicos de confirmación de pedido.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
