---
title: Información general sobre la implementación
description: Obtenga más información sobre las estrategias de implementación para la aplicación Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---


# Información general sobre la implementación

En estos temas se analiza el proceso de implementación de la aplicación Commerce en un sitio de producción para Adobe Commerce versión 2.2 y posteriores. Adobe recomienda este método de implementación para todo aquel que tenga un sitio grande y no desee experimentar downtime durante la implementación.

Si implementa Commerce en un único equipo y puede tolerar cierto tiempo de inactividad durante la implementación, consulte [Implementación de una sola máquina](../deployment/single-machine.md).

## Implementación de canalización

Con la versión 2.2 de Commerce, se ha introducido Adobe _implementación de canalización_ como una nueva forma de implementar en producción con un tiempo de inactividad mínimo. Este proceso de implementación se produce en diferentes sistemas y proporciona una manera de mantener configuraciones coherentes para todos los sistemas de implementación de canalización. Es un modelo sencillo pero potente que le permite separar los ajustes de configuración normales de los ajustes específicos del sistema (como host y puerto) o de los ajustes confidenciales (como nombres y contraseñas).

Para utilizar la implementación de canalización, Adobe supone que:

- Un integrador de sistemas experimentado con excelentes conocimientos de las opciones de configuración de Adobe Commerce.
- Administración de un sitio de comercio grande (miles de unidades de mantenimiento de existencias (SKU)) y desea reducir al mínimo el tiempo de inactividad del sitio de producción.
- Conocido sobre la programación PHP.
- Experiencia con métodos de control de código fuente.
- El código se encuentra en un repositorio de control de código fuente. En esta guía, suponemos que está utilizando un repositorio basado en Git.

### Reducción del tiempo de inactividad

Al implementar recursos estáticos y compilar código en un equipo independiente del sistema de producción, se minimiza el tiempo de inactividad. El tiempo de inactividad en el sistema de producción está limitado a la cantidad de tiempo necesario para transferir archivos estáticos y código compilado al servidor.

## Sistemas de implementación

Utilizamos los términos siguientes para describir los sistemas involucrados en la implementación.

- **Sistema de desarrollo**—Máquina en la que los desarrolladores trabajan para personalizar el código; e instale extensiones, temas y paquetes de idioma de Commerce Marketplace. Además, puede realizar todos los cambios de configuración en el sistema de desarrollo. Puede tener muchos sistemas de desarrollo.

- **Generar sistema**: un sistema en el que se implementan recursos estáticos y se compila código para el sistema de producción. Como estos recursos se crean en un sistema que no está en producción, el tiempo de inactividad de su sistema de producción se minimiza.

   El sistema de compilación no tiene que tener Commerce instalado. Solo necesita el código de comercio, pero no se requiere ninguna conexión de base de datos. Además, el sistema de compilación no necesita ser un servidor físicamente separado.

- **Sistema de ensayo**—_Opcional_. Si lo desea, puede configurar un sistema de ensayo para utilizarlo en la prueba final de todo el código integrado, incluida la prueba de aceptación del usuario (UAT). Configure un sistema de ensayo del mismo modo que configura un sistema de producción. Excepto por el hecho de que el ensayo no es su tienda activa y no procesa los pedidos de los clientes, es idéntico a la producción.

- **Sistema de producción**: su tienda en directo. Aquí debe realizar cambios mínimos de configuración directa y, desde luego, nada que no se haya probado en una instancia de ensayo. Si es posible, realice cambios de configuración con [Parches de datos](https://developer.adobe.com/commerce/php/development/components/declarative-schema/patches/) que se han probado en una instancia de Ensayo/Desarrollo.

## Otros métodos de implementación

Opcionalmente, puede utilizar otros métodos de implementación, como:

- Copia segura con SCP o rsync
- [Capistrano](https://capistranorb.com/documentation/overview/what-is-capistrano)
- La variable [Herramienta de implementación](https://deployer.org/)

## Administrar la configuración

Modelado después de [factor 3 en el diseño de aplicaciones de 12 factores](https://12factor.net/config), Commerce ahora almacena la configuración de cada sistema del propio sistema. (Los ajustes de configuración de desarrollo se almacenan en el sistema de desarrollo, los ajustes de producción se almacenan en el sistema de producción).

Proporcionamos una forma de sincronizar la configuración de sus sistemas:

- **Configuración compartida**: configuraciones que no son específicas del sistema ni confidenciales.

   La configuración compartida es una configuración que desea que sea coherente en los sistemas de desarrollo y producción. Establezca la configuración compartida en Admin en su desarrollo (o Adobe Commerce en la infraestructura de nube) _integración_).

   El archivo de configuración compartido, `app/etc/config.php`, debe incluirse en el control de código fuente para que se pueda compartir entre sistemas de desarrollo, compilación y producción.

- **Configuración específica del sistema**: configuraciones que varían según el sistema, como los nombres de host y puertos del motor de búsqueda.

- **Configuración confidencial**—Configuración que debería _not_ estar en control de código fuente porque exponen información de identificación personal (PII) o configuraciones como claves de API o contraseñas.

   El archivo de configuración específico del sistema, `app/etc/env.php`, debería _not_ se incluirán en el control de código fuente o se compartirán de otro modo entre sistemas. En su lugar, utilice el [`magento config:set` y `magento:sensitive:set` comandos](../cli/set-configuration-values.md) para proporcionar valores para esa configuración en el sistema de producción.

>[!INFO]
>
>Estos nuevos métodos para administrar la configuración son opcionales. No es necesario, pero se recomienda encarecidamente que los utilice.

La mayoría de las veces, las opciones de configuración que configure en la configuración compartida, específica del sistema o confidencial no se pueden editar en el Administrador. Esto ayuda a mantener la configuración uniforme en todos los sistemas. (Si lo desea, puede usar la variable [`magento config:set` command](../cli/set-configuration-values.md) sin el `--lock` para configurar las opciones que se pueden editar en Admin.)

Cada opción de configuración de Commerce tiene una _ruta de configuración_. Para establecer un valor para una opción de configuración, puede utilizar un comando CLI o una variable de entorno para establecer el valor de esa ruta de configuración en un sistema específico.
