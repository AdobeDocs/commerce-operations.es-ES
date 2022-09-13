---
title: Requisitos previos del motor de búsqueda
description: Siga estos pasos para instalar y configurar el software de motor de búsqueda admitido para las instalaciones locales de Adobe Commerce y Magento Open Source.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 0%

---


# Requisitos previos del motor de búsqueda

A partir de Adobe Commerce y Magento Open Source 2.4, todas las instalaciones deben configurarse para utilizar [Elasticsearch](https://www.elastic.co) o [OpenSearch](https://opensearch.org/) como el [catálogo](https://glossary.magento.com/catalog) solución de búsqueda.

>[!NOTE]
>
>La compatibilidad con OpenSearch se ha agregado en la versión 2.4.4. OpenSearch es una ramificación de Elasticsearch compatible. Todas las instrucciones para configurar el Elasticsearch 7 se aplican a OpenSearch. [Migración de Elasticsearch a OpenSearch](../../../upgrade/prepare/opensearch-migration.md) proporciona instrucciones para cambiar a OpenSearch.

## Versiones compatibles

Debe instalar y configurar Elasticsearch u OpenSearch antes de instalar Adobe Commerce o Magento Open Source 2.4.4.

Consulte la [Requisitos del sistema](../../system-requirements.md) para obtener información de la versión específica.

## Configuración recomendada

Recomendamos lo siguiente:

* [Configure nginx en su motor de búsqueda](configure-nginx.md)
* [Configurar Apache para su motor de búsqueda](configure-apache.md)

## Ubicación de instalación

Las siguientes tareas suponen que ha configurado el sistema según el siguiente diagrama:

![Diagrama del motor de búsqueda](../../../assets/installation/search-engine-config.svg)

El diagrama anterior muestra:

* La aplicación Commerce y el motor de búsqueda están instalados en diferentes hosts.

   La ejecución en hosts separados requiere el uso de proxys para funcionar. (La agrupación del motor de búsqueda está fuera del ámbito de esta guía, pero puede encontrar más información en la [documentación sobre clústeres de Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/guide/current/distributed-cluster.html).)

* Cada host tiene su propio servidor web; los servidores web no tienen por qué ser iguales.

   Por ejemplo, la aplicación Commerce puede ejecutar Apache y el motor de búsqueda puede ejecutar nginx.

* Ambos servidores web utilizan Transport Layer Security (TLS).

   La configuración de TLS está fuera del alcance de nuestra documentación.

Las solicitudes de búsqueda se procesan de la siguiente manera:

1. El servidor web de comercio recibe una solicitud de búsqueda de un usuario, que la reenvía al servidor del motor de búsqueda.

   El motor de búsqueda se configura para que se conecte al host y al puerto del proxy. Recomendamos el puerto SSL del servidor web (de forma predeterminada, 443).

1. El servidor web del motor de búsqueda (que escucha en el puerto 443) envía la solicitud al servidor del motor de búsqueda (de forma predeterminada, escucha en el puerto 9200).

1. El acceso al motor de búsqueda está protegido por la autenticación HTTP Basic. Para que una solicitud llegue al motor de búsqueda, debe desplazarse por SSL *y* proporcione un nombre de usuario y una contraseña válidos.

1. El motor de búsqueda procesa la solicitud.

1. La comunicación regresa a lo largo de la misma ruta, con el servidor web Elasticsearch actuando como un proxy inverso seguro.

## Requisitos previos

Las tareas analizadas en esta sección requieren lo siguiente:

* [Firewall y SELinux](#firewall-and-selinux)
* [Instalación del Kit de desarrollo de software de Java (JDK)](#install-the-java-software-development-kit)
* [Instalación del motor de búsqueda](#install-the-search-engine)
* [Actualización del Elasticsearch](#upgrading-elasticsearch)

### Firewall y SELinux

El software relacionado con la seguridad (iptables, SELinux, AppArmor) puede configurarse de forma predeterminada para bloquear la comunicación entre subsistemas. Puede ser una buena idea comprobarlas si hay problemas.

#### Configuración de reglas para iptables y SELinux

Para configurar reglas que permitan la comunicación con el firewall o SELinux habilitado, consulte los siguientes recursos:

* [procedimiento iptables](https://help.ubuntu.com/community/IptablesHowTo)
* [Cómo editar las reglas iptables (proyecto fedora)](https://fedoraproject.org/wiki/How_to_edit_iptables_rules)
* [Introducción a SELinux (CentOS.org)](https://www.centos.org)
* [Wiki sobre procedimientos de SELinux (CentOS.org)](https://wiki.centos.org/HowTos/SELinux)

### Instalación del Kit de desarrollo de software de Java

Para determinar si Java ya está instalado, introduzca el siguiente comando:

```bash
java -version
```

Si el mensaje `java: command not found` , debe instalar el SDK de Java como se describe en la siguiente sección.

Consulte una de las siguientes secciones:

* [Instalación del JDK más reciente en CentOS](#install-the-jdk-on-centos)
* [Instale el JDK más reciente en Ubuntu](#install-the-jdk-on-ubuntu)

#### Instalación del JDK en CentOS

Consulte esta [Tutorial sobre océano digital](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora#install-oracle-java-8).

Asegúrese de instalar el JDK y *not* el JRE.

```bash
yum -y install java-1.8.0-openjdk
```

>[!NOTE]
>
>Es posible que la versión 8 de Java no esté disponible para todos los sistemas operativos. Por ejemplo, puede [buscar la lista de paquetes disponibles para Ubuntu](https://packages.ubuntu.com/).

#### Instalar el JDK en Ubuntu

Para instalar JDK 1.8 en Ubuntu, introduzca los siguientes comandos como usuario con `root` privilegios:

```bash
apt-get -y update
```

```bash
apt-get install -y openjdk-8-jdk
```

Para ver otras opciones, consulte [documentación de oracle](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html).

### Instalación del motor de búsqueda

Seguir [Instalación del Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) o [Instalación y configuración de OpenSearch](https://opensearch.org/docs/latest/opensearch/install/index/) para los pasos específicos de la plataforma.

Para comprobar que el Elasticsearch funciona, introduzca el siguiente comando en el servidor en el que se está ejecutando:

```bash
curl -XGET '<host>:9200/_cat/health?v&pretty'
```

Se muestra un mensaje similar al siguiente:

```terminal
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks
1519701563 03:19:23  elasticsearch green           1         1      0   0    0    0        0             0
```

Para verificar que OpenSearch funciona, introduzca los siguientes comandos:

```bash
curl -XGET https://<host>:9200 -u 'admin:admin' --insecure
```

```bash
curl -XGET https://<host>:9200/_cat/plugins?v -u 'admin:admin' --insecure
```

## Actualización del Elasticsearch

Consulte [Actualización del Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) para obtener instrucciones completas sobre cómo realizar copias de seguridad de los datos, detectar posibles problemas de migración y probar actualizaciones antes de implementarlas en producción. Según la versión actual del Elasticsearch, puede que sea necesario o no reiniciar el clúster completo.

Elasticsearch requiere JDK 1.8 o superior. Consulte [Instalación del Kit de desarrollo de software de Java](#install-the-java-software-development-kit) para comprobar qué versión de JDK está instalada.

## Recursos adicionales

Para obtener más información, consulte [documentación del Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html).
