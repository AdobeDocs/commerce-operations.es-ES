---
title: 'MDVA-43731: Los sinónimos de búsqueda no funcionan cuando se agrega un valor en "Términos mínimos de coincidencia"'
description: El parche MDVA-43731 corrige el problema en el que los sinónimos de búsqueda dejan de funcionar cuando se agrega un valor en "Términos mínimos de coincidencia". Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-43731. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Cache, Marketing Tools, Search
role: Admin
exl-id: 1eada0cd-c0ab-4f0f-b6bf-7c10e1df07ce
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---

# MDVA-43731: Los sinónimos de búsqueda no funcionan cuando se agrega un valor en &quot;Términos mínimos de coincidencia&quot;

El parche MDVA-43731 corrige el problema en el que los sinónimos de búsqueda dejan de funcionar cuando se agrega un valor en &quot;Términos mínimos de coincidencia&quot;. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12. El ID del parche es MDVA-43731. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los sinónimos de búsqueda dejan de funcionar cuando se agrega un valor en &quot;Términos mínimos que deben coincidir&quot;.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce con datos de ejemplo.
1. Configure Elasticsearch7 como motor de búsqueda.
1. Busca la palabra &quot;Chaqueta&quot;. Se mostrará una lista de productos.
1. Agregue el parámetro [4&lt;60%] en **Configuración** > **Catálogo** > **Búsqueda en el catálogo** > **Términos mínimos que deben cumplirse**.
1. Borre la caché de configuración y vuelva a indexar.
1. De nuevo busque la palabra &quot;Chaqueta&quot; y observe que se muestra una lista de productos.
1. Vaya a **Marketing** > **SEO y búsqueda** > **Sinónimos de búsqueda**.
1. Cree Sinónimos de búsqueda añadiendo los siguientes sinónimos: jacket, bagtecs, express plus.
1. Realice una reindexación.
1. Realice una búsqueda de productos utilizando cualquiera de los sinónimos. Por ejemplo, chaqueta.

<u>Resultados esperados</u>:

Obtendrá la misma lista de productos que antes en los resultados de búsqueda.

<u>Resultados reales</u>:

No se muestra ningún producto en los resultados de búsqueda.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
