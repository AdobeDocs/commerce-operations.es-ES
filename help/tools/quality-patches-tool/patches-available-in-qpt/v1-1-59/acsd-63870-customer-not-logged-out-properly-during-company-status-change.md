---
title: 'ACSD-63870: el cliente no ha cerrado sesión correctamente durante el cambio de estado de la empresa'
description: Aplique el parche ACSD-63870 para corregir el problema de Adobe Commerce en el que un cliente de la compañía no cierra sesión correctamente cuando el estado de la compañía cambia durante una sesión activa del cliente.
feature: Customers, B2B, Companies
role: Admin, Developer
exl-id: 4488f3cb-bb34-491e-8821-c2e98ff69429
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63870: el cliente no ha cerrado sesión correctamente durante el cambio de estado de la empresa

El parche ACSD-63870 resuelve el problema en el que un cliente de la empresa no cierra sesión correctamente cuando el estado de la empresa cambia durante una sesión de cliente activa. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. El ID del parche es ACSD-63870. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.8.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4-p6

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.4-p10

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Error de cierre de sesión del cliente cuando se cambia el estado de la empresa durante una sesión activa del cliente.

<u>Pasos a seguir</u>:

1. Habilitar la funcionalidad B2B.
1. Cree un producto sencillo.
1. Cree una nueva compañía y márquela como *Activa*.
1. Inicie sesión como usuario de la empresa y añada un producto al carro de compras.
1. Continúe con el cierre de compra hasta el paso [!UICONTROL Shipping Address]. No introduzca la dirección.
1. Vaya a Administración y cambie el estado de la compañía a *Aprobación pendiente*.
1. Vuelva al front-end y rellene la dirección de envío.

<u>Resultados esperados</u>:

Se ha cerrado la sesión del cliente.

<u>Resultados reales</u>:

* Los usuarios reciben el error *Se produjo un error*.
* `var/log/exception.log` contiene:

  ```
  report.CRITICAL: InvalidArgumentException: Incorrect theme identification key in /home/lib/internal/Magento/Framework/View/Design/Theme/FlyweightFactory.php:60
  ```


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Pasos adicionales necesarios tras la instalación del parche

(Esta sección es opcional; es posible que se requieran algunos pasos después de aplicar el parche para solucionar el problema). 

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
