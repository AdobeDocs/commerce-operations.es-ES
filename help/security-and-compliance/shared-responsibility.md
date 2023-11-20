---
title: Responsabilidad compartida
description: Obtenga información sobre las responsabilidades de seguridad de cada parte involucrada en su proyecto de infraestructura de Adobe Commerce en la nube.
source-git-commit: d216418c69cb972e93c04b5d5cc0a8ab0495653d
workflow-type: tm+mt
source-wordcount: '1562'
ht-degree: 0%

---


# Modelo de seguridad de responsabilidad compartida

Adobe Commerce en la infraestructura en la nube es una oferta de plataforma como servicio (PaaS) que se basa en un modelo de seguridad de responsabilidad compartida. El Adobe, el comerciante, el proveedor de servicios en la nube y el proveedor de red de entrega de contenido (CDN) tienen una responsabilidad distinta de mantener la seguridad de Adobe Commerce en la aplicación de infraestructura en la nube y el código y las extensiones específicos del comerciante.

Este enfoque permite a los comerciantes diseñar e implementar una solución altamente flexible, personalizable y escalable que se adapta mejor a sus requisitos comerciales, al mismo tiempo que minimiza las responsabilidades y los costes operativos.

En general, el Adobe es responsable de desarrollar y mantener el código de aplicación principal seguro, mantener la seguridad de la plataforma, garantizar la compatibilidad de la plataforma con SOC 2 y PCI y su compatibilidad con los componentes de tecnología compatibles con PCI (por ejemplo, PHP, Redis), y responder a los problemas de seguridad relacionados con la plataforma principal. Adobe también es responsable de trabajar con los proveedores de servicios en la nube y los socios de CDN para resolver los problemas que puedan surgir.

Los comerciantes son responsables de mantener el código personalizado seguro y las integraciones con aplicaciones de terceros, garantizar el desarrollo de aplicaciones seguras, obtener la certificación PCI si lo solicita el procesador de pagos del comerciante y reaccionar ante los incidentes de seguridad.

## responsabilidades de Adobe

El Adobe es responsable de la seguridad y disponibilidad del entorno de Adobe Commerce en la nube y del código de solución principal de Adobe Commerce en la nube. Además, el Adobe es responsable de las actividades y mecanismos necesarios para mantener la seguridad de la solución Adobe Commerce en la infraestructura en la nube, lo que incluye:

- Aplicación de parches y seguridad de nivel de servidor para aplicaciones compatibles con Adobe Commerce en infraestructuras en la nube, como almacenamiento de datos en la nube y funciones de búsqueda
- Realizar pruebas de penetración y análisis del código de infraestructura principal de Adobe Commerce en la nube
- Realización de revisiones/auditorías semestrales de la solución y la administración de permisos de los proveedores de servicios públicos en la nube (IAM) (requisito de cumplimiento de PCI)
- Realizar revisiones/auditorías semestrales de usuarios autorizados, incluidos empleados y contratistas del Adobe (requisito de conformidad con el PCI)
- Realización de pruebas y documentación anuales de la funcionalidad de backup y restauración
- Configuración de servidores de seguridad perimetrales y de servidor
- Conexión y configuración de Adobe Commerce en el repositorio de la infraestructura en la nube
- Definir, probar, implementar y documentar planes de recuperación ante desastres (DR) para las áreas dentro del ámbito de responsabilidad de Adobe
- Definición de reglas de firewall de aplicaciones web de plataforma global (WAF)
- Protección del sistema operativo (SO)
- Implementación y mantenimiento de la integración de soluciones de red de distribución de contenido (CDN) y administración del rendimiento de las aplicaciones (APM) con Adobe Commerce en la infraestructura en la nube
- Emisión de actualizaciones periódicas de seguridad y de otro tipo para el código de infraestructura central de Adobe Commerce en la nube (la aplicación de parches es responsabilidad del comerciante)
- Administración de soporte comercial y control de acceso de soporte (por ejemplo, Zendesk)
- Monitorización, registro y corrección de incidentes de seguridad relacionados con Adobe Commerce en la infraestructura de la plataforma de la nube
- Monitorización de las operaciones de la plataforma y asistencia las 24 horas del día y los 7 días de la semana para Adobe Commerce en comerciantes de infraestructura en la nube
- Aprovisionamiento de los entornos de producción y ensayo
- Evaluación de posibles amenazas de seguridad para las operaciones e infraestructura de la plataforma
- Escalar la computación, el almacenamiento, la red y otros recursos, tal como se describe en el contrato de nivel de servicio (SLA) con el comerciante
- Configuración de DNS (Adobe Commerce solo en la infraestructura de la plataforma de la nube)
- Prueba de la plataforma para detectar vulnerabilidades de seguridad

Mientras que Adobe mantiene la certificación PCI para la infraestructura y los servicios utilizados en el funcionamiento de la solución de Adobe Commerce en la nube, los comerciantes son responsables de la conformidad de los procesos de código personalizado, sistema y red, y la organización.

El Adobe también garantiza la disponibilidad de la infraestructura del comerciante según lo acordado en el SLA aplicable.

## Responsabilidades del comerciante

El comerciante es responsable de seguir las prácticas recomendadas de seguridad para su instancia específica y personalizada de Adobe Commerce en la solución de infraestructura en la nube, y para:

- Añadir al repositorio los archivos de configuración de Adobe Commerce en la nube necesarios
- La aplicación de parches de seguridad y de otro tipo a su solución personalizada de Adobe Commerce en la nube inmediatamente después de su lanzamiento por Adobe.
- Aplicar parches de seguridad y de otro tipo a todas las extensiones y códigos personalizados, inmediatamente después de su lanzamiento por el proveedor
- Creación, implementación y prueba de archivos VCL de barniz personalizados
- Diseñar, asignar temas, instalar, integrar y proteger la solución de Adobe Commerce personalizada en infraestructura en la nube, incluidas todas las extensiones y el código personalizados
- Concesión y revocación del acceso de usuario a la instancia de Adobe Commerce del comerciante en la configuración, aplicación y plataforma de la infraestructura en la nube
- Gestión de los problemas de seguridad relacionados con la red interna del comerciante, los servidores, la infraestructura y cualquier aplicación personalizada creada en Adobe Commerce en la plataforma de infraestructura en la nube
- Instalación de la herramienta de integración de la línea de comandos (CLI) de Adobe Commerce en la infraestructura de la nube
- Mantener el nivel requerido de conformidad con PCI de la aplicación personalizada y otros procesos internos, según se define en las directrices de PCI-DSS

  >[!NOTE]
  >
  >La conformidad con PCI del comerciante se basa en las certificaciones PCI de Adobe Commerce en la infraestructura en la nube y el proveedor de alojamiento en la nube para minimizar las áreas que deben revisarse.

- Ejecución de análisis ASV de PCI y corrección de problemas en el Adobe Commerce principal en el código y la plataforma de la infraestructura en la nube
- Monitorización de todas las actividades de la aplicación que puedan revelar una posible amenaza para la seguridad, incluidas las pruebas de penetración, los análisis de vulnerabilidades y los registros
- Monitorización y respuesta a incidentes de seguridad, incluidos análisis forenses, corrección y creación de informes relacionados con la solución Adobe Commerce on cloud Infrastructure del comerciante y las cuentas de usuario
- Obtención de un proveedor de DNS y configuración y mantenimiento de registros DNS específicos del comerciante
- Ejecución de pruebas de rendimiento en la aplicación personalizada
- Protección del acceso a las cuentas de plataforma, al acceso a instancias y a la aplicación
- Pruebas y control de calidad de la aplicación personalizada
- Mantener la seguridad de cualquier sistema o red que el comerciante conecte con la aplicación de infraestructura en la nube de Adobe Commerce

## Responsabilidades del proveedor de Cloud Service

Adobe se basa en proveedores de servicios en la nube bien establecidos para alojar la infraestructura de servidores en la nube de Adobe Commerce en la nube. Estos proveedores son responsables de la seguridad de la red, incluido el enrutamiento, la conmutación y la seguridad de la red perimetral a través de sistemas de cortafuegos y sistemas de detección de intrusiones (IDS). Los proveedores de servicios en la nube también son responsables de la seguridad física de los centros de datos que alojan la solución Adobe Commerce en la infraestructura en la nube y de la seguridad medioambiental de los centros de datos.

Los proveedores de servicios en la nube también son responsables de:

- Mantener las certificaciones PCI DSS, SOC 2 e ISO 27001 para sus servicios en la nube
- Fijación del hipervisor
- Protección del centro de datos, incluido el acceso físico y de red

## Responsabilidades del proveedor de CDN

La solución de Adobe Commerce en la nube utiliza proveedores de CDN para acelerar el tiempo de carga de página, almacenar en caché el contenido y purgar instantáneamente el contenido obsoleto. Estos proveedores también son responsables de los problemas de seguridad directamente relacionados con su CDN o que afectan a ella, y de definir y mantener las reglas WAF de CDN.

## Gráfico de responsabilidades de seguridad

El siguiente gráfico utiliza el modelo RACI (R — Responsable, A — Responsable, C — Consultado, I — Informado) para representar visualmente las responsabilidades de seguridad de cada parte en el ecosistema en relación con el modelo de responsabilidad compartida de Adobe Commerce en la infraestructura en la nube:

<table>
<thead>
  <tr>
    <th>Tarea</th>
    <th>Adobe</th>
    <th>Comerciante</th>
    <th>Proveedor de servicios en la nube</th>
    <th>Proveedor de CDN</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Aplicación de Adobe Commerce en parches de infraestructura en la nube</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Aplicación de parches a servicios de soporte<br>(por ejemplo, Nginx, MySQL)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Definición de reglas WAF de origen</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Definición de reglas WAF de CDN</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Implementación de reglas WAF de plataforma</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Implementación de reglas WAF de CDN</td>
    <td>A</td>
    <td>I</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Corrección de errores principales en Adobe Commerce en el código de infraestructura de la nube</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Lanzamiento de Adobe Commerce en parches de infraestructura en la nube</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Escalado (computación y almacenamiento)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Escala (PaaS/cuadrícula)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Garantizar el acceso al código fuente, incluido repo.magento.com</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Instalación de Adobe Commerce en la herramienta CLI de infraestructura en la nube</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Añadir archivos de configuración de Adobe Commerce en la nube al repositorio</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Creación de un proyecto para el comerciante (IU de incorporación)</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Conexión de repositorios a Adobe Commerce en la infraestructura de la nube</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Configuración del repositorio de origen<sup>1</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Creación de un usuario para el administrador de versiones (IU de incorporación)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Implementación del código en producción</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Implementar el código en el ensayo</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Integración de aplicaciones y extensiones externas</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Instalación de extensiones</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Personalización de Adobe Commerce en la infraestructura en la nube</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Prueba del rendimiento de Adobe Commerce personalizado en la infraestructura en la nube</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Prueba de la aplicación personalizada</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Temática y diseño de la aplicación personalizada</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
    <tr>
    <td>Creación, implementación y prueba de VCL de barniz personalizados</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Configuración de DNS (solo infraestructura de plataforma)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Desarrollo de la extensión de CDN y corrección de errores</td>
    <td>A</td>
    <td>C</td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Incorporación de CDN</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>CDN de soporte<sup>2</sup></td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Configuración de New Relic APM/infraestructura</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Instalación de New Relic APM/Infrastructure</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Soporte de New Relic APM/infraestructura</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Configuración De Nginx<sup>3</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Obtención del proveedor DNS (solo Pro)</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Protección del sistema operativo</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Aprovisionamiento de los entornos de producción y ensayo</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Acceder a Zendesk para Adobe Commerce en la infraestructura en la nube</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Resolviendo problemas de seguridad del comerciante</td>
    <td>C</td>
    <td>R</td>
    <td></td>
    <td>C</td>
  </tr>
  <tr>
    <td>Solución de problemas de seguridad de Adobe Commerce en la nube</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Solución de problemas de seguridad de CDN</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td>R</td>
  </tr>
  <tr>
    <td>Resolver problemas de seguridad de APM</td>
    <td>A</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Asistencia al Adobe en la investigación de seguridad (software)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Asistencia al Adobe en la investigación de seguridad (análisis/auditorías)</td>
    <td>R</td>
    <td>C</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Realización de exploraciones ASV PCI</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Remediación de Adobe Commerce en exploraciones PCI de infraestructura en la nube<sup>4</sup></td>
    <td>R</td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Corrección de exploraciones PCI PaaS</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Administración de secretos de plataforma y sistema operativo</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Administración de Adobe Commerce en claves de cifrado de infraestructura en la nube</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Análisis de Adobe Commerce personalizado en instancias de infraestructura en la nube</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Monitorización de registros de seguridad</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Administración de IAM y permisos para Adobe Commerce en la infraestructura en la nube</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Administración de los controles de acceso de soporte (Teleport)</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Control del soporte y acceso del comerciante</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Pruebas anuales y documentación del plan de recuperación ante desastres de Adobe y backup y restauración</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Pruebas y documentación anuales del plan de recuperación ante desastres</td>
    <td>R</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
<tfoot>
  <tr>
    <td colspan="5">
      <p><sup><strong>1</strong></sup> Solo si el repositorio de Adobe Commerce en la nube se utiliza como repositorio principal. El uso de otros repositorios externos es responsabilidad exclusiva del comerciante.</p>
      <p><sup><strong>2</strong></sup> El Adobe de proporciona compatibilidad de nivel 1 para problemas con proveedores de CDN.</p>
      <p><sup><strong>3</strong></sup> Algunos controles Ngnix son configurados por el comerciante para sus aplicaciones y son su responsabilidad.</p>
      <p><sup><strong>4</strong></sup> Para PCI, los requisitos de prueba de penetración se comparten entre el Adobe y el comerciante.</p>
    </td>
  </tr>
</tfoot>
</table>
