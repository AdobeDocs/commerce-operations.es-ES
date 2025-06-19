---
title: 'MDVA-43451: Error al configurar los precios y la estructura del catálogo compartido'
description: El parche de MDVA-43451 soluciona el problema en el que el usuario no puede establecer los precios y la estructura de un catálogo compartido. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. El ID del parche es MDVA-43451. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Catalog Management
role: Admin
exl-id: 2cddfca2-ee32-4e73-9ef6-78125fbaa13d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# MDVA-43451: Error al configurar los precios y la estructura del catálogo compartido

El parche de MDVA-43451 soluciona el problema en el que el usuario no puede establecer los precios y la estructura de un catálogo compartido. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. El ID del parche es MDVA-43451. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario no puede establecer los precios y la estructura de un catálogo compartido. Se muestra el siguiente mensaje: *No se encontró el almacén solicitado. Compruebe el almacén e inténtelo de nuevo.*

<u>Pasos a seguir</u>:

1. Crear un sitio web personalizado. Los ID de los sitios web deben ser 0, 1, 2.
1. Cree una tienda en el sitio web anterior. Los ID de las tiendas deben ser 0,1,2.
1. Cree tres vistas de tienda para la tienda de arriba. Los ID de las vistas de tienda deben ser 0, 1, 2, 3, 4.
1. Eliminar la vista de la tienda con ID 2. Ahora, la tabla de tiendas debe ser similar a la siguiente tabla.

   ```bash
   MariaDB [m24devinvb2b]> SELECT store_id,code,website_id,group_id,name FROM store;
   +----------+----------------+------------+----------+--------------------+
   | store_id | code           | website_id | group_id | name               |
   +----------+----------------+------------+----------+--------------------+
   |        0 | admin          |          0 |        0 | Admin              |
   |        1 | default        |          1 |        1 | Default Store View |
   |        3 | web1storeview2 |          2 |        2 | web1storeview2     |
   |        4 | web1storeview3 |          2 |        2 | web1storeview3     |
   +----------+----------------+------------+----------+--------------------+
   ```

1. Cree un nuevo catálogo compartido.
1. Al configurar Precio y Estructura, seleccione la tienda creada en el paso 2.
1. Guarde el catálogo compartido.

<u>Resultados esperados</u>:

El catálogo compartido se ha guardado sin problemas.

<u>Resultados reales</u>:

No puede guardar el catálogo compartido. Se muestra el siguiente error:
*No se encontró el almacén solicitado. Compruebe el almacén e inténtelo de nuevo.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
