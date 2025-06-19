---
title: 'ACSD-56741: solución de problemas de configuración de bases de datos con déclencheur MySQL personalizados'
description: Aplique el parche ACSD-56741 para corregir el problema de Adobe Commerce donde aparece un mensaje de error *Intentando acceder al desplazamiento de la matriz en el valor de tipo null* durante setup:upgrade debido a un déclencheur MySQL personalizado en la base de datos no relacionado con la indexación y  [!DNL MView].
feature: Install
role: Admin, Developer
exl-id: 93a1c75f-8a45-49df-9fa4-6ba1234c822d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-56741: solución de problemas de configuración de bases de datos con déclencheur MySQL personalizados

La revisión ACSD-56741 corrige el problema en el que aparece un mensaje de error *Intentando obtener acceso al desplazamiento de la matriz en un valor de tipo null* durante `setup:upgrade` debido a un déclencheur MySQL personalizado en la base de datos no relacionado con la indexación y [!DNL MView]. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48. El ID del parche es ACSD-56741. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.5.0

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Aparece un mensaje de error *Al intentar obtener acceso al desplazamiento de la matriz en un valor de tipo null* durante `setup:upgrade` debido a un déclencheur MySQL personalizado en la base de datos no relacionado con la indexación y [!DNL MView].

<u>Pasos a seguir</u>:

1. Ejecutar `php bin/magento indexer:set-mode schedule`.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. Ejecutar `php bin/magento c:f`.
1. Ejecutar `php bin/magento setup:upgrade`.

<u>Resultados esperados</u>:

La actualización de la instalación finaliza sin ningún error.

<u>Resultados reales</u>:

La actualización de la instalación se cierra con un mensaje de error:

*Advertencia: se está intentando obtener acceso al desplazamiento de matriz en un valor de tipo null*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
