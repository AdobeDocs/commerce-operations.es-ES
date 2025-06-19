---
title: 'MDVA-41164: No se puede guardar ni editar la compañía con atributos de cliente personalizados'
description: El parche MDVA-41164 resuelve el problema en el que el usuario administrador no puede guardar o editar una empresa con atributos de cliente personalizados de archivos o imágenes de cualquier tipo. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. El ID del parche es MDVA-41164. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: Admin Workspace, Attributes, B2B, Companies
role: Developer
exl-id: 9d1792e0-ba7b-444b-b1b1-771fd0e328eb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# MDVA-41164: No se puede guardar ni editar la compañía con atributos de cliente personalizados

El parche MDVA-41164 resuelve el problema en el que el usuario administrador no puede guardar o editar una empresa con atributos de cliente personalizados de archivos o imágenes de cualquier tipo. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. El ID del parche es MDVA-41164. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador no puede guardar ni editar una empresa con atributos de cliente personalizados de archivos o imágenes de cualquier tipo.

<u>Requisitos previos</u>:

El módulo B2B está instalado.

<u>Pasos a seguir</u>:

1. Habilitar la compañía en **tiendas** > **configuración** > **características B2B**.
1. Crear un atributo de cliente en **Tiendas** > **Atributos** > **Clientes** > **Agregar nuevo atributo**:
   * Tipo de entrada: Archivo (adjunto)
   * Mostrar en la tienda: Sí
   * Orden de clasificación: Cualquiera
   * Forms que se usará en: seleccionar todo
1. Cree una nueva compañía en **Clientes** > **Compañías** > **Agregar nueva compañía** y cargue un archivo para el nuevo atributo creado anteriormente.

<u>Resultados esperados</u>:

El usuario puede completar la creación de la empresa y el archivo adjunto se carga sin ningún error.

<u>Resultados reales</u>:

* Aparece un mensaje de error: *Se produjo un error al guardar el archivo.*
* El registro de excepciones contiene un registro como el siguiente:

  ```php
  report.CRITICAL: Notice: Undefined index: customer in
  ../app/code/Magento/Customer/Controller/Adminhtml/File/Customer/Upload.php on line 69
  ```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
