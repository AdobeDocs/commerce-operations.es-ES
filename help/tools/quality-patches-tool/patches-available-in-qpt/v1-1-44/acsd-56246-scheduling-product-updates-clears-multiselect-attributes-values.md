---
title: 'ACSD-56246: al programar actualizaciones de productos, se borran los valores de atributos multiselect'
description: Aplique el parche ACSD-56246 para corregir el problema de Adobe Commerce donde la programación de actualizaciones de productos borra los valores de atributos de selección múltiple.
feature: Products, Attributes, Staging
role: Admin, Developer
exl-id: 1751a03d-2610-423f-be2f-b9d060452904
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-56246: al programar actualizaciones de productos se borran los valores de atributos de selección múltiple

El parche ACSD-56246 corrige el problema en el que la programación de actualizaciones de productos borra los valores de atributos de selección múltiple. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.44. El ID del parche es ACSD-56246. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las actualizaciones de productos programadas borran los valores de atributos multiselect.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce.
1. Vaya a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** y cree el atributo siguiente:

   * Etiqueta predeterminada: Programa
   * Tipo de entrada de catálogo para el propietario de la tienda: Selección múltiple
   * Administrar opciones (valores de su atributo): Choice, Sunscape, Safetyshield
   * Código de atributo: customer_program
   * Ámbito: Global
   * Agregar a opciones de columna: No
   * Uso en las opciones de filtro: no
   * Propiedades de tienda
   * Posición: *333*
   * Permitir etiquetas de HTML en tienda: No

1. Ejecutar
   `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Ejecutar
   `bin/magento setup:upgrade`.
1. Vaya a **[!UICONTROL Admin]** > Seleccionar cualquier producto simple > Seleccionar todos los elementos en el atributo del programa > Haga clic en **[!UICONTROL Save the product]**.
1. Programe una actualización para este producto en el siguiente minuto y ejecute el siguiente comando para que el ensayo de contenido funcione:
   `for i in {1..100}; do bin/magento cron:run; done`.

<u>Resultados esperados</u>:

El atributo **[!UICONTROL program]** del producto no debe cambiar.

<u>Resultados reales</u>:

Se ha borrado el atributo **[!UICONTROL program]** del producto.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
