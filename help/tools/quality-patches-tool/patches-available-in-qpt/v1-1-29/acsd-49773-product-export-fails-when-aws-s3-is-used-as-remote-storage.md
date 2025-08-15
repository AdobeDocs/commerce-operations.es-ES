---
title: 'ACSD-49773: la exportación del producto falla cuando AWS S3 se utiliza como almacenamiento remoto'
description: Aplique el parche ACSD-49773 para corregir el problema de Adobe Commerce en el que la exportación del producto falla cuando AWS S3 se utiliza como almacenamiento remoto.
feature: Data Import/Export, Iaas, Products, Storage
role: Admin
exl-id: 82f1299f-52b6-4f87-b01c-072d1661c022
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-49773: la exportación del producto falla cuando AWS S3 se utiliza como almacenamiento remoto

El parche de ACSD-49773 corrige el problema en el que la exportación del producto falla cuando AWS S3 se utiliza como almacenamiento remoto. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29. El ID del parche es ACSD-49773. Tenga en cuenta que el problema se solucionó en Adobe Commerce 2.4.6.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.2 - 2.4.5-p2

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La exportación del producto falla cuando AWS S3 se utiliza como almacenamiento remoto.

<u>Pasos a seguir</u>:

1. Instale un perfil de datos de gran tamaño.
1. Cree una cuenta de AWS, y configure un contenedor de S3 y un usuario de IAM.
1. Actualice `app/etc/env.php` con las configuraciones.
1. Ejecutar `bin/magento setup:upgrade`.
1. Vaya al servidor y realice una exportación de producto completa.
1. Supervise el estado del mensaje en cola de la tabla `[queue_message_status]`.
1. Compruebe los registros del sistema.

<u>Resultados esperados</u>:

La exportación del producto finaliza sin errores.

<u>Resultados reales</u>:

Se registra un error en los registros del sistema.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool]
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool]
* [Prácticas recomendadas para modificar tablas de base de datos](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) en el libro de estrategias de implementación de Commerce

Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) en la guía [!DNL Quality Patches Tool].
