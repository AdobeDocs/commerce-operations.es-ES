---
title: 'ACSD-48058: el reíndice de precios del producto no funciona si el producto agrupado no está asignado a un sitio web'
description: Aplique el parche ACSD-48058 para corregir el problema de Adobe Commerce en el que el reíndice de precios del producto no funciona si el producto agrupado no está asignado a ningún sitio web.
feature: Admin Workspace, Orders, Products
role: Admin
exl-id: 270e1b5d-75e0-4374-973a-2bb37161ceec
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-48058: el reíndice de precios del producto no funciona si el producto agrupado no está asignado a un sitio web

El parche ACSD-48058 corrige el problema de que el reíndice de precios del producto no funciona si el producto agrupado no está asignado a ningún sitio web. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25. El ID del parche es ACSD-48058. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El reíndice de precios del producto no funciona si el producto agrupado no está asignado a ningún sitio web.

<u>Pasos a seguir</u>:

1. Vaya a Adobe Commerce Admin > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** y cree un nuevo producto agrupado o edite uno existente.
   * Haga clic en la ficha **[!UICONTROL Product in Websites]** y desmarque todas las casillas (sitios web)
   * Guardar el producto
1. Realice una reindexación.

<u>Resultados esperados</u>:

La reindexación se ha realizado correctamente.

<u>Resultados reales</u>:

Se produce el siguiente error al ejecutar el índice de precios del producto:

```bash
Undefined array key <bundel product id > in vendor/magento/module-bundle/Model/ResourceModel/Indexer/Price/DisabledProductOptionPriceModifier.php on line 117
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
