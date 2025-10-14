---
title: 'ACSD-61845: Se produce un error en las solicitudes con encabezado de aceptación de texto/html'
description: Aplique el parche ACSD-61845 para solucionar el problema de Adobe Commerce donde el envío de una solicitud HTTP con solo un encabezado de aceptación *text/html* provoca un error 500, con módulos B2B instalados.
feature: B2B
role: Admin, Developer
exl-id: 6fa6c3ff-bb45-4b9e-afd4-95692acb0a90
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-61845: Se produce un error en las solicitudes con *text/html* accept header

El parche ACSD-61845 corrige el problema en el que una solicitud HTTP con solo un encabezado de aceptación *text/html* provoca un error 500 debido a discrepancias de tipo de medios en la gestión de respuestas. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. El ID del parche es ACSD-61845. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p1 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Al enviar una solicitud HTTP con solo *text/html* en el encabezado Aceptar, se produce un error 500 debido a una discrepancia en la configuración del tipo de medios.

<u>Requisitos previos</u>:

Los módulos B2B están instalados y habilitados.

<u>Pasos a seguir</u>:

1. Envíe una solicitud con solo *text/html* en el encabezado Aceptar, de la siguiente manera:

   ```
   curl -I --header "Accept: text/html, text/plain" http://<hostname>/pub/
   ```

<u>Resultados esperados</u>:

Se devuelve la página con un *código de estado 200*.

<u>Resultados reales</u>:

Se devuelve un error 500, con el siguiente mensaje de error en `exception.log`:

```
Magento\Framework\Webapi\Exception: Server cannot match any of the given Accept HTTP header media type(s) from the request: "text/html" with media types from the config of response renderer. in vendor/magento/framework/Webapi/Rest/Response/RendererFactory.php:84
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

[[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
