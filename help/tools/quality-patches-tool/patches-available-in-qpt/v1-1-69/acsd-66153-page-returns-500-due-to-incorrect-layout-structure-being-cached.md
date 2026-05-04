---
title: 'ACSD-66153: La página devuelve un error 500 debido a una estructura de diseño incorrecta en caché'
description: Aplique el parche ACSD-66153 para corregir el problema de Adobe Commerce en el que una página devuelve un código de error 500 debido a una estructura de diseño incorrecta en caché.
feature: Catalog Management
role: Admin, Developer
type: Troubleshooting
exl-id: 2d6f47cb-2244-40b6-b1b9-0d03f13adc43
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# ACSD-66153: La página devuelve un error 500 debido a una estructura de diseño incorrecta en caché

El parche ACSD-66153 corrige el problema en el que una página devuelve un código de error 500 debido a una estructura de diseño incorrecta en caché. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACSD-66153. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p10

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Una página devuelve un error 500 debido a una estructura de diseño incorrecta en caché.

<u>Pasos a seguir</u>:

1. Instalar `2.4-develop`.
1. Cree e instale un módulo personalizado:
1.1 Agregar un bloque personalizado al diseño `catalog_category_view`.
1.1 Inserte `Magento\Framework\View\Result\Layout` en el bloque personalizado mediante su constructor.
1. Crear la categoría **[!UICONTROL shop]**.
1. Abrir **[!UICONTROL two terminal windows]**:
   1. **Terminal 1**: Limpie continuamente la caché de diseño:

      ```shell
      for i in {1..200}; do
        bin/magento cache:clean layout
      done
      ```

   1. **Terminal 2**: simular solicitudes simultáneas en la página de categoría:

      ```shell
      for i in {1..200}; do
        curl -s -o /dev/null -w "Request $i: HTTP %{http_code}\n""http://your_magento_base_url/shop.html?req=$i"
      done
      ```

1. Algunas solicitudes fallan aleatoriamente con un código de estado 500 y `var/log/support_report.log` muestra el siguiente error:

   ```yaml
   report.CRITICAL: The element with the "root" ID wasn't found. Verify the ID and try again. [] []
   ```

<u>Resultados esperados</u>:

Todas las solicitudes devuelven 200 OK.

<u>Resultados reales</u>:

Algunas solicitudes devuelven de forma intermitente 500 Error interno del servidor.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
