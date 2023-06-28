---
title: Práctica recomendada para configurar la conexión esclava MySQL
description: Obtenga información sobre cómo configurar la conexión esclava MySQL para sitios de Adobe Commerce implementados en la infraestructura en la nube.
role: Developer
feature: Best Practices
exl-id: d65bc80a-c4ec-4ea4-aff1-110592838201
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Práctica recomendada para configurar la conexión esclava MySQL

>[!NOTE]
>
>Este artículo contiene términos de software estándar en la industria que algunos pueden encontrar racistas, sexistas u opresivos y que pueden hacer que el lector se sienta herido, traumatizado o no deseado. El Adobe de está trabajando para eliminar estos términos de nuestro código, documentación y experiencias de usuario.

Para los sitios de Adobe Commerce implementados en la arquitectura Pro de la infraestructura en la nube, Adobe recomienda habilitar la conexión esclava MYSQL para la base de datos de forma predeterminada.

Adobe Commerce puede leer varias bases de datos de forma asincrónica. Al habilitar la conexión esclava MYSQL, Adobe Commerce utiliza una conexión de solo lectura a la base de datos para recibir tráfico de solo lectura en un nodo no maestro. El rendimiento mejora mediante el equilibrio de carga cuando solo un nodo gestiona el tráfico de lectura-escritura.

## Versiones afectadas

Adobe Commerce en infraestructura en la nube, arquitectura Pro

## Configurar la conexión esclava de MySQL

En Adobe Commerce en la infraestructura en la nube, puede anular la configuración predeterminada para la conexión esclava de MYSQL estableciendo el [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) variable. Establezca esta variable como true para utilizar automáticamente una conexión de solo lectura con la base de datos.

**Para habilitar la conexión esclava MySQL**:

1. En la estación de trabajo local, cambie al directorio del proyecto.

1. En el `.magento.env.yaml` , configure el `MYSQL_USE_SLAVE_CONNECTION` a true.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Confirme el `.magento.env.yaml` cambios de archivo y push al entorno remoto.

   Una vez que la implementación se completa correctamente, la conexión esclava MySQL se activa para el entorno de nube.

Obtenga más información sobre cómo personalizar el entorno de la nube anulando la configuración de Commerce existente con [Variables de entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) en el _guía de Adobe Commerce sobre infraestructura en la nube_.

## Información adicional

- [Cuello de botella de carga alta MySQL en Adobe Commerce en la infraestructura en la nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Prácticas recomendadas de bases de datos para Adobe Commerce en infraestructura en la nube](database-on-cloud.md)
