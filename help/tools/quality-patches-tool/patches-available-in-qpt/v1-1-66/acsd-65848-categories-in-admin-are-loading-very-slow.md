---
title: 'ACSD-65848: las categorías de administración se cargan muy lentamente'
description: Aplique el parche ACSD-65848 para corregir el problema de Adobe Commerce en el que el recuento total de productos en una categoría se calculó mediante una subselección, lo que retrasó el tiempo de carga de la categoría.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: 0233db9b-86b1-4320-a566-7e7e207dab84
source-git-commit: 1ccb4c1dda5141934e04509b27fdafbfdc436a15
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-65848: las categorías de administración se cargan muy lentamente

El parche ACSD-65848 corrige el problema en el que el recuento total de productos en una categoría se calculaba mediante una subselección, lo que retrasaba el tiempo de carga de la categoría. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66. El ID del parche es ACSD-65848. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La página de vista/edición de la categoría de administrador experimenta retrasos significativos al cargar. El retraso se debe al método utilizado para calcular el recuento total de productos en una categoría, que depende de una consulta de subselección. La refactorización de esta lógica para utilizar una unión en su lugar mejora el rendimiento y reduce el tiempo de carga.

<u>Pasos a seguir</u>:

1. Cree una nueva instancia de Adobe Commerce Cloud con la versión 2.4.8.
1. Crea 2.500 categorías y al menos 10.000 productos:
   1. Copie el directorio `setup/performance-toolkit` en `./var` para poder editar los perfiles.
   1. Abra el perfil `small.xml` y actualícelo para incluir 2500 categorías y 250 000 productos (que coincidan con la configuración del comerciante).
   1. Ejecute el siguiente comando para generar las sujeciones:

      ```bash
      bin/magento 
      setup:performance:generate-fixtures var/setup/performance-toolkit/profiles/ce/small.xml
      ```

1. Una vez creados los productos y las categorías, asegúrese de que todas las categorías estén configuradas como anclajes. Ejecute esta consulta SQL:

   ```sql
   UPDATE catalog_category_entity_int 
   SET value = 1 
   WHERE attribute_id = (
   SELECT attribute_id 
   FROM eav_attribute 
   WHERE attribute_code = 'is_anchor'
   );
   ```

1. En el panel Administración, cree una estructura de categorías más profunda:
   * Mueva la categoría 2 bajo la categoría 1 para anidarla más profundamente en el árbol.
1. Intente abrir una página de categoría en el panel de administración con una dirección URL como:
   ```/admin/catalog/category/edit/id/xx/```

<u>Resultados esperados</u>:

Cada página de categoría se abre en el primer intento en unos segundos.

<u>Resultados reales</u>:

Las páginas de categoría tardan más de un minuto en abrirse.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
