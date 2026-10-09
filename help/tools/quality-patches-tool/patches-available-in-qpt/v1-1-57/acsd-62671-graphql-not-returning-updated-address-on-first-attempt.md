---
title: 'ACSD-62671: [!DNL GraphQL] no devuelve la dirección actualizada en el primer intento'
description: Aplique el parche ACSD-62671 para corregir el problema de Adobe Commerce en el que una solicitud [!DNL GraphQL] no devuelve información de dirección actualizada en el primer intento.
feature: GraphQL
role: Admin, Developer
exl-id: afd75ad2-e801-4f8a-b68f-526ca5168413
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%
---
# ACSD-62671: [!DNL GraphQL] no devuelve la dirección actualizada en el primer intento

El parche ACSD-62671 corrige el problema en el que una solicitud [!DNL GraphQL] no devuelve información de dirección actualizada en el primer intento. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57. El ID del parche es ACSD-62671. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
