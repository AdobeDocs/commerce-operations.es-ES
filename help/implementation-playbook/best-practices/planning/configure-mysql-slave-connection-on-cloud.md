---
title: Práctica recomendada para configurar la conexión esclava de MySQL
description: Aprenda a configurar la conexión esclava de MySQL para los sitios de Adobe Commerce implementados en la infraestructura de la nube.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---


# Práctica recomendada para configurar la conexión esclava de MySQL

Para los sitios de Adobe Commerce implementados en la arquitectura de la infraestructura de nube Pro, Adobe recomienda habilitar la conexión esclava de MYSQL para la base de datos de forma predeterminada.

Adobe Commerce puede leer varias bases de datos asincrónicamente.  Cuando se habilita la conexión esclava de MYSQL, Adobe Commerce utiliza una conexión de solo lectura con la base de datos para recibir tráfico de solo lectura en un nodo no maestro. Esto mejora el rendimiento mediante el equilibrio de carga, ya que solo un nodo necesita gestionar el tráfico de lectura y escritura.

## Versiones afectadas

Adobe Commerce en infraestructura en la nube, arquitectura Pro

## Configuración de la conexión esclava de MySQL

La configuración de la conexión esclava de MYSQL la establece el [MYSQL_SLAVE_CONNECTION](https://devdocs.magento.com/cloud/env/variables-deploy.html#mysql_use_slave_connection) implementar variable en Adobe Commerce en el archivo de configuración de entorno de infraestructura de nube, `.magento.env.yaml`. Establezca esta variable como `true` para activar la conexión.

Para habilitar la conexión esclava de MySQL:

1. Edite su `.magento.env.yaml` y verifique que `MYSQL_USE_SLAVE_CONNECTION` está activada.

   ```
   stage:
      deploy:
      MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Confirme los cambios y, a continuación, colóquelos en la rama de entorno para implementarlos.

   Una vez que la implementación se haya completado correctamente, la conexión esclava de MySQL está habilitada en su infraestructura de nube.

## Información adicional

- [Variables de entorno](https://devdocs.magento.com/cloud/env/variables-intro.html)
- [Cuello de botella de alta carga de MySQL en Adobe Commerce en infraestructura de nube](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/mysql-high-load-bottleneck-in-magento-commerce-cloud.html?lang=en)
- [Prácticas recomendadas de bases de datos para Adobe Commerce en infraestructura en la nube](database-on-cloud.md)

>!![NOTE]
Somos conscientes de que este artículo todavía puede contener términos de software estándar de la industria que algunos pueden encontrar racistas, sexistas u opresivos y que pueden hacer que el lector se sienta herido, traumatizado o no bienvenido. Adobe está trabajando para eliminar estos términos de nuestro código, documentación y experiencias de usuario.
