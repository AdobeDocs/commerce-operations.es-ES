---
title: 'ACSD-48164: el administrador restringido no puede guardar el valor de nivel de sitio web'
description: Aplique el parche ACSD-48164 para corregir el problema de Adobe Commerce en el que un administrador restringido no puede guardar un valor de nivel de sitio web.
feature: Admin Workspace
role: Admin
exl-id: 1ad4758e-7ecc-48d0-8313-1163188cbe73
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48164: el administrador restringido no puede guardar el valor de nivel de sitio web

El parche ACSD-48164 corrige el problema en el que un administrador restringido no puede guardar un valor de nivel de sitio web. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27. El ID del parche es ACSD-48164. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El administrador restringido no puede guardar un valor de nivel de sitio web.

<u>Pasos a seguir</u>:

1. Crear un nuevo sitio web, tienda y vista de tienda en [!UICONTROL Admin] > **[!UICONTROL Store]** > **[!UICONTROL All Stores]**.
1. Cree un nuevo rol de administrador en [!UICONTROL Admin] > **[!UICONTROL System]** > **[!UICONTROL User Roles]**.

   * Vaya a **[!UICONTROL Role Resources]** > **[!UICONTROL Role Scopes]**, seleccione el nuevo sitio web y asigne este rol a cualquier usuario administrador.

1. Seleccione cualquier producto y asigne solo el nuevo sitio web. No seleccione el sitio web predeterminado.
1. Inicie sesión como el usuario administrador asignado en el paso dos y edite el producto en el ámbito **[!UICONTROL All Store View]** cambiando cualquier atributo de nivel de sitio web como *[!UICONTROL Status]*, *[!UICONTROL Tax Class]* y establezca el producto como nuevo.
1. Guarde el producto.

<u>Resultados esperados</u>:

El usuario administrador asociado con el ámbito de función a un sitio web puede guardar atributos de producto de nivel de sitio web utilizando el ámbito *[!UICONTROL All Store View]*.

<u>Resultados reales</u>:

Aparece el mensaje de éxito que indica que se ha guardado el producto, pero los valores de atributo del producto permanecen inalterados.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
