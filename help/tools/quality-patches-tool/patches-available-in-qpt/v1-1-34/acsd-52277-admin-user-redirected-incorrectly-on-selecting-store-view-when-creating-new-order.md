---
title: 'ACSD-52277: el usuario administrador redireccionaba incorrectamente al seleccionar la vista de la tienda al crear un nuevo pedido'
description: Aplique el parche ACSD-52277 para corregir el problema de Adobe Commerce en el que un usuario administrador no se redirige correctamente después de seleccionar la vista de tienda al crear un nuevo pedido en Administración.
exl-id: 61ef59a9-7a31-441f-a763-2d8016498fa7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---

# ACSD-52277: el usuario administrador redireccionaba incorrectamente al seleccionar la vista de la tienda al crear un nuevo pedido

El parche de ACSD-52277 corrige el problema en el que un usuario administrador no se redirige correctamente después de seleccionar la vista de la tienda al crear un nuevo pedido en Administración. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34. El ID del parche es ACSD-52277. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4, 2.4.6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Un usuario administrador no se redirige correctamente después de seleccionar la vista de la tienda al crear un nuevo pedido.

<u>Pasos a seguir</u>

1. Instale una instancia limpia.
1. Cree un producto.
1. Cree un sitio web, una tienda y dos vistas de la tienda adicionales.
1. Cree un pedido del administrador seleccionando *vista de tienda 1*.

<u>Resultados esperados</u>:

Se redirige al usuario a la página de pedidos.

<u>Resultados reales</u>:

No se redirige al usuario a la página de pedidos después de seleccionar la vista de la tienda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
