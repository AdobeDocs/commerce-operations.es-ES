---
title: 'ACSD-52906: resolviendo el problema de cookies X-Magento-Vary para el almacenamiento en caché de clientes que iniciaron sesión'
description: Aplique el parche ACSD-52906 para corregir el problema de Adobe Commerce en el que la cookie X-Magento-Vary se establece incorrectamente para los clientes que iniciaron sesión.
feature: Cache
role: Admin, Developer
exl-id: 487b7588-7131-4502-b714-05f37520991f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-52906: resolución del problema de las cookies X-Magento-Vary para los clientes que iniciaron sesión

La revisión ACSD-52906 corrige el problema en el que la cookie X-Magento-Vary se establece incorrectamente para los clientes que iniciaron sesión. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.36. El ID del parche es ACSD-52906. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cookie X-Magento-Vary se establece incorrectamente para los clientes que iniciaron sesión y que pertenecen al mismo segmento de cliente, lo que provoca un almacenamiento en caché incorrecto para algunas páginas.

<u>Requisitos previos</u>:

Los módulos Adobe Commerce Inventory management (MSI) están instalados y habilitados.

<u>Pasos a seguir</u>:

1. Configurar la caché de [!DNL Varnish] o [!DNL Fastly].
1. Cree un nuevo segmento de cliente y asígnelo a los clientes *registrados*.
1. Cree dos clientes, por ejemplo, cliente1 y cliente2.
1. Borre la caché.
1. Inicie sesión como cliente1 y vaya a la página de inicio.
1. Abra una página de incógnito en el explorador.
1. Vaya a cualquier página que no sea la página principal.
1. Inicie sesión como cliente2.
1. Vaya a la página principal.
1. Compruebe si la página se almacena en caché en la consola de desarrollo del explorador.

<u>Resultados esperados</u>:

La página se recupera de la caché.

<u>Resultados reales</u>:

La página no se almacena en caché.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
