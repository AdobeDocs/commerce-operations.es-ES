---
title: 'ACSD-51666: Error "La sesión ha caducado, vuelva a iniciar sesión". después de iniciar sesión'
description: Aplique el parche ACSD-51666 para solucionar el problema de Adobe Commerce donde el error * La sesión ha caducado, vuelva a iniciar sesión. * se produce después de intentar iniciar sesión.
feature: Customers
role: Admin, Developer
exl-id: 8968b314-6625-45fa-9733-20560cca7089
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# ACSD-51666: Error *La sesión ha caducado, vuelva a iniciar sesión.* después de iniciar sesión

La revisión ACSD-51666 corrige el problema donde el error *La sesión ha caducado, inicie sesión de nuevo.* se produce después de intentar iniciar sesión. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.36. El ID del parche es ACSD-51666. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Recibe el error *La sesión ha caducado, vuelva a iniciar sesión.* al intentar iniciar sesión con la nueva contraseña desde un dispositivo después de restablecer la contraseña en otro dispositivo. Solo sucede si hay una solicitud de Ajax adicional en la página agregada por un módulo personalizado.

<u>Pasos a seguir</u>:

1. Instale un módulo personalizado que agregue una solicitud de Ajax a todas las páginas de la tienda.
1. Cree una nueva cuenta.
1. Cierre la sesión y vuelva a la página de inicio de sesión.
1. Abra el vínculo *Olvidé la contraseña* en un explorador diferente y envíe el correo electrónico *Restablecer contraseña*.
1. Abra el correo electrónico para restablecer la contraseña en el primer explorador y establezca la nueva contraseña.
1. Intente iniciar sesión en el segundo explorador.

<u>Resultados esperados</u>:

Puede iniciar sesión correctamente en el primer intento.

<u>Resultados reales</u>:

* Ha visto *La sesión ha caducado, vuelva a iniciar sesión.* error.
* No ha iniciado sesión ni se le ha redirigido a la página principal.
* El segundo intento de iniciar sesión se ha realizado correctamente.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
