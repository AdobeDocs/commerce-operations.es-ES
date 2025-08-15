---
title: 'ACSD-42807: el signo de moneda personalizado no se muestra en la tienda'
description: El parche de ACSD-42807 corrige el problema en el que el signo de moneda personalizado no se muestra en la tienda. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17. El ID del parche es ACSD-42807. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.
feature: Storefront
role: Developer
exl-id: 9aa3dd73-fab8-4a5b-b177-5226a37ee3c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-42807: el signo de moneda personalizado no se muestra en la tienda

El parche de ACSD-42807 corrige el problema en el que el signo de moneda personalizado no se muestra en la tienda. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17. El ID del parche es ACSD-42807. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.3

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.4

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El signo de moneda personalizado no se muestra en la tienda.

<u>Pasos a seguir</u>:

1. Vaya a **Tienda** > **Configuración** > **Configuraciones** > **General** > **Configuración de moneda** y seleccione cualquier moneda personalizada. Por ejemplo: **Peso mexicano**.
1. Vaya a **Tienda** > **Configuración** > **Configuraciones** > **General** > **Opciones locales** y seleccione **Español (México)**.
1. Vaya a **Almacenar** > **Símbolos de moneda** y configure el símbolo de moneda en **MX$**.
1. Compruebe el símbolo de moneda en el front-end.

<u>Resultados esperados</u>:

El símbolo de moneda predeterminado es &quot;MX$&quot;, con la moneda establecida como &quot;Peso mexicano&quot; y la configuración regional establecida como &quot;Español (México)&quot;.

<u>Resultados reales</u>:

El símbolo de moneda predeterminado muestra &quot;$&quot;.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
