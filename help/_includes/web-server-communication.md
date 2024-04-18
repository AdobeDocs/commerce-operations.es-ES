---
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---
# Comunicación segura con el servidor web

En este tema se describe un ejemplo de cómo proteger la comunicación entre el servidor web y el motor de búsqueda (Elasticsearch u OpenSearch) mediante una combinación de cifrado de Seguridad de la capa de transporte (TLS) y [Autenticación básica HTTP](https://datatracker.ietf.org/doc/html/rfc2617). Si lo desea, también puede configurar otros tipos de autenticación. Proporcionamos referencias para esa información.

(Un término más antiguo, Capa de sockets seguros (SSL), se utiliza con frecuencia indistintamente con TLS. En este tema, nos referimos a *TLS*.)

>[!WARNING]
>
>A menos que se indique lo contrario, todos los comandos de este tema deben escribirse como un usuario con `root` privilegios.

## Recommendations

Recomendamos lo siguiente:

* El servidor web utiliza TLS.

  TLS está fuera del ámbito de este tema; sin embargo, le recomendamos encarecidamente que utilice un certificado real en producción y no un certificado autofirmado.

* El motor de búsqueda se ejecuta en el mismo host que un servidor web. La ejecución del motor de búsqueda y del servidor web en hosts diferentes está fuera del ámbito de este tema.

  La ventaja de colocar el motor de búsqueda y el servidor web en el mismo host es que hace imposible interceptar la comunicación cifrada. El servidor web del motor de búsqueda no tiene por qué ser el mismo que el servidor web de Adobe Commerce; por ejemplo, Adobe Commerce puede ejecutar Apache y Elasticsearch/OpenSearch puede ejecutar nginx.

  Si el motor de búsqueda está expuesto a la web pública, debe configurar la autenticación. Si la instancia del motor de búsqueda está protegida dentro de la red, es posible que no sea necesario. Póngase en contacto con su proveedor de alojamiento para determinar qué medidas de seguridad debe implementar para proteger su instancia.

## Más información sobre TLS

Consulte uno de los siguientes recursos:

* Apache

   * [Procedimientos para el cifrado fuerte de Apache 2.4](https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html)
   * [Cómo crear un certificado SSL en Apache para Ubuntu 14.04 (tutorial de Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)
   * [Configuración de un servidor web seguro para SSL con CentOS (wiki de CentOS)](https://wiki.centos.org/HowTos/Https)

* Nginx

   * [Terminación SSL de Nginx](https://www.nginx.com/resources/admin-guide/nginx-ssl-termination/)
   * [Cómo crear un certificado SSL en Nginx para Ubuntu 14.04 (tutorial de Digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)
   * [Instalación del certificado SSL de Nginx (digicert)](https://www.digicert.com/ssl-certificate-installation-nginx.htm)
