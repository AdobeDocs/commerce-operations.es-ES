---
title: 'ACSD-65983: Se produce un error al volver a configurar la oferta de productos agrupados en Administración'
description: Aplique la revisión ACSD-65983 para corregir el problema de Adobe Commerce en el que aparece un error al intentar configurar un producto del paquete en la pantalla [!UICONTROL Sales] > [!UICONTROL Quotes] > [!UICONTROL Edit] en el backend.
feature: B2B, Quotes
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8a8f2b273bcbcf135677ad7ca289398bf660e02e
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---


# ACSD-65983: Se produce un error al volver a configurar la oferta de productos agrupados en Administración

El parche ACSD-65983 corrige el problema en el que la reconfiguración de una cotización de producto agrupado en el backend de administración devuelve un error. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACSD-65983. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La reconfiguración de una oferta de producto agrupada en el backend de administración devuelve un error.

<u>Pasos a seguir</u>:

1. Vaya al panel de administración y habilite **[!UICONTROL B2B Feature]**: **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Feature]**.
1. Cree un paquete de productos con un importe fijo (por ejemplo: *$10*) y agregue tres o más productos simples con un importe de *0*, *2* en **Opción 1** y *otros* en **Opción 2**.
1. Cree una cuenta de compañía desde el front-end.
1. Vaya a **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** y asigne la empresa y los productos creados al catálogo compartido nuevo o personalizado.
1. Inicie sesión como **usuario de la compañía** en el front-end y agregue un producto simple al carro de compras desde el paquete.
1. Abra la página del carro de compras y envíela como **Solicitar presupuesto**.
1. Vaya al servidor y edite la oferta creada.
1. En la sección **Citar elemento**, haga clic en el botón **Configurar**.
1. Seleccione otro producto simple de **Opción 2**.
1. Ahora haga clic en el botón **Aceptar** y verá el mensaje de error.

<u>Resultados esperados</u>:

Puede configurar correctamente los elementos de presupuesto solicitados desde el administrador normalmente, sin que se muestre ningún mensaje de error.

<u>Resultados reales</u>:

Verá el mensaje de error:

*Un problema técnico con el servidor creó un error. Intenta de nuevo continuar lo que estabas haciendo. Si el problema persiste, inténtelo de nuevo más tarde.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas
