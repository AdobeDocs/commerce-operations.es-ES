---
title: 'ACSD-66149: el controlador IPN devuelve *500* para tipos no compatibles'
description: Aplique el parche ACSD-66149 para corregir el problema de Adobe Commerce en el que el controlador IPN no ignora los tipos IPN no admitidos o desconocidos, lo que provoca que el problema no se registre, interrumpe el proceso y también devuelve un error 500.
feature: Payments
role: Admin, Developer
source-git-commit: 81e8bf62c026023f71d52c219357bd7911275f69
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---


# ACSD-66149: el controlador IPN devuelve *500* para tipos no compatibles

El parche ACSD-66149 corrige el problema en el que el controlador de IPN (Notificación de pago instantáneo) devuelve un error *500* para tipos de IPN desconocidos o no compatibles. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACSD-66149. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El problema es que el controlador IPN devuelve un error *500* para tipos IPN no admitidos o desconocidos. Ocurre cuando Paypal envía IPN con algunos campos faltantes.

<u>Pasos a seguir</u>:

1. Crea un módulo personalizado que emulará todo tipo de tipos de IPN desconocidos de PayPal.
1. Cree al menos un producto.
1. Configura PayPal Express con tus propias credenciales.
1. Realiza un pedido con Paypal Express.
1. Ejecute el emulador de PayPal.

<u>Resultados esperados</u>:

El controlador IPN de la aplicación ignora los tipos IPN incorrectos y no genera *500* errores:

```Order 000000001: Status processing — HTTP 500```

<u>Resultados reales</u>:

La aplicación genera muchos errores de *500* durante el procesamiento de IPN incorrectos y, esporádicamente, no procesa algunos pedidos si faltan los campos esperados.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas
