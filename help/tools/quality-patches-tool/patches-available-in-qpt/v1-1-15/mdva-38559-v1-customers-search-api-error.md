---
title: 'MDVA-38559: /V1/customers/search API devuelve un error'
description: El parche MDVA-38559 soluciona el problema en el que la API /V1/customers/search devuelve un error para los clientes que tienen más de una suscripción. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.15. El ID del parche es MDVA-38559. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.3.
feature: REST, Search
role: Admin
exl-id: 6bcb65d0-1389-4090-b53c-8048bf64d8fb
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%
---
# MDVA-38559: /V1/customers/search API devuelve un error

La revisión MDVA-38559 corrige el problema en el cual la API `/V1/customers/search` devuelve un error para los clientes que tienen más de una suscripción. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.15. El ID del parche es MDVA-38559. Tenga en cuenta que el problema se corrige en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La API `/V1/customers/search` devuelve un error para los clientes con más de una suscripción.

<u>Requisitos previos</u>:

La tienda Adobe Commerce utiliza más de un sitio web.

<u>Pasos a seguir</u>:

1. Vaya a **Tienda** > **Configuración** > **Cliente** > **Configuración del cliente** > **Opciones para compartir cuentas** y seleccione **Global**.
1. Vaya a **Clientes** > **Todos los clientes**, seleccione **Editar** en cualquier cliente y luego seleccione **Boletín**.
1. Suscríbase a una newsletter de más de un sitio web y guarde al cliente.
1. Envíe la siguiente solicitud:

```REST API
V1/customers/search?searchCriteria[filterGroups][0][filters][0][field]=email&searchCriteria[filterGroups][0][filters][0][value]=test@example.com&searchCriteria[filterGroups][0][filters][0][conditionType]=eq
```

<u>Resultados esperados</u>:

Se muestran los resultados de búsqueda del cliente.

<u>Resultados reales</u>:

El siguiente error se registró en exception.log: *Ya existe un elemento (Magento\Customer\Model\Customer\Interceptor) con el mismo identificador &quot;1&quot;.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
