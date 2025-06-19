---
title: 'ACSD-47179: la eliminación masiva de críticas de productos no funciona cuando se inicia sesión como función de usuario limitada'
description: Aplique el parche ACSD-47179 para corregir el problema de Adobe Commerce en el que la eliminación masiva de revisiones de productos no funciona cuando se inicia sesión como una función de usuario limitada.
feature: Marketing Tools, Products, Roles/Permissions
role: Admin
exl-id: 7131ee47-fadc-4e93-b8b2-5b2e0521ad97
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-47179: la eliminación masiva de críticas de productos no funciona cuando se inicia sesión como una función de usuario limitada

El parche ACSD-47179 corrige el problema en el que la eliminación masiva de revisiones de productos no funciona cuando se inicia sesión como una función de usuario limitada. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.23. El ID del parche es ACSD-47179. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La eliminación masiva de críticas de productos no funciona cuando se inicia sesión como una función de usuario limitada.

<u>Pasos a seguir</u>:

1. Crear un sitio web secundario.
1. Cree una función de usuario restringida al sitio web secundario con pleno permiso para las siguientes secciones:
   * Catálogo
   * Cliente
   * Marketing
1. Cree un producto y asígnelo al sitio web secundario.
1. Agregue dos críticas al producto desde el front-end.
1. Inicie sesión en el administrador de [!DNL Commerce] con el usuario administrador restringido que acaba de crear.
1. Intente eliminar de forma masiva las revisiones pendientes.

<u>Resultados esperados</u>:

Un administrador con permisos suficientes puede eliminar de forma masiva las revisiones pendientes.

<u>Resultados reales</u>:

Recibió el siguiente error: _Se produjo un error. Excepción generada en support_report.log_

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
