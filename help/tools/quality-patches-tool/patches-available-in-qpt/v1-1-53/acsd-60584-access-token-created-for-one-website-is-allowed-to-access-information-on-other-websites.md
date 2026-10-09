---
title: 'ACSD-60584: el token de acceso creado para un sitio web permite acceder a la información de otros sitios web'
description: Aplique el parche ACSD-60584 para solucionar el problema en el que el token de acceso creado para el usuario en un sitio web puede acceder o cambiar la información del cliente en otros sitios web.
feature: Customers, GraphQL
role: Admin, Developer
exl-id: ea30ba92-4b7b-44f9-a1b1-97946061d9e6
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
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
source-wordcount: '463'
ht-degree: 0%
---
# ACSD-60584: el token de acceso creado para un sitio web permite acceder a la información de otros sitios web

El parche ACSD-60584 soluciona el problema que supone que el token de acceso creado para el usuario en un sitio web puede acceder o cambiar la información del cliente en otros sitios web. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=es) 1.1.53. El ID del parche es ACSD-60584. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5 - 2.4.6-p8

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El token de API creado para el usuario en un sitio web le permite acceder a la información del cliente, crear un carro de compras y agregar productos al carro de compras en otras vistas de sitios web.

<u>Pasos a seguir</u>:

1. Asegúrese de que **[!DNL Share Customer Accounts configuration]** esté establecido en **[!UICONTROL Per Website]**.
1. Crear *sitio web*, *tienda* y *vista de tienda* adicionales.
1. Cree dos clientes con el mismo correo electrónico en el *sitio web* principal y en el *sitio web* del paso anterior.
1. Generar un token de cliente mediante [!DNL GraphQL] en el sitio web principal.
1. Utilizando el token generado, envíe una consulta al cliente **[!DNL GraphQL]** con el segundo sitio web en el encabezado para recuperar la información del cliente.
1. Observe el resultado devuelto.

<u>Resultados esperados</u>:

Se ha devuelto la información del cliente del *sitio web* principal porque el token del *sitio web* principal se usa en la consulta [!DNL GraphQL].

<u>Resultados reales</u>:

Se devuelve la información del cliente del segundo sitio web.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
