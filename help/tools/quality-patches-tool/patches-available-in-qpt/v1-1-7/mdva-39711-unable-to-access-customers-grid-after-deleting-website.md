---
title: 'MDVA-39711: No se puede acceder a la cuadrícula de los clientes después de eliminar el sitio web'
description: El parche de MDVA-39711 corrige el problema en el que el usuario administrador no puede acceder a la cuadrícula de los clientes después de eliminar el sitio web. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7. El ID del parche es MDVA-39711. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
feature: Configuration
role: Admin
exl-id: 7ddca2e7-86f5-4ffd-9c00-ea4c511ab663
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# MDVA-39711: No se puede acceder a la cuadrícula de los clientes después de eliminar el sitio web

El parche de MDVA-39711 corrige el problema en el que el usuario administrador no puede acceder a la cuadrícula de los clientes después de eliminar el sitio web. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7. El ID del parche es MDVA-39711. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7-p2, 2.3.4-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador no puede acceder a la cuadrícula de los clientes después de eliminar el sitio web.

<u>Pasos a seguir</u>:

1. Crear un nuevo sitio web, tienda y vista de tienda.
1. Cree un nuevo cliente en Admin y asócielo al sitio web creado.
1. Vaya a **Tiendas** > **Todas las tiendas** y elimine el sitio web creado.
1. Vaya a **Clientes** > **Todos los clientes**.

<u>Resultados esperados</u>:

* No hay ningún mensaje de error.
* Todos los clientes son visibles en la cuadrícula.

<u>Resultados reales</u>:

* El usuario recibe un mensaje de error: *No se encontró el sitio web con el ID 2 solicitado. Compruebe el sitio web e inténtelo de nuevo*
* No se muestran todos los clientes.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
