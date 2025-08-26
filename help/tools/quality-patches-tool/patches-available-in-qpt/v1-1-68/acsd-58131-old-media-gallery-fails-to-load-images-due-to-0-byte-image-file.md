---
title: 'ACSD-58131: la galería de medios antigua no puede cargar imágenes debido a un archivo de imagen de 0 bytes'
description: Aplique el parche ACSD-58131 para corregir el problema de Adobe Commerce en el que la galería de medios antigua no procesa imágenes cuando una imagen de 0 bytes está presente en el directorio.
feature: Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: b09749a1e56ab6a7b613135ca252fd69757669d0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-58131: la galería de medios antigua no puede cargar imágenes debido a un archivo de imagen de 0 bytes

El parche ACSD-58131 corrige el problema en el que la antigua galería de medios no procesaba imágenes cuando una imagen de 0 bytes estaba presente en el directorio. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. El ID del parche es ACSD-58131. Este problema está programado para solucionarse en Adobe Commerce 2.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se coloca una imagen de 0 bytes en el directorio de la galería de medios, la galería de medios antigua no procesa ninguna imagen. El sistema actualizado ahora omite los archivos de 0 bytes no válidos, muestra las imágenes válidas según lo esperado y registra una advertencia para cada archivo no válido.

```
[2024-05-02T14:00:39.616459+00:00] report.WARNING: The image empty2.jpg is invalid and cannot be displayed in the gallery. [] []
```

<u>Pasos a seguir</u>:

1. Vaya a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]**.
1. Establezca **[!UICONTROL Enable Old Media Gallery]** en *Sí*.
1. Coloque algunas imágenes en el directorio `pub/media/wysiwyg`.
1. Cree una imagen de 0 bytes en el mismo directorio usando `touch pub/media/wysiwyg/empty_image.png`.
1. Agregue una imagen del directorio `wysiwyg` mediante Page Builder bajo cualquier contenido (por ejemplo, un bloque de CMS):
   1. Cree un nuevo bloque. Vaya a **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Blocks]** y haga clic en **[!UICONTROL Add New Block]**.
   1. Edite la sección de contenido mediante Page Builder.
   1. En **[!UICONTROL Layout]**, arrastre un nuevo(a) **[!UICONTROL Row]** al escenario.
   1. Expanda **[!UICONTROL Media]** y arrastre un marcador de posición **[!UICONTROL Image]** a la fila.
   1. Haga clic en **[!UICONTROL Select from Gallery]**.
   1. Seleccione el directorio `wysiwyg` si no está seleccionado de forma predeterminada.

<u>Resultados esperados</u>:

La galería de medios sigue funcionando aunque exista una imagen de 0 bytes (o cualquier otro archivo).

<u>Resultados reales</u>:

La galería de medios no puede cargar ninguna imagen del directorio `wysiwyg` debido a un error crítico registrado en `var/log/system.log`:

```
[2024-03-22T05:00:55.100934+00:00] report.CRITICAL: Exception: Notice: getimagesizefromstring(): Error reading from ! in /app/project/vendor/magento/module-cms/Model/Wysiwyg/Images/Storage.php on line 426 in /app/project/vendor/magento/framework/App/ErrorHandler.php:62
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
