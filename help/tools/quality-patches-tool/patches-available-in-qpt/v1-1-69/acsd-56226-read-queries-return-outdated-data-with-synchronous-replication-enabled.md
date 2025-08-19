---
title: 'ACSD-56226: las consultas READ devuelven datos obsoletos con la replicación sincrónica habilitada'
description: Aplique el parche ACSD-56226 para corregir el problema de Adobe Commerce en el que las consultas READ devuelven datos obsoletos cuando el indicador "sync_replication" está habilitado para la conexión esclava en la nube.
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: a45cef14b7b37f1112d2ef82adf29b09d63b8e2b
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# ACSD-56226: las consultas READ devuelven datos obsoletos con `synchronous_replication` habilitado

El parche ACSD-56226 corrige el problema en el que las consultas READ devuelven datos obsoletos cuando el indicador `synchronous_replication` está habilitado para la conexión esclava en la nube. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACSD-56226. Este problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Las consultas READ devuelven datos obsoletos cuando el indicador `synchronous_replication` está habilitado. Esto hace que se deshabilite la conexión esclava, lo que provoca una sobrecarga de la base de datos.

<u>Pasos a seguir</u>:

1. Establezca `MYSQL_USE_SLAVE_CONNECTION` en *true* en las variables de entorno en Adobe Commerce en la infraestructura de la nube.
1. Agregue la siguiente configuración a `.magento.env.yaml` para establecer `synchronous_replication` en *false*:

   ```
   DATABASE_CONFIGURATION:
     _merge: true
     slave_connection:
       default:
         synchronous_replication: false
   ```

1. Vuelva a implementar y realice acciones de front-end como iniciar sesión, agregar al carro de compras o realizar un pedido.

<u>Resultados esperados</u>:

La conexión esclava permanece habilitada cuando `synchronous_replication` se establece en *false*.

<u>Resultados reales</u>:

La conexión esclava se deshabilitó cuando `synchronous_replication` se estableció en *false*, lo que provoca la sobrecarga de la base de datos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
