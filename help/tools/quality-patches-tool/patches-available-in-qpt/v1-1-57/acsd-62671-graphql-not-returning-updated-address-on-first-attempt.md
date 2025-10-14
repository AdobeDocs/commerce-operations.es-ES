---
title: 'ACSD-62671: [!DNL GraphQL] no devuelve la dirección actualizada en el primer intento'
description: Aplique el parche ACSD-62671 para corregir el problema de Adobe Commerce donde una  [!DNL GraphQL] solicitud no devuelve información de dirección actualizada en el primer intento.
feature: GraphQL
role: Admin, Developer
exl-id: afd75ad2-e801-4f8a-b68f-526ca5168413
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-62671: [!DNL GraphQL] no devuelve la dirección actualizada en el primer intento

El parche ACSD-62671 corrige el problema en el que una solicitud [!DNL GraphQL] no devuelve información de dirección actualizada en el primer intento. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) 1.1.57. El ID del parche es ACSD-62671. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al usar [!DNL GraphQL Application Server], la solicitud de dirección de cliente no devuelve los datos más recientes.

<u>Pasos a seguir</u>:

1. Instalar e iniciar [!DNL GraphQL Application Server].
1. Asegúrese de que el tipo de caché `graphQL_query_resolver_result` esté habilitado.
1. Use [!DNL GraphQL] para:

   * Crear un cliente.
   * Genere un token.
   * Utilice el token para crear varias direcciones para el cliente anterior.

1. Envíe [!DNL GraphQL] solicitud para obtener las direcciones del cliente.
1. Añadir una nueva dirección al cliente.
1. Repita la solicitud del paso #4 varias veces mientras supervisa el recuento de direcciones devueltas en la respuesta.

<u>Resultados esperados</u>:

[!DNL GraphQL] respuesta contiene el número correcto de direcciones de clientes.

<u>Resultados reales</u>:

En ocasiones, se devuelve un número incorrecto de direcciones en la respuesta [!DNL GraphQL].

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
