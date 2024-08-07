---
title: Información general de implementación
description: Obtenga información sobre las estrategias de implementación para la aplicación de Commerce.
feature: Configuration, Deploy
exl-id: d5ed6fb3-2dd2-49df-802b-6d712ecd9ccf
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---

# Información general de implementación

En estos temas se describe el proceso de implementación de la aplicación Commerce en un sitio de producción para la versión 2.2 y posteriores de Adobe Commerce. Adobe recomienda este método de implementación para cualquier persona con un sitio grande que no desee experimentar tiempo de inactividad durante la implementación.

Si implementa Commerce en un solo equipo y puede tolerar cierto tiempo de inactividad durante la implementación, consulte [Implementación de un solo equipo](../deployment/single-machine.md).

## Implementación de canalización

Con la versión 2.2 de Commerce, el Adobe introdujo la _implementación de canalización_ como una nueva forma de implementar en producción con un tiempo de inactividad mínimo. Este proceso de implementación se produce en diferentes sistemas y proporciona una forma de mantener configuraciones coherentes para todos los sistemas de implementación de canalización. Es un modelo sencillo pero eficaz que le permite separar las opciones de configuración ordinarias de las específicas del sistema (como host y puerto) o de las opciones confidenciales (como nombres y contraseñas).

Para utilizar la implementación de canalización, Adobe supone lo siguiente:

- Un integrador de sistemas experimentado con un excelente conocimiento de las opciones de configuración de Adobe Commerce.
- Gestionar un sitio de Commerce de gran tamaño (miles de unidades de stock (SKU)) y desea reducir al mínimo el tiempo de inactividad en el sitio de producción.
- Conocido sobre programación PHP.
- Con experiencia en métodos de control de código fuente.
- El código se encuentra en un repositorio de control de código fuente. En esta guía, suponemos que está utilizando un repositorio basado en Git.

### Menor tiempo de inactividad

Al implementar recursos estáticos y compilar código en un equipo independiente del sistema de producción, se minimiza el tiempo de inactividad. El tiempo de inactividad del sistema de producción se limita a la cantidad de tiempo necesaria para transferir archivos estáticos y código compilado al servidor.

## Sistemas de implementación

Utilizamos los siguientes términos para describir los sistemas implicados en la implementación.

- **Sistema de desarrollo**: equipo en el que los desarrolladores trabajan para personalizar código e instalar extensiones, temáticas y paquetes de idioma desde Commerce Marketplace. Además, puede realizar todos los cambios de configuración en el sistema de desarrollo. Puede tener muchos sistemas de desarrollo.

- **Sistema de compilación**: un sistema en el que se implementan recursos estáticos y se compila código para el sistema de producción. Debido a que estos recursos se crean en un sistema que no está en producción, se minimiza el tiempo de inactividad del sistema de producción.

  El sistema de compilación no tiene que tener Commerce instalado. Solo necesita el código Commerce, pero no se requiere ninguna conexión a la base de datos. Además, el sistema de compilación no necesita ser un servidor físicamente independiente.

- **Sistema de ensayo**—_Opcional_. Si lo desea, puede configurar un sistema de ensayo para utilizarlo en las pruebas finales de todo el código integrado, incluidas las pruebas de aceptación de usuarios (UAT). Configure un sistema de ensayo del mismo modo que configura un sistema de producción. Excepto por el hecho de que el ensayo no es su tienda en directo y no procesa pedidos de clientes, es idéntico al de producción.

- **Sistema de producción**—Su tienda en vivo. Aquí debe realizar cambios mínimos directos en la configuración y, desde luego, nada que no se haya probado en una instancia de ensayo. Si es posible, realice cambios de configuración con [Parches de datos](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) que se hayan probado en una instancia de ensayo/desarrollo.

## Otros métodos de implementación

Opcionalmente, puede utilizar otros métodos de implementación, como:

- Copia segura con SCP o rsync
- [Capistrano](https://capistranorb.com/documentation/overview/what-is-capistrano)
- La [herramienta de implementación](https://deployer.org/)

## Administrar la configuración

Modelado después del [factor 3 en el diseño de la aplicación de 12 factores](https://12factor.net/config), Commerce ahora almacena la configuración de cada sistema en el propio sistema. (Las opciones de configuración de desarrollo se almacenan en el sistema de desarrollo, las opciones de producción se almacenan en el sistema de producción).

Proporcionamos una forma de sincronizar la configuración de sus sistemas:

- **Configuración compartida**: opciones que no son específicas del sistema ni confidenciales.

  La configuración compartida es la configuración que desea que sea coherente en los sistemas de desarrollo y producción. Establezca la configuración compartida en Admin en su sistema de desarrollo (o Adobe Commerce en la infraestructura en la nube _integration_).

  El archivo de configuración compartida, `app/etc/config.php`, debe incluirse en el control de código fuente para que pueda compartirse entre los sistemas de desarrollo, compilación y producción.

- **Configuración específica del sistema**: opciones que varían según el sistema, como los puertos y los nombres de host del motor de búsqueda.

- **Configuración confidencial**: configuración que debería _no_ estar en el control de código fuente porque expone información de identificación personal (PII) o configuraciones como claves de API o contraseñas.

  El archivo de configuración específico del sistema, `app/etc/env.php`, debería _no_ incluirse en el control de código fuente o compartirse de otro modo entre sistemas. En su lugar, use los comandos [`magento config:set` y `magento:sensitive:set` ](../cli/set-configuration-values.md) para proporcionar valores para esas configuraciones en el sistema de producción.

>[!INFO]
>
>Estos nuevos métodos para administrar la configuración son opcionales. No es necesario, pero se recomienda encarecidamente que los utilice.

La mayoría de las veces, las opciones de configuración establecidas en la configuración compartida, específica del sistema o confidencial no se pueden editar en el Administrador. Esto ayuda a mantener la coherencia de la configuración en todos los sistemas. (Opcionalmente, puede usar el comando [`magento config:set` ](../cli/set-configuration-values.md) sin la opción `--lock` para configurar opciones que se pueden editar en el Administrador).

Cada opción de configuración de Commerce tiene una _ruta de configuración_ única. Para establecer un valor para una opción de configuración, puede utilizar un comando CLI o una variable de entorno para establecer el valor de esa ruta de configuración en un sistema específico.
