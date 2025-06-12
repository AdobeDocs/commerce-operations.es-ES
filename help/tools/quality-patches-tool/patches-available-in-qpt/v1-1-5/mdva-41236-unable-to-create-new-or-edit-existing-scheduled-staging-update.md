---
title: 'MDVA-41236: No se pueden crear nuevas actualizaciones programadas o editar las existentes para el producto'
description: El parche de MDVA-41236 soluciona el problema en el que los usuarios no pueden crear actualizaciones programadas nuevas o editar las existentes para el producto si se ha eliminado anteriormente la "Fecha de finalización". Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. El ID del parche es MDVA-41236. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.
feature: Products, Staging
role: Admin
exl-id: 82192778-4f25-40a0-882e-d52d32c433c2
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# MDVA-41236: No se pueden crear nuevas actualizaciones programadas o editar las existentes para el producto

El parche de MDVA-41236 soluciona el problema en el que los usuarios no pueden crear actualizaciones programadas nuevas o editar las existentes para el producto si se ha eliminado anteriormente la &quot;Fecha de finalización&quot;. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.5. El ID del parche es MDVA-41236. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.5.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.2

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los usuarios no pueden crear nuevas programaciones o editar las existentes para productos si la &quot;Fecha de finalización&quot; se ha eliminado anteriormente.

<u>Pasos a seguir</u>:

1. Cree un producto con el estado establecido en *deshabilitar*.
1. Añada una actualización programada para habilitar este producto.
   * Añadir fechas de inicio y finalización futuras.
1. Edite la actualización programada eliminando **End Date**.
1. Vuelva a editar la programación e intente agregar una **Fecha de finalización**. Se producirá un error.
1. Actualice la página y vuelva a **Editar actualización programada**.
1. Haga clic en **Eliminar de la actualización** > **Eliminar la actualización**.
1. Ahora no debería ver la actualización programada en la parte superior de la página de edición del producto.
1. Intente crear una nueva actualización programada que se superponga a la duración anterior.

<u>Resultados esperados</u>:

* No hay ningún error en el paso 4. El administrador puede actualizar la actualización programada sin ningún error, ya que la programación aún no está activa.
* El usuario administrador puede eliminar la actualización anterior y crear una nueva.

<u>Resultados reales</u>:

Los usuarios reciben el siguiente mensaje de error:

*error: ya existe una actualización futura en este intervalo de tiempo. Establezca un intervalo diferente e inténtelo de nuevo.*


## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte la sección [Parches disponibles en QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
