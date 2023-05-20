---
title: Recuperación ante desastres de Adobe Commerce con alojamiento propio
description: Obtenga información sobre ideas y conceptos de recuperación ante desastres con alojamiento propio y prácticas recomendadas que debe tener en cuenta.
landing-page-description: Conozca algunos conceptos y cosas que debe tener en cuenta a la hora de alojar Adobe Commerce por su cuenta.
short-description: Aprenda estrategias y conceptos de recuperación ante desastres para alojar Adobe Commerce usted mismo.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: cab6213b-da44-498f-b5c1-e7f89e95038e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1771'
ht-degree: 0%

---

# Ideas de recuperación ante desastres de Adobe Commerce con alojamiento propio

La recuperación ante desastres de este artículo incluye una implementación fallida. Aunque todo el proceso puede no ser el mismo, se aplican principios similares. Un desastre puede deberse a un error en la implementación de la producción, a que el servidor deja de responder, al descubrimiento de una vulnerabilidad y a muchos otros escenarios. Cuando el proceso de recuperación de una implementación fallida puede requerir solo dos simples pasos, la recuperación de una explotación puede ser mucho más difícil. Debido a la complejidad de los entornos, las variaciones de alojamiento y otras complejidades, este artículo proporciona ideas y conceptos, pero es necesario que continúe la investigación por su cuenta. De esta forma, puede asegurarse de diseñar una estrategia que se adapte a sus necesidades empresariales.

## Practicar el proceso de recuperación a menudo

Práctica, Práctica, Práctica. Hay una razón por la que las prácticas aparecen primero en la lista de recuperación ante desastres. Es muy fácil configurar un plan de recuperación, pero nunca ejecutarlo. Si no practica lo suficiente, es propenso a errores, pasos perdidos y probablemente haga que una recuperación real tarde más. La cadencia de la recuperación de su práctica depende de usted y de sus socios comerciales. Hacer del proceso de recuperación un evento anual puede ser suficiente, pero una conversación profunda con los responsables de la toma de decisiones de su empresa debe incluir varios temas clave. Estos temas les ayudan a comprender por qué practicar es importante y se debe esperar. A continuación se indican algunos temas que ayudan a iniciar la conversación:

* La práctica reduce el tiempo de inactividad real cuando un evento se produce de forma real. Si una ejecución en seco de práctica elimina el sitio durante una hora al año, puede reducir el tiempo de inactividad real de un evento real en varias horas. No es raro que una recuperación de un sitio tarde ocho horas o más. Al practicar este evento a menudo puede reducir la cantidad de tiempo que cada fase toma, y usted es capaz de recuperarse más rápido.
* El tiempo de inactividad programado para estas ejecuciones de práctica puede coincidir con parches de servidor, ajustes de inventario o cualquier otra cosa que deba hacerse de forma regular.
* Practicar diferentes escenarios en lugar del mismo. Tómese el tiempo de vez en cuando, para hacer una recuperación completa de una fecha anterior. Esto incluye tareas como buscar y utilizar una copia archivada de la base de datos, o revertir el código para que coincida con la fecha. Una más fácil podría ser la recuperación de una implementación fallida, en la que simplemente debe volver a la confirmación anterior.
* Compruebe que el proceso de recuperación funciona realmente, a veces las bases de datos archivadas pueden dañarse. Al hacerlo, garantiza que todo se pueda recuperar y funcione. La búsqueda y restauración de una base de datos antigua lleva tiempo. Debe saberse durante cuánto tiempo puede durar esta parte del proceso.
* Compruebe que todos los cambios en las configuraciones estén documentados. Esto garantiza que cualquier recuperación de una base de datos anterior que obtenga cualquier cambio de configuración nuevo debe ser funcional. Por ejemplo, si su clave de API cambió a su procesador de pagos en los últimos días. Al tener un buen proceso de administración de cambios, la búsqueda de estas actualizaciones clave hace que el proceso vaya según lo planificado.

## Backups de BD

Las copias de seguridad deben ser bastante regulares. No es raro tener instantáneas por hora, diarias, semanales y mensuales. Las copias de seguridad deben trasladarse finalmente al almacenamiento a largo plazo. Este almacenamiento a largo plazo puede ocurrir siempre que el equipo empresarial o tecnológico decida que ha pasado el tiempo suficiente como para que probablemente ya no sea necesaria una rápida recuperación de los mismos. Una recuperación de un almacenamiento a largo plazo añade tiempo al proceso de recuperación, por lo que se debe tener cuidado al decidir cuándo debe ocurrir esto. Las copias de seguridad de la base de datos deben automatizarse y no depender de la interacción humana. Esto garantiza que tenga suficientes para proporcionar un proceso de recuperación seguro y predecible. Esto también ayuda en cualquier actividad forense, si tal actividad es necesaria, es factible y confiable. Es posible que encuentre una necesidad de investigación forense después de que se detecte un ataque, o cuando intente diagnosticar cuándo se produjo una actividad de fraude con tarjeta de crédito o incluso cuando alguien se unió a su sitio web. No hay límite en la forma en que usa estas copias de seguridad, pero tener una buena cadencia de copias de seguridad es su gracia cuando realmente la necesita.

A continuación se muestra un ejemplo de una directiva de retención de datos:

* Cada ocho horas. Las copias de seguridad deben ser fácilmente accesibles.
* Copias de seguridad diarias durante los últimos siete días y debe ser fácilmente accesible. Una copia de ellos podría ser candidata para ser trasladada fuera del sitio.
* Las copias de seguridad semanales de las últimas cuatro semanas consideran la posibilidad de trasladarse fuera del sitio.
* los backups mensuales de los últimos tres meses se han trasladado fuera del sitio.
* Las copias de seguridad más antiguas se trasladan al almacenamiento a largo plazo fuera del sitio.

## Infraestructura como código

Esta metodología significa que dispone de herramientas y código para reconstruir partes o toda la infraestructura del proyecto. Esto puede ser necesario cuando un servidor tiene problemas y debe desconectarse. Poder poner rápidamente en línea un nuevo servidor, implementar el código, hacer cualquier configuración de PHP, Nginx o Apache, y lo que sea, automáticamente significa menos tiempo de inactividad. Incluso los pasos bien documentados en un libro de ejecución son más fáciles de configurar, para ejecutar los pasos toma mucho más tiempo. Además, considere el error humano que puede ocurrir mientras está bajo estrés para volver a poner en línea un sitio que no responde.

## Base de datos secundaria

El uso de una base de datos secundaria puede resultar útil por varios motivos:

* Espera en espera si hay un fallo en la unidad principal
* Permitir solicitudes listas desde la aplicación
* Permitir que se produzca mysqldump y permitir que se produzcan transacciones normales sin bloquear la base de datos
* Permite el acceso a los datos desde una fuente de datos externa sin reducir la capacidad de los sitios web para realizar transacciones de información cuando los clientes lo solicitan.

La base de datos secundaria se puede utilizar como `warm standby`. Esto puede entrar en juego cuando esté considerando cómo recuperarse de un error de base de datos principal. La promoción de la base de datos secundaria a la principal es menos compleja que la reconstrucción y restauración de una base de datos en una instancia de Mysql recién creada. Esto reduce el tiempo de inactividad real durante una operación de recuperación.

Existe la oportunidad de desviar algunas de las solicitudes a la base de datos secundaria. Si se utiliza este método, se recomienda hacer que la base de datos secundaria sea de solo lectura. Permitir que la aplicación de Adobe Commerce utilice esta base de datos secundaria para operaciones de lectura ayuda tomando algunas de las solicitudes de lectura y permitiendo que la base de datos secundaria responda. Sin embargo, este cambio solo representa el 30-50 % de todas las solicitudes, pero cualquier carga que pueda retirar de la base de datos principal es una victoria.

## Creación de un plan de implementación que incluya una reversión

Cada implementación debe incluir un plan de reversión. Sí, en cada implementación. Si lo planeas, nunca te sorprenderás y estarás listo para el mal evento. A veces, las actualizaciones de código más sencillas pueden fallar catastróficamente por cualquier razón.

Considere esta historia real de un equipo que confirmó una pequeña y simple solicitud de extracción para ejecutar un cambio de esquema en la base de datos. A medida que el despliegue pasó de 1 minuto, a 5, luego 10, y el equipo se preocupó más. Lo que no pudieron verificar y considerar hasta este punto fue cualquier discrepancia de la base de datos de producción en comparación con la base de datos provisional. Normalmente se eliminaban todos los datos de clientes al actualizar el entorno de ensayo con una copia de la producción. Esto significaba que todas las pruebas y el control de calidad anteriores a esto reflejaban que la implementación debería tardar solo unos minutos en completarse. En realidad, tenían más de 20 millones de clientes y este pequeño cambio de esquema estaba tardando mucho tiempo en completarse. Debido a que no tenían idea de cuánto tiempo esto iba a tomar realmente, se vieron obligados a terminar el proceso mysql y revertir la implementación.

La preparación para un proceso de reversión para una implementación tarda solo unos minutos, ya que el proceso general va a ser similar. Sin embargo, debe tomarse el tiempo para documentar exactamente a qué confirmación restablecería el HEAD del repositorio de Git de nuevo. Debe documentar exactamente qué instantánea de base de datos utilizar o dónde encontrar la actual si siempre está en el mismo lugar. Tener tiempos definidos en los que se debe discutir el estado de la implementación y en los que las cosas surten efecto automáticamente. Por ejemplo, si una implementación tarda más de 15 minutos, pregunte al administrador del proyecto y a otras partes interesadas si las cosas deben continuar. Sin embargo, ejecute automáticamente el proceso de reversión y notifique a todas las partes interesadas si el proceso tarda 45 minutos, independientemente de si el administrador y el arquitecto del proyecto vacilan al respecto.

Asegúrese de que varias personas estén involucradas en todo el proceso y en cada fase. Hacer que los desarrolladores de nivel medio revisen el proceso de implementación, el procedimiento de reversión y la ubicación de los archivos es una buena manera de involucrarlos. Eventualmente estarán realizando los pasos para que entiendan que todo el proceso es clave para el éxito a largo plazo. Asegúrese de que todos estén capacitados para cancelar una implementación. Dar a su equipo esta cantidad de voz es empoderador y gratificante. Si un desarrollador junior realmente siente que algo falta, debería sentirse obligado a hablar y dejar que se escuche su precaución. Deje que el arquitecto y los gerentes de proyectos confirmen o mitiguen su miedo. Es importante tener un equipo sólido que esté pendiente del proyecto y que mantenga su historial de implementaciones sin problemas.

## Verificar el acceso a la administración de nombres de dominio, DMS, SSL, WAF

Debido a que los nombres de dominio caducan, los registros DNS se pueden modificar accidentalmente, los certificados SSL pueden caducar y mucho más; asegúrese de que tiene la capacidad de iniciar sesión y comprobar que la conectividad debería suceder con frecuencia. Hacer esta simple comprobación cada trimestre le mantiene seguro de que sabe exactamente dónde se encuentran las cosas, especialmente en una emergencia. No asuma que su DNS está administrado en su registrador solo para saber si lo ha administrado en Amazon. Estos registros no se utilizan con frecuencia, por lo que olvidar dónde están es una alta probabilidad. No confíe únicamente en la documentación escrita para nombres de usuario y contraseñas. Inicie sesión en cada una de ellas y verifique que las configuraciones que busca se gestionan allí. Muy a menudo las cosas cambian durante la rotación de la gerencia o la adquisición de la compañía y solo una persona sabe lo que pasó, porque ellos son los que hicieron la actualización. No sabían que confiaba en un documento de palabra compartida para saber cuál era la ubicación, el nombre de usuario y la contraseña. Encuentre un proceso de comprobación que tenga sentido para usted y su organización, pero hacerlo cada tres o seis meses es un buen punto de partida.

{{$include /help/_includes/hosting-related-links.md}}
