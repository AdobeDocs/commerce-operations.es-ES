---
title: Práctica recomendada para configurar la conexión esclava de MySQL
description: Aprenda a configurar la conexión esclava de MySQL para los sitios de Adobe Commerce implementados en la infraestructura de la nube.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: cb86772e9ceabc580ec32ad6ae1206a71ea03946
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# Práctica recomendada para configurar la conexión esclava de MySQL

>[!NOTE]
>
>Este artículo contiene términos de software estándar de la industria que algunos pueden encontrar racistas, sexistas u opresivos y que pueden hacer que el lector se sienta herido, traumatizado o no bienvenido. Adobe está trabajando para eliminar estos términos de nuestro código, documentación y experiencias de usuario.

Para los sitios de Adobe Commerce implementados en la arquitectura de la infraestructura de nube Pro, Adobe recomienda habilitar la conexión esclava de MYSQL para la base de datos de forma predeterminada.

Adobe Commerce puede leer varias bases de datos asincrónicamente. Cuando se habilita la conexión esclava de MYSQL, Adobe Commerce utiliza una conexión de solo lectura con la base de datos para recibir tráfico de solo lectura en un nodo no maestro. El rendimiento mejora mediante el equilibrio de carga cuando solo un nodo gestiona el tráfico de lectura y escritura.

## Versiones afectadas

Adobe Commerce en infraestructura en la nube, arquitectura Pro

## Configuración de la conexión esclava de MySQL

En Adobe Commerce en la infraestructura de nube, puede anular la configuración predeterminada para la conexión esclava de MYSQL estableciendo la variable [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#mysql_use_slave_connection) variable. Establezca esta variable como true para utilizar automáticamente una conexión de solo lectura con la base de datos.

**Para habilitar la conexión esclava de MySQL**:

1. En la estación de trabajo local, cambie al directorio del proyecto.

1. En el `.magento.env.yaml` , establezca la variable `MYSQL_USE_SLAVE_CONNECTION` a true.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Confirmar el `.magento.env.yaml` cambios de archivos e inserte en el entorno remoto.

   Una vez que la implementación se haya completado correctamente, la conexión esclava de MySQL está habilitada para el entorno de la nube.

Obtenga más información sobre cómo personalizar el entorno de la nube anulando la configuración de comercio existente con [Variables de entorno](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/configure-env-yaml.html#environment-variables) en el _Guía de infraestructura de Adobe Commerce en la nube_.

## Información adicional

- [Cuello de botella de alta carga de MySQL en Adobe Commerce en infraestructura de nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Prácticas recomendadas de bases de datos para Adobe Commerce en infraestructura en la nube](database-on-cloud.md)
