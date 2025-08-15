---
title: 'MDVA-31590: No se pueden actualizar atributos por lotes mediante colas asíncronas de MySQL'
description: El parche MDVA-31590 resuelve el problema en el que los usuarios no pueden actualizar los atributos de forma masiva mediante colas asincrónicas de MySQL. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3. El ID del parche es MDVA-31590. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.
feature: Attributes, Services
role: Admin
exl-id: f8d1c3bd-e995-41ef-89e1-93eec6e8b1f1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# MDVA-31590: No se pueden actualizar atributos por lotes mediante colas asíncronas de MySQL

El parche MDVA-31590 resuelve el problema en el que los usuarios no pueden actualizar los atributos de forma masiva mediante colas asincrónicas de MySQL. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3. El ID del parche es MDVA-31590. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.2.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0-2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios no pueden actualizar los atributos de forma masiva mediante MySQL asincrónico.

<u>Pasos a seguir</u>:

1. En la cuadrícula de productos del servidor, realice una acción masiva para actualizar los valores de atributo de algunos productos.
   * Compruebe los productos y seleccione **Actualizar atributos** en la lista desplegable Acciones.
1. Establezca valores para los atributos necesarios, asigne productos a sitios web y guárdelos.
1. Una vez que la página se vuelve a cargar, muestra un mensaje como el siguiente:
   *Tarea &quot;Actualizar atributos para N productos seleccionados&quot;: 1 artículo(s) se ha(n) programado para una actualización.*
1. Espere unos segundos y vuelva a cargar la página back-end.

<u>Resultados esperados</u>:

1. La página muestra un mensaje de actualización correcto como: *1 elemento(s) se ha(n) actualizado(s) correctamente.*
1. Se actualizan los valores de atributo de los productos relacionados.
1. En la base de datos, se crean nuevos registros tanto en la tabla `magento_bulk` como en la tabla `magento_operation` (operaciones relacionadas con la carga masiva).
1. Se crean nuevos registros en la tabla `queue_message` (relacionados con las colas `product_action_attribute.update` o `product_action_attribute.website.update`).
1. La tabla `queue_message_status` tiene registros con el estado &quot;4&quot;.
1. NO hay errores en `system.log`.

<u>Resultados reales</u>:

1. La página sigue mostrando un mensaje como el siguiente:
   *Tarea &quot;Actualizar atributos para N productos seleccionados&quot;: 1 artículo(s) se ha(n) programado para una actualización.*
1. Se actualizan los valores de atributo de los productos.
1. Se crea un nuevo registro en la tabla `message_bulk`, pero no hay ningún registro relacionado en la tabla `magento_operation`.
1. Se crean registros nuevos en `queue_message` y `queue_message_status` tablas.
1. La tabla `queue_message_status` tiene un registro con estado de error (valor de estado &quot;6&quot;).
1. `system.log` contiene un error similar al siguiente:

   ```sql
   *main.CRITICAL: Message has been rejected: SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'operation_key' cannot be null, query was: INSERT INTO {{magento_operation}} ({{id}}, {{bulk_uuid}}, {{topic_name}}, {{serialized_data}}, {{result_serialized_data}}, {{status}}, {{error_code}}, {{result_message}}, {{operation_key}}) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?) [] []*
   ```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
