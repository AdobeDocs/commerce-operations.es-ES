---
title: "MDVA-39384: No se puede guardar el atributo de cliente personalizado para el usuario de la empresa"
description: El parche MDVA-39384 resuelve el problema en el que el atributo de cliente personalizado de un usuario de la empresa no se guarda. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2. El ID del parche es MDVA-39384. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# MDVA-39384: No se puede guardar el atributo de cliente personalizado para el usuario de la empresa

El parche MDVA-39384 resuelve el problema en el que el atributo de cliente personalizado de un usuario de la empresa no se guarda. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2. El ID del parche es MDVA-39384. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El atributo personalizado del cliente de un usuario de la empresa no se ha guardado.

<u>Requisitos previos</u>:

Los módulos B2B están instalados.

<u>Pasos a seguir</u>:

1. Vaya a **Tiendas** > Configuración > **Configuración** > **Características B2B** y establezca la opción **Habilitar compañía** en Sí.
1. Crear un atributo de cliente personalizado:
   * Valores Necesarios: Sí (opcional, actívela para que se muestre el error de validación).
   * Mostrar en tienda: Sí.
   * Forms para usar en: todos disponibles en la lista.
1. Cree una Empresa e inicie sesión como administrador de la empresa.
1. Vaya a Estructura de la empresa en su cuenta.
1. Haga clic en el vínculo **Agregar usuario**.
1. Rellene el formulario, incluido el atributo personalizado.
1. Haga clic en **Guardar**.

<u>Resultados esperados</u>:

Los valores de atributo personalizados se guardan con el nuevo usuario de la empresa.

<u>Resultados reales</u>:

Los valores de atributo personalizados NO se guardan con el nuevo usuario de la empresa.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
