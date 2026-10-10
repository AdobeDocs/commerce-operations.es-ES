---
title: 'ACSD-48313: la columna [!UICONTROL configurable_variations] no se analiza si el valor del atributo contiene una coma'
description: Aplique el parche ACSD-48313 para corregir el problema de Adobe Commerce en el que la columna [!UICONTROL configurable_variations] no se analiza si el valor del atributo contiene una coma.
feature: Attributes, Configuration
role: Admin
exl-id: 1ce0c8dc-0d03-4ebd-b02a-08090b244190
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 76cfaac4-e563-56dd-8938-708bf8b84956
    internal-label: Attributes
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%
---
# ACSD-48313: la columna **[!UICONTROL configurable_variations]** no se analiza si el valor del atributo contiene una coma

El parche ACSD-48313 resuelve el problema en el que la columna **[!UICONTROL configurable_variations]** no se analiza si el valor del atributo contiene una coma. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.25. El ID del parche es ACSD-48313. La versión en la que se solucionará este problema aún no está disponible.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.4

**Compatible con versiones de Adobe Commerce:**
* Adobe Commerce (todos los métodos de implementación) 2.4.0 - 2.4.4-p5

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

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

```text
1. Column configurable_variations: Attribute with code "2cm" does not exist or is missing from product attribute set in row(s): 3
2. Column configurable_variations: Attribute with code "5cm" does not exist or is missing from product attribute set in row(s): 3
3. Column configurable_variations: Invalid option value for attribute "size" in row(s): 3
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.


## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
