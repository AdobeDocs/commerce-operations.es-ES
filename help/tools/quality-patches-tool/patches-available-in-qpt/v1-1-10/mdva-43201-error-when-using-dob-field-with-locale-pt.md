---
title: 'MDVA-43201: Error al utilizar el campo DOB con la configuración regional PT'
description: El parche MDVA-43201 resuelve el problema en el que se produce un error al utilizar el atributo de cliente DOB en el formulario de registro de cliente para la configuración regional en portugués. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. El ID del parche es MDVA-43201. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: B2B, Cache
role: Admin
exl-id: be087420-1ee3-40cc-8ff7-62c5641609cc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-43201: Error al utilizar el campo DOB con la configuración regional PT

El parche MDVA-43201 resuelve el problema en el que se produce un error al utilizar el atributo de cliente DOB en el formulario de registro de cliente para la configuración regional en portugués. Este parche está disponible cuando está instalada la [Herramienta Parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. El ID del parche es MDVA-43201. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Cuando se agrega el atributo de cliente DOB al formulario de registro de cliente para la configuración regional en portugués, el formulario da el error *Argumento 1 pasado a iterator_to_array() debe implementar la interfaz travesable, nulo dado*.

<u>Requisitos previos</u>:

Los módulos B2B están instalados.

<u>Pasos a seguir</u>:

1. Vaya a Administración > **Tiendas** > **Configuración** > **General** > **Opciones de configuración regional**, establezca la configuración regional en **Portugués (Portugal)** y haga clic en **Guardar**.
1. Reindexe y borre la caché.
1. Vaya a **Tiendas** > **Atributo** > **Cliente**.
1. Abra el atributo de cliente DOB y establezca **Mostrar en tienda** en **Sí**.
1. Seleccionar todo del **formulario que se usará en**.
1. Guarde el atributo.
1. Vaya a la página Crear nueva cuenta en el front-end.

<u>Resultados esperados</u>:

El formulario de registro de cliente de la tienda portuguesa no genera ningún error al añadir el atributo DOB.

<u>Resultados reales</u>:

El formulario de registro de cliente de la tienda portuguesa proporciona un error al añadir el atributo DOB.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
