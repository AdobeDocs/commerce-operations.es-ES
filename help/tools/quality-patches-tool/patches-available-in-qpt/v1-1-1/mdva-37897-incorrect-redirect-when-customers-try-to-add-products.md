---
title: "MDVA-37897: Redirección incorrecta al añadir productos de Vistos recientemente"
description: El parche MDVA-37897 resuelve el problema de la redirección incorrecta cuando los usuarios intentan agregar productos con opciones del widget de elementos visualizados recientemente. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1. El ID del parche es MDVA-37897. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.4 de Adobe Commerce.
feature: Products
role: Admin
source-git-commit: c1055ed10813aa6e585f93ec3091d216af06affd
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# MDVA-37897: redirección incorrecta al añadir productos de productos vistos recientemente

El parche MDVA-37897 resuelve el problema de la redirección incorrecta cuando los usuarios intentan agregar productos con opciones del widget de elementos visualizados recientemente. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.1. El ID del parche es MDVA-37897. Tenga en cuenta que está programado que el problema se corrija en la versión 2.4.4 de Adobe Commerce.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce en nuestra infraestructura de nube 2.4.1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando un usuario intenta agregar un producto de la sección Vistos recientemente que tiene opciones requeridas para seleccionarse, se redirige al usuario a la página de lista de productos en lugar de a la página de detalles del producto.

<u>Pasos a seguir</u>:

1. Cree un producto sencillo con opciones personalizables (Tipo: Botón de opción).
1. Configure el widget de elementos visualizados recientemente para mostrar productos.
1. Visite los productos que tengan opciones personalizables para que aparezcan en el widget de elementos visualizados recientemente.
1. Haga clic en **Agregar al carro** en uno de los productos del widget de elementos visualizados recientemente.

<u>Resultados esperados</u>:

Se le redirigirá a la página de detalles del producto para elegir las opciones.

<u>Resultados reales</u>:

Se le redirigirá a la página de lista de productos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos en función del tipo de implementación:

* Adobe Commerce on-premise: [Guía de actualización de software > Aplicar parches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) en nuestra documentación para desarrolladores.
* Adobe Commerce en nuestra infraestructura de nube: [Actualizaciones y parches > Aplicar parches](https://devdocs.magento.com/cloud/project/project-patch.html) en nuestra documentación para desarrolladores.

## Lectura relacionada

Para obtener más información sobre parches de calidad para Adobe Commerce, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
