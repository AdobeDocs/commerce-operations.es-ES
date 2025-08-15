---
title: 'AC-14985: Error al enviar correos electrónicos SMTP mediante TLS'
description: Aplique el parche de AC-14985 para corregir el problema de Adobe Commerce donde se produce un error al enviar correo electrónico del Protocolo simple de transferencia de correo (SMTP) mediante Seguridad de la capa de transporte (TLS).
feature: Configuration
role: Admin, Developer
type: Troubleshooting
exl-id: 98d91421-ebfd-4414-ade3-f25d29541874
source-git-commit: 515e6d1f00c910455a2ffddf70c4a450184e7e81
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# AC-14985: Error al enviar correos electrónicos SMTP mediante TLS

El parche de AC-14985 corrige un problema en el que se produce un error al enviar correo electrónico del Protocolo simple de transferencia de correo (SMTP) mediante Seguridad de la capa de transporte (TLS). Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. El ID del parche es AC-14985. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Se produce un error al enviar correo electrónico a través de SMTP con TLS habilitado.

<u>Pasos a seguir</u>:

1. Establezca la configuración de SMTP de la siguiente manera:
* Transporte: SMTP
* Host: url.to.smtp.host
* Puerto: 587
* SSL: TLS

<u>Resultados esperados</u>:

El correo electrónico se envía correctamente sin errores.

<u>Resultados reales</u>:

Aparece el siguiente error:

```
error:1408F10B:SSL routines:ssl3_get_record:wrong version number [] []
```

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
