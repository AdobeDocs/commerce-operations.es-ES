---
title: 'ACSD-63139: La exportación de productos falla cuando los atributos de productos contienen miles de valores de opción'
description: Aplique el parche ACSD-63139 para corregir el problema de Adobe Commerce en el que la exportación del producto falla cuando los atributos del producto contienen miles de valores de opción.
feature: Data Import/Export
role: Admin, Developer
exl-id: 785907dc-aa3f-49e2-bd52-c3afe4393456
type: Troubleshooting
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63139: La exportación de productos falla cuando los atributos de productos contienen miles de valores de opción

El parche ACSD-63139 corrige el problema en el que la exportación del producto falla cuando los atributos del producto contienen miles de valores de opción. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64. El ID del parche es ACSD-63139. Este problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p10

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La exportación del producto falla cuando los atributos del producto contienen miles de valores de opción.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce con el módulo B2B.
1. Importar un volcado de base de datos grande con:
   &#x200B;- ~7.000 productos
   &#x200B;- ~450 atributos del producto
   : Algunos atributos con más de 100 opciones
1. Ejecute el siguiente comando para instalar cron (si no está instalado):

   ```
   bin/magento cron:install
   ```

1. Configure [!DNL RabbitMQ] siguiendo las instrucciones de [[!DNL RabbitMQ] requisitos previos](https://experienceleague.adobe.com/es/docs/commerce-operations/installation-guide/prerequisites/message-brokers/rabbitmq).
1. Abra el archivo `php.ini`, establezca el límite de memoria en 4G y reinicie el servicio PHP.
1. En el panel de administración, vaya a **[!UICONTROL System]** > *[!UICONTROL Data Transfer]* > **[!UICONTROL Export]**.
1. En la sección *[!UICONTROL Export Settings]*, establezca **[!UICONTROL Entity Type]** en *Productos*, desplácese hacia abajo y haga clic en **[!UICONTROL Continue]**.
1. Ejecute el siguiente comando para iniciar el procesador de exportación:

   ```
   bin/magento queue:consumers:start exportProcessor --max-messages=1
   ```

<u>Resultados esperados</u>:

La exportación del producto debe finalizar correctamente.

<u>Resultados reales</u>:

El proceso de exportación del producto falla y devuelve el siguiente error irrecuperable:

```
Fatal error: Allowed memory size of 4294967296 bytes exhausted (tried to allocate 12288 bytes) in /var/www/html/app/code/Magento/Catalog/Model/ResourceModel/Product/Collection.php on line 597
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
