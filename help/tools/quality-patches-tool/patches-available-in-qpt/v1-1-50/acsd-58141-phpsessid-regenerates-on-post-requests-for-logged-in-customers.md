---
title: 'ACSD-58141: PHPSESSID se regenera en solicitudes POST para clientes que iniciaron sesión con la caché de L2 Redis habilitada'
description: Aplique el parche ACSD-58141 para corregir el problema de Adobe Commerce en el que PHPSESSID se regenera en solicitudes POST en el área de Storefront para un cliente que ha iniciado sesión con la caché de L2 Redis habilitada y el cliente se actualiza desde Administración.
feature: Customers, Cache
role: Admin, Developer
exl-id: c188c215-204c-489f-8703-4c81ca8703b7
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '474'
ht-degree: 0%
---
# ACSD-58141: PHPSESSID se regenera en [!DNL POST] solicitudes para clientes que han iniciado sesión si la caché de L2 Redis está habilitada

El parche ACSD-58141 corrige el problema en el cual `PHPSESSID` se regenera en [!DNL POST] solicitudes para un cliente que ha iniciado sesión si la caché de L2 Redis está habilitada y el cliente se actualiza desde Administración. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.50. El ID del parche es ACSD-58141. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6

**Compatible con versiones de Adobe Commerce y Magento Open Source:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

`PHPSESSID` se regenera en [!DNL POST] solicitudes de un cliente que ha iniciado sesión con la caché de L2 Redis habilitada.

<u>Requisitos previos</u>

El entorno debe configurarse con Redis que tenga al menos 3 nodos.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo.
1. Cree un cliente e inicie sesión en la Tienda.
1. Compruebe el valor de `PHPSESSID`.
1. Envíe algunas [!DNL POST] solicitudes (por ejemplo, agregar un producto al carro de compras) y vea que `PHPSESSID` sigue siendo el mismo).
1. Inicie sesión en el panel **[!UICONTROL Admin]** y cambie el segundo nombre del cliente.
1. Cuando se guarde el segundo nombre, cámbielo y guárdelo de nuevo varias veces.
1. En la tienda, envíe una solicitud [!DNL POST]. `PHPSESSID` debería haberse actualizado.
1. En la tienda, envía otra solicitud [!DNL POST] y marca `PHPSESSID`.
1. Repita el paso anterior varias veces.

<u>Resultados esperados</u>

`PHPSESSID` se regenera solo una vez después de cambiar los datos del cliente.

<u>Resultados reales</u>:

`PHPSESSID` se regenera cada vez que se envían las [!DNL POST] solicitudes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
