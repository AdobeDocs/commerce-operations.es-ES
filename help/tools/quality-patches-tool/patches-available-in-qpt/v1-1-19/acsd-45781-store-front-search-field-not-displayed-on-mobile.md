---
title: 'ACSD-45781: el campo de búsqueda principal de la tienda no se muestra en el móvil'
description: El parche de MDVA-45781 resuelve el problema de que el campo de búsqueda de la tienda no se muestre en dispositivos móviles. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.19. El ID del parche es MDVA-45781. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.
feature: Cache, Native Luma Frontend Development, Search
role: Admin
exl-id: f761461b-2dd0-45d2-b80d-57793f6f0924
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-45781: el campo de búsqueda principal de la tienda no se muestra en el móvil

El parche de MDVA-45781 resuelve el problema de que el campo de búsqueda de la tienda no se muestre en dispositivos móviles. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.19. El ID del parche es MDVA-45781. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.3.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El campo de búsqueda principal de la tienda no se muestra en dispositivos móviles

<u>Pasos a seguir</u>:

1. Vaya a Commerce Admin > **Tiendas** > **Configuración** > **Catálogo** > **Búsqueda en el catálogo** y establezca:
   * Habilitar las recomendaciones de búsqueda para *No*
   * Habilitar sugerencias de búsqueda para *No*
1. Haga clic en el botón **Guardar configuración**.
1. Limpie la caché.
1. Con la temática estándar de Luma, navegue con dispositivos móviles.
1. Haz clic en el botón **Buscar**.

<u>Resultados esperados</u>:

Aparecerá el formulario de búsqueda de entrada.

<u>Resultados reales</u>:

No pasa nada.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
