---
title: 'ACSD-51291: un administrador restringido puede añadir imágenes/vídeos al producto asignado a varios sitios web'
description: Aplique el parche ACSD-51291 para solucionar el problema de Adobe Commerce, donde los administradores restringidos con acceso a un sitio web pueden agregar imágenes/vídeos a un producto asignado a varios sitios web.
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: a4edd034-f718-4559-9993-11609f0d0efa
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%
---
# ACSD-51291: un administrador restringido puede añadir imágenes/vídeos al producto asignado a varios sitios web

El parche ACSD-51291 corrige el problema en el que un administrador restringido con acceso a un sitio web puede agregar imágenes/vídeos a un producto asignado a varios sitios web. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32. El ID del parche es ACSD-51291. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un administrador restringido con acceso a un sitio web puede agregar imágenes o vídeos a un producto asignado a varios sitios web.

<u>Pasos a seguir</u>

1. Inicie sesión como administrador.
1. Cree un segundo sitio web, tienda y vista de tienda.
1. Cree una segunda función de administrador con recursos solo para la segunda vista del sitio web, la tienda y la tienda.
1. Cree un segundo administrador y asígnelo al nuevo rol de administrador restringido.
1. Cree un nuevo producto y asígnelo a los sitios web predeterminados y a los nuevos.
1. Cierre la sesión del perfil de administrador principal.
1. Inicie sesión como el nuevo administrador restringido.
1. Edite el producto creado, que se ha asignado a ambos sitios web.
1. Abra la ficha **[!UICONTROL Images and Videos]**.

<u>Resultados esperados</u>:

* Se muestra el siguiente mensaje:

  *El administrador restringido puede realizar acciones con imágenes o vídeos, pero únicamente si tiene derechos sobre todos los sitios web a los que está asignado el producto.*

* El botón **[!UICONTROL Add Video]** no está activo.

<u>Resultados reales</u>:

El administrador restringido puede añadir imágenes y vídeos incluso cuando el producto está asignado a un sitio web al que no tiene acceso.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
