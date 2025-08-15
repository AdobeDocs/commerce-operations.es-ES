---
title: Prácticas recomendadas de configuración de MySQL
description: Aprenda cómo los déclencheur MySQL y las conexiones esclavas afectan el rendimiento del sitio de Commerce y cómo utilizarlos de forma eficaz.
role: Developer
feature: Best Practices
exl-id: 7c2f51fd-9333-4954-bd35-79c2de3cb2ff
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Prácticas recomendadas de configuración de MySQL

>[!NOTE]
>
>Este tema contiene términos de software estándar en la industria que algunos pueden encontrar racistas, sexistas u opresivos y que pueden hacer que el lector se sienta herido, traumatizado o no deseado. Adobe está trabajando para eliminar estos términos del código, la documentación y las experiencias de los usuarios.

## Déclencheur

Este artículo explica cómo evitar problemas de rendimiento al utilizar déclencheur MySQL. Los déclencheur se utilizan para registrar cambios en tablas de auditoría.

### Productos y versiones afectados

- Adobe Commerce local
- Adobe Commerce en la infraestructura en la nube

>[!WARNING]
>
>Para Adobe Commerce en proyectos en la nube, pruebe siempre los cambios de configuración en el entorno de ensayo antes de cambiar la configuración del entorno de producción.

### Impactos en el rendimiento

Los déclencheur se interpretan como código, lo que significa que MySQL no los precompila.

Al conectarse al espacio de transacciones de la consulta, los déclencheur agregan sobrecarga a un analizador e intérprete para cada consulta realizada con la tabla. Los déclencheur comparten el mismo espacio de transacciones que las consultas originales y, mientras que estas consultas compiten por bloqueos en la tabla, los déclencheur compiten de forma independiente por bloqueos en otra tabla.

Esta sobrecarga adicional puede afectar negativamente al rendimiento del sitio si se utilizan muchos déclencheur.

>[!WARNING]
>
>Adobe Commerce no admite ningún déclencheur personalizado en la base de datos de Adobe Commerce porque los déclencheur personalizados pueden producir incompatibilidades con versiones futuras de Adobe Commerce. Para conocer las prácticas recomendadas, consulte [Directrices generales de MySQL](../../../installation/prerequisites/database/mysql.md) en la documentación de Adobe Commerce.

### Uso efectivo

Para evitar problemas de rendimiento al utilizar déclencheur, siga estas directrices:

- Si tiene déclencheur personalizados que escriben algunos datos cuando se ejecuta el déclencheur, muévalos para que escriban directamente en las tablas de auditoría. Por ejemplo, agregando una consulta adicional en el código de la aplicación, después de la consulta para la que pretendía crear el déclencheur.
- Revise los déclencheur personalizados existentes y considere la posibilidad de eliminarlos y escribir directamente en las tablas desde la aplicación. Compruebe los déclencheur existentes en la base de datos utilizando la instrucción SQL [`SHOW TRIGGERS`](https://dev.mysql.com/doc/refman/8.0/en/show-triggers.html).
- Para obtener ayuda, preguntas o inquietudes adicionales, [envíe un ticket de soporte de Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=es&#submit-ticket).

## Conexiones esclavas

Adobe Commerce puede leer varias bases de datos de forma asincrónica. Si se espera una carga alta para la base de datos MySQL de un sitio Commerce implementado en la arquitectura Cloud Infrastructure Pro, Adobe recomienda habilitar la conexión esclava MYSQL.

Al habilitar la conexión esclava MYSQL, Adobe Commerce utiliza una conexión de solo lectura a la base de datos para recibir tráfico de solo lectura en un nodo no maestro. El rendimiento mejora mediante el equilibrio de carga cuando solo un nodo gestiona el tráfico de lectura-escritura.

### Versiones afectadas

Adobe Commerce en infraestructura en la nube, solo arquitectura Pro

### Configuración

En Adobe Commerce en la infraestructura de la nube, puede anular la configuración predeterminada para la conexión esclava MYSQL estableciendo la variable [MYSQL_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=es#mysql_use_slave_connection). Establezca esta variable en `true` para utilizar automáticamente una conexión de solo lectura con la base de datos.

**Para habilitar la conexión esclava MySQL**:

1. En la estación de trabajo local, cambie al directorio del proyecto.

1. En el archivo `.magento.env.yaml`, establezca `MYSQL_USE_SLAVE_CONNECTION` como verdadero.

   ```
   stage:
     deploy:
       MYSQL_USE_SLAVE_CONNECTION: true
   ```

1. Confirme los cambios de archivo de `.magento.env.yaml` y envíelos al entorno remoto.

   Una vez que la implementación se completa correctamente, la conexión esclava MySQL se activa para el entorno de nube.
