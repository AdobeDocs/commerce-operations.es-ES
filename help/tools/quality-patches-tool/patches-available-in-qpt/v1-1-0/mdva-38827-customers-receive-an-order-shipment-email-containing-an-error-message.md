---
title: 'MDVA-38827: Los clientes reciben un error de envío de pedidos por correo electrónico'
description: 'El parche de MDVA-38827 soluciona el problema en el que los clientes reciben un correo electrónico de envío de pedidos que contiene el siguiente mensaje de error: *Lo sentimos, se ha producido un error al generar este contenido*. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0. El ID del parche es MDVA-38827. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.'
feature: Communications, Marketing Tools, Orders, Shipping/Delivery
role: Admin
exl-id: ab522c9c-2983-4c2f-b341-4487bdbee34d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-38827: Los clientes reciben un error de envío de pedidos por correo electrónico

El parche MDVA-38827 corrige el problema en el que los clientes reciben un correo electrónico de envío de pedidos que contiene el siguiente mensaje de error: *Lo sentimos, se ha producido un error al generar este contenido*. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.0. El ID del parche es MDVA-38827. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce en infraestructura en la nube 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.3-p1 - 2.4.2-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se selecciona la opción Notificar a los clientes por correo electrónico para el envío, los clientes reciben un correo electrónico con el siguiente mensaje de error: *Lo sentimos, se ha producido un error al generar este contenido*.

<u>Pasos a seguir</u>:

1. Vaya a **Marketing** > **Comunicaciones** > **Plantillas de correo electrónico** y seleccione **Agregar nueva plantilla**.
   * Seleccione **Ventas Magento** > **Nuevo envío**.
   * Haz clic en **Cargar plantilla**.
   * Agregue un nombre de plantilla (por ejemplo, Plantilla de envíos principal) y haga clic en **Guardar**.
1. Vaya a **Tienda** > Configuración > **Configuración** > **Ventas** > **Correo electrónico de ventas**:
   * Habilitar **comentarios de envío**.
   * Seleccione **Plantilla de envío principal** (consulte la parte &quot;Agregar un nombre de plantilla&quot; del Paso 1) en Plantilla de correo electrónico de comentario de envío y Plantilla de correo electrónico de comentario de envío para invitado.
1. Haga un pedido. Vaya al panel de administración > **Ventas** > **Pedido**, haga clic en **Ver** y envíe el pedido.
1. El estado del pedido cambiará de Pendiente a Procesamiento.
1. Haga clic en **Envíos** en el menú de la barra lateral izquierda y, a continuación, haga clic en **Ver** para ver el pedido.
1. Agregue un comentario en **Texto del comentario** debajo de **Historial de envíos** y marque la casilla **Notificar al cliente por correo electrónico**.
1. Haga clic en **Enviar comentario**.

<u>Resultados esperados</u>:

Se genera un correo electrónico de ventas con comentarios sobre el envío.

<u>Resultados reales</u>:

Se recibió el siguiente mensaje de error en el correo electrónico: *Lo sentimos, se produjo un error al generar este contenido.*

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
