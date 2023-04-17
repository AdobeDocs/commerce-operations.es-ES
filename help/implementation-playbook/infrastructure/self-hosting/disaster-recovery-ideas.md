---
title: Recuperación ante desastres de Adobe Commerce con alojamiento propio
description: Obtenga información sobre ideas y conceptos de recuperación ante desastres de alojamiento propio y prácticas recomendadas para tener en cuenta.
landing-page-description: Aprenda algunos conceptos y cosas que debe tener en cuenta al alojar Adobe Commerce por su cuenta.
short-description: Aprenda estrategias y conceptos de recuperación ante desastres para hospedarse usted mismo en Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 6e361169889c8fe1c176d3a3283d52699dfa3b85
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Ideas de recuperación ante desastres de Adobe Commerce con alojamiento propio

La recuperación ante desastres para este artículo abarca una implementación fallida. Aunque todo el proceso puede no ser el mismo, se aplican principios similares. Un desastre puede deberse a una implementación de producción fallida, a que el servidor no responde, al descubrimiento de una explotación y muchos otros escenarios. Cuando el proceso de recuperación para una implementación fallida solo requiera dos pasos simples, una recuperación de una explotación puede ser mucho más difícil. Debido a la complejidad de los entornos, las variaciones de alojamiento y otras complejidades, este artículo proporciona ideas y conceptos, pero usted debe continuar la investigación por su cuenta. De este modo, puede asegurarse de diseñar una estrategia que se adapte a sus necesidades comerciales.

## El proceso de recuperación de prácticas a menudo

Práctica, Práctica, Práctica. Hay una razón por la que las prácticas aparecen primero en la lista de recuperación ante desastres. Es muy fácil configurar un plan de recuperación pero nunca ejecutarlo. Si no practica lo suficiente, es probable que se produzcan errores, que se pierdan pasos y que una recuperación real tarde más tiempo. La cadencia para la recuperación de sus prácticas depende de usted y de sus socios comerciales. Hacer que el proceso de recuperación sea un evento anual puede ser lo suficientemente bueno, pero una conversación profunda con quienes toman decisiones en su empresa debería incluir varios temas clave. Estos temas les ayudan a comprender por qué la práctica es importante y debe esperarse. A continuación se presentan algunos temas que ayudan a iniciar la conversación:

* La práctica reduce el tiempo de inactividad real cuando se produce un evento real. Si un simulacro de práctica interrumpe el sitio durante una hora al año, puede reducir el tiempo de inactividad real de un evento real en varias horas. No es raro que la recuperación de un sitio tome ocho horas o más. Al practicar este evento a menudo puede reducir la cantidad de tiempo que tarda cada fase y puede recuperarse más rápido.
* El tiempo de inactividad programado para estas ejecuciones de prácticas puede coincidir con parches del servidor, ajustes de inventario o cualquier otra cosa que se deba hacer en un programa regular.
* Practique diferentes escenarios en lugar del mismo. Tómese el tiempo ocasionalmente para realizar una recuperación completa desde una fecha anterior. Esto incluye cosas como encontrar y usar una copia archivada de la base de datos, retroceder el código para que coincida con la fecha. Una más fácil podría ser la recuperación de una implementación fallida, donde simplemente debe volver a la confirmación anterior.
* Compruebe que el proceso de recuperación funcione, a veces las bases de datos archivadas pueden dañarse. Al hacerlo, garantiza que todo se pueda recuperar y que funcione. Encontrar y restaurar una base de datos antigua lleva tiempo, se debe saber cuánto tiempo puede durar esta parte del proceso.
* Compruebe que todos los cambios en las configuraciones estén documentados. Esto garantiza que cualquier recuperación de una base de datos anterior obtenga cualquier cambio de configuración nuevo que sea funcional. Por ejemplo, si la clave de API ha cambiado a su procesador de pagos en los últimos días. Al tener un buen proceso de administración de cambios, encontrar estas actualizaciones clave hace que el proceso vaya según lo planeado.

## Backups de base de datos

Las copias de seguridad de la base de datos deben ser bastante regulares. No es inusual tener instantáneas por hora, diarias, semanales y mensuales. Con el tiempo, los backups deberían trasladarse al almacenamiento de información a largo plazo. Este almacenamiento de información a largo plazo puede ocurrir siempre que el equipo de tecnología o del negocio decida que ha pasado suficiente tiempo para que probablemente ya no se necesite una rápida recuperación de ellos. Una recuperación desde un almacenamiento de información a largo plazo agrega tiempo al proceso de recuperación, por lo que se debe tener cuidado al decidir cuándo debe ocurrir esto. Las copias de seguridad de la base de datos deben automatizarse y no depender de la interacción humana. Esto garantiza que tenga suficientes para proporcionar un proceso de recuperación seguro y predecible. Esto también contribuye a cualquier actividad forense, si es necesaria, viable y fiable. Es posible que encuentre la necesidad de realizar una investigación forense después de que se detecte una explotación, o cuando intente diagnosticar cuándo se produjo un fraude con tarjeta de crédito o incluso quizás cuando alguien se unió a su sitio web. No hay límite en la forma en que se utilizan estas copias de seguridad, pero tener una buena cadencia de copias de seguridad es su gracia de ahorro cuando realmente lo necesita.

El siguiente es un ejemplo de política de retención de datos:

* Cada ocho horas. Las copias de seguridad deben ser fácilmente accesibles.
* Copias de seguridad diarias durante los últimos siete días y debe ser fácilmente accesible. Una copia de ellos podría ser un candidato para ser trasladado fuera del sitio.
* Las copias de seguridad semanales de las últimas cuatro semanas consideran la posibilidad de trasladarse fuera del sitio.
* copias de seguridad mensuales durante los últimos tres meses se han trasladado fuera del sitio.
* Los backups más antiguos se trasladan al almacenamiento de información a largo plazo fuera del sitio.

## Infraestructura como código

Esta metodología significa que dispone de herramientas y código para reconstruir partes o toda la infraestructura de su proyecto. Esto puede ser necesario cuando un servidor experimenta problemas y debe quitarse de su uso. Poder poner rápidamente en línea un nuevo servidor, implementar el código, realizar cualquier configuración de PHP, Nginx o Apache, y lo que sea, significa automáticamente menos tiempo de inactividad. Incluso los pasos bien documentados en un libro de ejecución son más fáciles de configurar, para ejecutar los pasos toma mucho más tiempo. Además, considere el error humano que puede ocurrir mientras está bajo estrés para volver a poner en línea un sitio que no responde.

## Base de datos secundaria

El uso de una base de datos secundaria puede resultar útil por algunos motivos:

* Caliente de espera si hay una falla de unidad primaria
* Permitir para solicitudes listas de la aplicación
* Permitir que se produzca mysqldump y permitir que se produzcan transacciones normales sin bloquear la base de datos
* Permite el acceso a los datos desde una fuente de datos externa sin reducir la capacidad de los sitios web de realizar transacciones de información para las solicitudes de los clientes.

La base de datos secundaria se puede usar como `warm standby`. Esto puede entrar en juego cuando está considerando cómo recuperarse de un error de base de datos principal. La promoción de la base de datos secundaria a primaria es más compleja que la reconstrucción y restauración de una base de datos a una instancia de Mysql recién creada. Esto reduce el downtime real durante una operación de recuperación.

Existe la oportunidad de desviar algunas de las solicitudes a la base de datos secundaria. Si se utiliza este método, se sugiere hacer que la base de datos secundaria sea de solo lectura. Al permitir que la aplicación de Adobe Commerce utilice esta base de datos secundaria para operaciones de lectura, ayuda al tomar algunas de las solicitudes de lectura y permitir que la base de datos secundaria responda. Sin embargo, este cambio solo representa entre el 30 y el 50 % de todas las solicitudes, pero cualquier carga que se pueda eliminar de la base de datos principal es una victoria.

## Crear un plan de implementación que incluya una reversión

Cada implementación debe incluir un plan de reversión. Sí, cada implementación. Si lo planeas, nunca te sorprendes y estás listo para el mal evento. A veces, las actualizaciones de código más simples pueden fallar catastróficamente por cualquier motivo.

Tenga en cuenta esta historia real de un equipo que comprometió una solicitud de extracción pequeña y sencilla para ejecutar un cambio de esquema en la base de datos. A medida que el despliegue iba de 1 minuto, a 5, luego a 10, y el equipo se preocupaba más. Lo que no pudieron verificar y considerar hasta este punto fue cualquier discrepancia de la base de datos de producción en comparación con la base de datos de ensayo. Tenían una práctica común de eliminar todos los datos de clientes al actualizar el entorno de ensayo con una copia de producción. Esto significa que todas sus pruebas y control de calidad anteriores a esto reflejaban la implementación deberían tardar unos minutos en completarse. En realidad, tenían más de 20 millones de clientes y este pequeño cambio de esquema tardaba un tiempo excepcionalmente largo en completarse. Debido a que no tenían idea de cuánto tiempo iba a tardar esto, se vieron obligados a finalizar el proceso mysql y revertir la implementación.

La preparación de un proceso de reversión para una implementación tarda unos minutos porque el proceso general será similar. Sin embargo, debería tomarse el tiempo de documentar exactamente a qué confirmación restablecería el HEAD del repositorio de Git. Debe documentar exactamente qué instantánea de base de datos utilizar o dónde encontrar la actual si siempre está en el mismo lugar. Han definido momentos en los que se debe debatir el estado de la implementación y en los que se aplica automáticamente. Por ejemplo, si alguna implementación tarda más de 15 minutos, pregunte al administrador del proyecto y a otros accionistas si las cosas deben continuar. Sin embargo, ejecute automáticamente el proceso de reversión y notifique a todas las partes interesadas si el proceso tarda 45 minutos, independientemente de si el administrador del proyecto y el arquitecto dudan en él.

Asegúrese de que varias personas estén involucradas en todo el proceso y en cada fase. Hacer que los desarrolladores de nivel medio revisen el proceso de implementación, el procedimiento de reversión y la ubicación de los archivos es una buena manera de involucrarlos. Con el tiempo, realizarán los pasos para que entiendan que todo el proceso es clave para el éxito a largo plazo. Asegúrese de que todos estén facultados para desactivar un despliegue. Darle a tu equipo esta cantidad de voz es empoderar y recompensar. Si un desarrollador junior realmente siente que algo falta, debería sentirse obligado a hablar y dejar que se escuche su precaución. Permita que el arquitecto y los jefes de proyecto confirmen o mitiguen su miedo. Es importante contar con un equipo fuerte que esté buscando el proyecto y que mantenga su historial de implementaciones incorrectas.

## Verifique el acceso a la administración de nombres de dominio, DMS, SSL, WAF

Dado que los nombres de dominio caducan, los registros DNS se pueden modificar accidentalmente, los certificados SSL pueden caducar y mucho más; asegurándose de tener la capacidad de iniciar sesión y verificar que la conectividad debería suceder con frecuencia. Hacer este simple chequeo cada trimestre te mantiene seguro de que sabes exactamente dónde están las cosas, especialmente en una emergencia. No asuma que su DNS se administra en su registrador solo para averiguar que lo ha administrado en Amazon. Estos registros no se utilizan con frecuencia, por lo que es muy probable que olvide dónde están. No confíe únicamente en la documentación escrita para nombres de usuario y contraseñas. Inicie sesión en cada uno de ellos y compruebe que las configuraciones que está buscando se administren realmente en el mismo. Con demasiada frecuencia las cosas cambian durante el recambio de la administración o la adquisición de la empresa y solo una persona sabe lo que ha sucedido, porque son ellos los que hicieron la actualización. No sabían que se basaba en un documento de palabras compartido en el que se documentaba la ubicación, el nombre de usuario y la contraseña. Encuentre un proceso de comprobación que tenga sentido para usted y su organización, pero hacerlo cada tres o seis meses es un buen punto de partida.

{{$include /help/_includes/hosting-related-links.md}}
