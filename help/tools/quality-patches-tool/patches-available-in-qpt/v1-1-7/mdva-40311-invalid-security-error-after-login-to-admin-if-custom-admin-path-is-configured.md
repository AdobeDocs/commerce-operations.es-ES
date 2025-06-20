---
title: 'MDVA-40311: Error "Seguridad no válida o clave de formulario" después de iniciar sesión en el administrador si se ha configurado la ruta de administración personalizada'
description: 'El parche de MDVA-40311 corrige el problema en el que el usuario administrador recibe un mensaje de error: *Seguridad o clave de formulario no válidas. Actualice la página*, después de iniciar sesión en el administrador, si la ruta de administración personalizada está configurada y la clave secreta está habilitada. Este parche está disponible cuando está instalada la [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7. El ID del parche es MDVA-40311. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.'
feature: Admin Workspace, Compliance, Security
role: Admin
exl-id: dce4914b-e32e-4af0-be24-e55680191fa3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# MDVA-40311: Error &quot;Seguridad no válida o clave de formulario&quot; después de iniciar sesión en el administrador si se ha configurado la ruta de administración personalizada

El parche MDVA-40311 corrige el problema en el que el usuario administrador recibe un mensaje de error: *Clave de formulario o seguridad no válida. Actualice la página*, después de iniciar sesión en el administrador, si la ruta de administración personalizada está configurada y la clave secreta está habilitada. Este parche está disponible cuando está instalada la [Herramienta de parches de calidad (QPT)](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7. El ID del parche es MDVA-40311. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.4.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de la herramienta Parches de Calidad. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El usuario administrador recibe un mensaje de error: *Clave de formulario o seguridad no válida. Actualice la página*, después de iniciar sesión en el administrador, si la ruta de administración personalizada está configurada y la clave secreta está habilitada.

<u>Pasos a seguir</u>:

* Inicie sesión como el usuario administrador con un nombre de usuario y una contraseña válidos.

<u>Resultados esperados</u>:

El usuario puede iniciar sesión sin ningún mensaje de error.

<u>Resultados reales</u>:

*Clave de formulario o seguridad no válida. Actualice la página* si se muestra el mensaje de error.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre la herramienta Parches de calidad, consulte:

* [Lanzamiento de la herramienta Parches de calidad: una nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de asistencia.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce mediante la herramienta Parches de calidad](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!DNL Quality Patches Tool].

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
