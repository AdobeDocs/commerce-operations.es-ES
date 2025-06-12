---
title: 'ACSD-59952: Error al eliminar el catálogo compartido con el mismo ID de grupo que otro catálogo compartido'
description: Aplique el parche ACSD-59952 para solucionar el problema de Adobe Commerce en el que se produce un error al eliminar un catálogo compartido con el mismo customer_group_id que otro catálogo compartido.
feature: B2B, REST
role: Admin, Developer
exl-id: 11cba2e6-dd62-4063-a38c-b98ea70a72e9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-59952: Error al eliminar el catálogo compartido con el mismo ID de grupo que otro catálogo compartido

La revisión ACSD-59952 corrige el error producido al eliminar catálogos compartidos con el mismo `customer_group_id` que otro catálogo compartido. Además, evita que los usuarios creen este tipo de catálogos compartidos. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52. El ID del parche es ACSD-59952. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

No se puede crear un nuevo catálogo compartido con el mismo `customer_group_id` que otro catálogo compartido. Sin embargo, al hacerlo, al intentar eliminar el catálogo compartido con el mismo `customer_group_id`, se genera un error.

<u>Requisitos previos</u>:

Instale los módulos B2B de Adobe Commerce.

<u>Pasos a seguir</u>:

1. Cree varios catálogos compartidos asignados al mismo `customer_group_id` mediante la siguiente llamada de API REST:

   ```REST
   {
       "sharedCatalog": {
           "name": "test1",
           "description": "test",
           "customer_group_id": 1,
           "type": 0,
           "created_at": "03:11:00",
           "created_by": 1,
           "store_id": 0,
           "tax_class_id": 3
       }
   }
   ```

1. Intente eliminar cualquiera de los catálogos compartidos mediante la siguiente llamada de API de REST:

   ```REST
   /rest/default/V1/sharedCatalog/4
   ```

<u>Resultados esperados</u>:

* No es posible crear varios catálogos compartidos asignados al mismo `customer_group_id`.
* El catálogo compartido en el caso anterior se ha eliminado correctamente.

<u>Resultados reales</u>:

* Es posible crear varios catálogos compartidos asignados al mismo `customer_group_id`.
* Se devolvió el siguiente error al intentar eliminar el catálogo compartido con el mismo `customer_group_id`: *No se puede eliminar el catálogo compartido*.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en nuestra base de conocimiento de soporte.
* [Comprueba si el parche está disponible para tu problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en nuestra base de conocimiento de soporte.

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
