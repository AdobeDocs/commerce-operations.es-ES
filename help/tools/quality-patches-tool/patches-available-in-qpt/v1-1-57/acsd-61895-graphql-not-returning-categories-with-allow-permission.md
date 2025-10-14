---
title: 'ACSD-61895: [!DNL GraphQL] la consulta de categorías falla en el catálogo compartido privado con vista restringida'
description: Aplique el parche ACSD-61895 para solucionar el problema de Adobe Commerce donde  [!DNL GraphQL] las respuestas de los clientes invitados (que usan un catálogo compartido público con todas las categorías permitidas) no arrojaron ninguna categoría cuando se creó un catálogo compartido privado con restricciones para las mismas categorías.
feature: Categories, GraphQL, Roles/Permissions
role: Admin, Developer
exl-id: ef986fa6-e8bc-4322-80f2-fa0c5d5e8d40
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# ACSD-61895: [!DNL GraphQL] `categories` error de consulta para catálogo compartido privado con vista restringida

El parche ACSD-61895 corrige el problema en el que las respuestas de [!DNL GraphQL] para clientes invitados (que usan un catálogo compartido público con todas las categorías permitidas) no devolvían ninguna categoría cuando se crea un catálogo compartido privado con restricciones para las mismas categorías.

Después de la corrección, devuelve todas las categorías con permisos de permiso (catálogo compartido público) para usuarios invitados, incluso si la categoría raíz no tiene permiso de permiso en el ámbito de un catálogo compartido privado.

Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. El ID del parche es ACSD-61895. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las respuestas de [!DNL GraphQL] para clientes invitados (que usan un catálogo compartido público con todas las categorías permitidas) no devuelven ninguna categoría cuando se crea un catálogo compartido privado con restricciones para las mismas categorías.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce con B2B y datos de ejemplo.
1. Asegúrese de que las funciones B2B estén habilitadas.
1. Cree dos catálogos compartidos: uno público y otro privado.

   * Catálogo compartido público:

      * Asigne todas las categorías al catálogo público.

   * Catálogo compartido privado:

      * Asigne solamente la categoría `Gear` y sus categorías secundarias al catálogo privado.
      * Asigne el catálogo privado a una empresa de prueba.

1. Crear un usuario de empresa:

   * Cree un usuario asociado a la empresa de prueba vinculado al catálogo compartido privado.
   * Asegúrese de que el usuario solo puede acceder a la categoría `Gear` y sus categorías secundarias en el front-end al iniciar sesión.

1. Categorías de consulta mediante API:

   * Use el cliente de API para ejecutar la siguiente consulta [!DNL GraphQL] sin un token de cliente:

   ```graphql
   query Categories { 
       categories { 
           items { 
               children_count 
               children { 
                   uid 
                   name 
                   children_count 
                   children { 
                   uid 
                   name 
                   } 
               } 
           } 
       } 
   }
   ```

1. Observe la respuesta y compruebe si se devuelven la categoría `Gear` y otras categorías.
1. Ahora, consulte las categorías con un token de cliente:

   * Inicie sesión como el usuario de la empresa de prueba.
   * Ejecute la misma consulta de categoría [!DNL GraphQL], pero incluya el token de cliente para el usuario que inició sesión.
   * Observe la respuesta y compruebe si solo se devuelven la categoría `Gear` y sus categorías secundarias.


<u>Resultados esperados</u>:

Al consultar como usuario invitado de la empresa, se deben devolver todas las categorías (según lo esperado).

<u>Resultados reales</u>:

La respuesta de la consulta `categories` no muestra ninguna categoría.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
