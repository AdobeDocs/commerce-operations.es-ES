---
source-git-commit: 475dbc056ac3e6a00c8f794259bb0fbf04143687
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---
# Comunicación segura del servidor web

En este tema se analiza un ejemplo de cómo asegurar la comunicación entre el servidor web y el motor de búsqueda (Elasticsearch o OpenSearch) mediante la combinación del cifrado Seguridad de la capa de transporte (TLS) y [Autenticación básica HTTP](https://datatracker.ietf.org/doc/html/rfc2617). Opcionalmente, también puede configurar otros tipos de autenticación; proporcionamos referencias para esa información.

(Un término más antiguo, Secure Sockets Layer (SSL), se utiliza con frecuencia de forma intercambiable con TLS. En este tema, nos referimos a *TLS*.)

>[!WARNING]
>
>A menos que se indique lo contrario, todos los comandos de este tema deben introducirse como usuario con `root` privilegios.

## Recommendations

Recomendamos lo siguiente:

* El servidor web utiliza TLS.

   TLS está fuera del alcance de este tema; sin embargo, recomendamos encarecidamente que utilice un certificado real en producción y no un certificado autofirmado.

* El motor de búsqueda se ejecuta en el mismo host que un servidor web. Ejecutar el motor de búsqueda y el servidor web en diferentes hosts está fuera del alcance de este tema.

   La ventaja de poner el motor de búsqueda y el servidor web en el mismo host es que hace imposible la interceptación de comunicaciones cifradas. El servidor web del motor de búsqueda no tiene por qué ser el mismo que el servidor web de Adobe Commerce o Magento Open Source; por ejemplo, Adobe Commerce puede ejecutar Apache y Elasticsearch/OpenSearch puede ejecutar nginx.

   Si el motor de búsqueda está expuesto a la web pública, debe configurar la autenticación. Si la instancia del motor de búsqueda está protegida dentro de la red, puede que no sea necesario. Póngase en contacto con su proveedor de alojamiento para determinar qué medidas de seguridad debe implementar para proteger su instancia.

## Más información sobre TLS

Consulte uno de los siguientes recursos:

* Apache

   * [Cómo implementar el cifrado seguro de Apache 2.4](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [Cómo crear un certificado SSL en Apache para Ubuntu 14.04 (tutorial de Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [Configuración de un servidor web seguro SSL con CentOS (wiki de CentOS)](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Terminación de Nginx SSL](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [Cómo crear un certificado SSL en Nginx para Ubuntu 14.04 (tutorial de Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Instalación del certificado SSL de Nginx (digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
