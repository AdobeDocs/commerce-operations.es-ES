---
title: 'ACSD-48318: error de anidación de emulación de entorno en "system.log"'
description: Aplique el parche ACSD-48318 para corregir el problema de Adobe Commerce donde aparece un mensaje de error *main.ERROR:No se permite el anidamiento de emulación de entorno* en "system.log" cada vez que se envía un correo electrónico de factura.
feature: System, Orders
role: Admin, Developer
exl-id: 24af18de-80dd-4e0a-bdf9-5b9c075fc608
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-48318: error de anidación de emulación de entorno en `system.log`

El parche ACSD-48318 corrige el problema en el que no se permite anidar un mensaje de error *main.ERROR:Environment emulation nesting is not allowed* aparece en `system.log` cada vez que se envía un correo electrónico de factura. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53. El ID del parche es ACSD-48318. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El mensaje de error *No se permite anidar la emulación del entorno* aparece en `system.log` cada vez que se envía un mensaje de correo electrónico de factura.

<u>Pasos a seguir</u>:

1. Realice un pedido y genere una factura.
1. Abra la factura desde el administrador y haga clic en **[!UICONTROL Send Email]**.
1. Siga el mismo paso para *nota de crédito* y *envío* haciendo clic en **[!UICONTROL Send Email]**.

<u>Resultados esperados</u>:

No hay errores en `system.log`.

<u>Resultados reales</u>:

`system.log` está inundado con *main.ERROR: no se permite anidar la emulación del entorno* error.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

[[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
