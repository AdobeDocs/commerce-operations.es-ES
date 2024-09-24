---
title: "ACSD-48313: la columna [!UICONTROL configurable_variations] no se analiza si el valor del atributo contiene una coma"
description: Aplique el parche ACSD-48313 para corregir el problema de Adobe Commerce en el que la columna [!UICONTROL configurable_variations] no se analiza si el valor del atributo contiene una coma.
feature: Attributes, Configuration
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-48313: la columna **[!UICONTROL configurable_variations]** no se analiza si el valor del atributo contiene una coma

El parche ACSD-48313 resuelve el problema en el que la columna **[!UICONTROL configurable_variations]** no se analiza si el valor del atributo contiene una coma. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25. El ID del parche es ACSD-48313. La versión en la que se solucionará este problema aún no está disponible.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Después de exportar productos configurables, el archivo resultante no se puede importar de nuevo debido a un problema de formato con el atributo **[!UICONTROL configurable_variations]**. Esto sucede cuando hay opciones de atributo que incluyen una coma.

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** y cree un nuevo atributo _Size_:
1. Tipo de entrada de catálogo para el propietario de la tienda: **[!UICONTROL Dropdown]**.
1. Cree opciones que incluyan una coma, p. ej.:
   * 10,2 cm.
   * 15,5 cm.
1. **[!UICONTROL Advanced Attribute Properties]** - Ámbito: _Global_.
1. Cree un nuevo producto configurable con la funcionalidad Crear configuraciones.
1. Seleccione el atributo _Size_ anterior y las dos opciones que incluyen la coma.
1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Export]** y cree una nueva exportación de productos (ejecute el cron para almacenar en déclencheur la generación del archivo CSV).
1. Vaya a **[!UICONTROL System]** > **[!UICONTROL Data Transfer]** > **[!UICONTROL Import]** e intente volver a importar el mismo archivo CSV creado anteriormente.

<u>Resultados esperados</u>:

El usuario debe poder importar el archivo.

<u>Resultados reales</u>:

```
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
