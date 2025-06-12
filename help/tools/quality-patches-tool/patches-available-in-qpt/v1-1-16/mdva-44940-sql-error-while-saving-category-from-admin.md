---
title: 'MDVA-44940: Error SQL al guardar la categoría del administrador'
description: El parche MDVA-44940 corrige el problema en el que se produce un error SQL al guardar una categoría del administrador. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16. El ID del parche es MDVA-44940. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
feature: Admin Workspace, Categories, Sales Channels
role: Admin
exl-id: de4384f1-a75d-4726-810f-6560a7c57b82
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-44940: Error SQL al guardar la categoría del administrador

El parche MDVA-44940 corrige el problema en el que se produce un error SQL al guardar una categoría del administrador. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16. El ID del parche es MDVA-44940. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error de SQL al guardar una categoría del administrador.

<u>Pasos a seguir</u>:

1. Instalar datos de ejemplo.
1. Cree un segundo sitio web con un grupo de tienda asignado a la categoría predeterminada.

   * Crear una vista de tienda asignada al nuevo grupo de tiendas.

1. Crear stock y un origen adicional asignado a este stock y un canal de ventas asignado al segundo sitio web.
1. Cree un producto de prueba asignado al segundo sitio web.
1. Vaya a **Administración** > **Catálogo** > **Categorías**, seleccione **Ámbito** = **Segundo sitio web** y vaya a **Productos en la categoría** > **Clasificación automática** > Mueva los productos sin existencias a la parte inferior y haga clic en **Guardar**.

<u>Resultados esperados</u>:

Se guardará la categoría.

<u>Resultados reales</u>:

Se produjo el siguiente error: *Se produjo un error al guardar la categoría*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
