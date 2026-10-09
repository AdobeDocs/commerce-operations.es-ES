---
title: 'MDVA-37364: atributo de cliente personalizado de tipo de fecha rompe la IU de la cuadrícula'
description: El parche MDVA-37364 resuelve el problema en el que el atributo de cliente personalizado de tipo de fecha rompe la interfaz de usuario de la cuadrícula del cliente. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. El ID del parche es MDVA-37364. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.4 de Adobe Commerce.
feature: Attributes, Cache
role: Developer
exl-id: 5bd64004-06c4-49fd-8e56-e2c44008ca82
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%
---
# MDVA-37364: atributo de cliente personalizado de tipo de fecha rompe la IU de la cuadrícula

El parche MDVA-37364 resuelve el problema en el que el atributo de cliente personalizado de tipo de fecha rompe la interfaz de usuario de la cuadrícula del cliente. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2. El ID del parche es MDVA-37364. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.4 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0-2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El atributo de cliente personalizado del tipo de fecha rompe la interfaz de usuario de cuadrícula del cliente.

<u>Pasos a seguir</u>:

1. Cree un atributo personalizado con tipo de fecha:
   * Vaya a **Tiendas** > **Atributos** > **Agregar atributo**.
   * Establezca el Tipo de entrada en Fecha.
   * Establezca las Opciones de Agregar a columna en Sí.
   * Guarde el atributo.
1. Vaya a **Administración** > **Clientes** > **Todos los clientes**.
   * Agregue el atributo personalizado recién agregado a la cuadrícula desde la opción Columnas.
1. Cree/edite un cliente y establezca el valor del campo de atributo de fecha personalizado creado.
1. Guarde, reindexe y borre la caché.
1. Vaya a **Clientes** > **Todos los clientes**.
   * Marque la cuadrícula de cliente.

<u>Resultados esperados</u>:

La cuadrícula de cliente de administración muestra todos los datos, incluido el nuevo atributo personalizado de fecha, sin interrumpir la interfaz de usuario de la cuadrícula de cliente.

<u>Resultados reales</u>:

La IU de la cuadrícula del cliente de administración está dañada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del tipo de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md).
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md).

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
