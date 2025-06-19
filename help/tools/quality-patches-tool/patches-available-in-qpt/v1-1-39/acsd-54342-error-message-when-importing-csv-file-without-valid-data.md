---
title: 'ACSD-54342: Mensaje de error al importar el archivo CSV sin datos válidos'
description: Aplique el parche ACSD-54342 para solucionar el problema de Adobe Commerce donde se produce un mensaje de error incorrecto al importar un archivo CSV sin datos válidos.
feature: Roles/Permissions
role: Admin, Developer
exl-id: 34324a18-45af-462b-a6e6-6b6a02d4d331
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-54342: Mensaje de error al importar el archivo CSV sin datos válidos

El parche ACSD-54342 corrige el problema en el que se produce un mensaje de error incorrecto al importar un archivo CSV sin datos válidos. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.39. El ID del parche es ACSD-54342. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un mensaje de error incorrecto al importar un archivo CSV sin datos válidos.

<u>Pasos a seguir</u>:

1. Cree un archivo de importación con solo datos no válidos (Ejemplos: [!DNL SKUs] que no existen, campos de dirección de cliente no válidos o direcciones de correo electrónico de cliente mal escritas).
1. Importe el archivo seleccionando para omitir los errores de validación.

<u>Resultados esperados</u>:

La validación falla con `There are no valid rows to import` mensaje.

<u>Resultados reales</u>:

La validación se aprueba, pero la importación falla con el mensaje `Error in data structure: values are mixed`.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
