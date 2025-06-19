---
title: 'ACSD-59930: Mejora el rendimiento de los flujos de la empresa'
description: Aplique el parche ACSD-59930 para resolver el problema de Adobe Commerce en el que se muestra un error *Timeout* en el panel de administración al crear, guardar o eliminar una compañía con un administrador que tenga direcciones *1000+* en la libreta de direcciones.
feature: Customers, B2B
role: Admin, Developer
exl-id: eaa6c78d-13e3-439d-90f7-70c1c96c3197
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59930: Mejora el rendimiento de los flujos de la empresa

El parche ACSD-59930 corrige el problema en el que se muestra un error de *Timeout* en el panel de administración al crear, guardar o eliminar una compañía con un administrador que tiene *1000+* direcciones en la libreta de direcciones. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.53. El ID del parche es ACSD-59930. Este problema está programado para solucionarse en Adobe Commerce B2B-1.5.0.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6-p4

**Compatible con versiones de Adobe Commerce:**

Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Mejora el rendimiento de los flujos de creación, guardado y eliminación de la empresa.

<u>Requisitos previos:</u>:

Instale y habilite los módulos B2B de Adobe Commerce.

<u>Pasos a seguir</u>:

1. Crear un cliente con *1000+* direcciones en *[!UICONTROL Address Book]*.
1. Cree una empresa y utilice el cliente anterior como administrador.
1. Guarde la compañía.

<u>Resultados esperados</u>:

La empresa se ha creado correctamente sin mostrar errores de tiempo de espera.

<u>Resultados reales</u>:

Se muestra un error de tiempo de espera.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
