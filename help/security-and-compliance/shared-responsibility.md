---
title: Modelo operativo y de seguridad de responsabilidad compartida
description: Obtenga información sobre las responsabilidades de seguridad de cada parte involucrada en su proyecto de infraestructura de Adobe Commerce en la nube.
exl-id: f3cc1685-e469-4e30-b18e-55ce10dd69ce
source-git-commit: 76aafb88855f7f41db8e57b06cf0e82370b57302
workflow-type: tm+mt
source-wordcount: '2802'
ht-degree: 0%

---

# Modelo operativo y de seguridad de responsabilidad compartida

Adobe Commerce en la infraestructura en la nube es una oferta de plataforma como servicio (PaaS) que se basa en un modelo operativo y de seguridad de responsabilidad compartida. Estas responsabilidades se comparten entre Adobe, el comerciante, el proveedor de servicios en la nube y el proveedor de la red de entrega de contenido (CDN). Cada parte tiene la responsabilidad distinta de proteger y operar la aplicación de Adobe Commerce y el código específico del comerciante y las extensiones implementadas en la infraestructura en la nube.

Este modelo compartido permite a los comerciantes diseñar e implementar una solución altamente flexible, personalizable y escalable para satisfacer sus necesidades comerciales, al mismo tiempo que minimiza las responsabilidades y los costes operativos.

En general, el Adobe es responsable de lo siguiente:

- Desarrollo y mantenimiento del código de la aplicación principal segura
- Mantenimiento de la seguridad de la plataforma
- Garantizar que la plataforma sea compatible con SOC 2 y PCI y compatible con componentes de tecnología compatibles con PCI (por ejemplo, PHP, Redis)
- Respuesta a los problemas de seguridad relacionados con la plataforma principal
- Trabajar con proveedores de servicios en la nube y socios de CDN para resolver cualquier problema que se produzca

Los comerciantes son responsables de lo siguiente:

- Mantenimiento de la seguridad para el código personalizado y las integraciones con aplicaciones de terceros
- Garantizar el desarrollo seguro de aplicaciones
- Obtención de la certificación PCI si así lo solicita el procesador de pagos del comerciante
- Reacción y respuesta a incidentes de seguridad

## responsabilidades de Adobe

El Adobe es responsable de la seguridad y disponibilidad de Adobe Commerce en el entorno de la infraestructura en la nube y del código de la solución principal. Además, el Adobe es responsable de las actividades y mecanismos necesarios para mantener la seguridad de la solución Adobe Commerce en la infraestructura en la nube, lo que incluye:

- Aplicación de parches y seguridad de nivel de servidor para aplicaciones compatibles con Adobe Commerce en infraestructuras en la nube, como almacenamiento de datos en la nube y funciones de búsqueda
- Realizar pruebas de penetración y análisis del código de infraestructura principal de Adobe Commerce en la nube
- Realización de revisiones y auditorías semestrales de las soluciones y la administración de permisos de los proveedores de servicios de nube pública de identidad y acceso (IAM) (requisito de cumplimiento de PCI)
- Realizar revisiones y auditorías semestrales de los usuarios autorizados, incluidos los empleados y contratistas del Adobe (requisito de conformidad con el PCI)
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

Adobe mantiene la certificación PCI para la infraestructura y los servicios utilizados para la solución Adobe Commerce.  Los comerciantes son responsables de la conformidad de los procesos de código personalizado, sistema y red, y de la organización.

El Adobe también garantiza la disponibilidad de la infraestructura del comerciante según lo acordado en el SLA aplicable.

## Responsabilidades del comerciante

El comerciante es responsable de seguir las prácticas recomendadas de seguridad para su instancia específica y personalizada de Adobe Commerce en la solución de infraestructura en la nube:

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
  >Para minimizar las áreas que deben revisarse, la conformidad con PCI para el comerciante se basa en las certificaciones PCI de Adobe Commerce y el proveedor de alojamiento en la nube.

- Ejecución de análisis ASV de PCI y corrección de problemas en el Adobe Commerce principal en el código y la plataforma de la infraestructura en la nube
- Monitorización de todas las actividades de la aplicación que puedan revelar una posible amenaza para la seguridad, incluidas las pruebas de penetración, los análisis de vulnerabilidades y los registros
- Monitorización y respuesta a incidentes de seguridad, incluidos análisis forenses, corrección y creación de informes relacionados con la solución Adobe Commerce on cloud Infrastructure del comerciante y las cuentas de usuario
- Obtención de un proveedor de DNS y configuración y mantenimiento de registros DNS específicos del comerciante
- Ejecución de pruebas de rendimiento en la aplicación personalizada
- Protección del acceso a las cuentas de plataforma, al acceso a instancias y a la aplicación
- Pruebas y control de calidad de la aplicación personalizada
- Mantener la seguridad de cualquier sistema o red que el comerciante conecte con la aplicación de infraestructura en la nube de Adobe Commerce

## Responsabilidades del proveedor Cloud Service

Adobe se basa en proveedores de servicios en la nube bien establecidos para alojar la infraestructura de servidores en la nube de Adobe Commerce en la nube. Estos proveedores son responsables de la seguridad de la red, incluido el enrutamiento, la conmutación y la seguridad de la red perimetral a través de sistemas de cortafuegos y sistemas de detección de intrusiones (IDS). Los proveedores de servicios en la nube también son responsables de la seguridad física de los centros de datos que alojan la solución Adobe Commerce en la infraestructura en la nube y de la seguridad medioambiental de los centros de datos.

Los proveedores de servicios en la nube también son responsables de:

- Mantener las certificaciones PCI DSS, SOC 2 e ISO 27001 para sus servicios en la nube
- Fijación del hipervisor
- Protección del centro de datos, incluido el acceso físico y de red

## Responsabilidades del proveedor de CDN

La solución de Adobe Commerce en la nube utiliza proveedores de CDN para acelerar el tiempo de carga de página, almacenar en caché el contenido y purgar instantáneamente el contenido obsoleto. Estos proveedores también son responsables de los problemas de seguridad directamente relacionados con su CDN o que afectan a ella, y de definir y mantener las reglas WAF de CDN.

## Resumen de responsabilidades de seguridad

>[!BEGINSHADEBOX]

La siguiente tabla de resumen utiliza el modelo RACI para mostrar las responsabilidades de seguridad compartidas entre el Adobe, el comerciante y el proveedor de servicios en la nube:

**R** — Responsable
**A** — Responsable
**C** — Consultado
**I** — Informado

>[!ENDSHADEBOX]

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
    <td>Aplicación de parches a servicios de soporte<br>(Por ejemplo, Nginx o MySQL).</td>
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
    <td>Escala (PaaS y cuadrícula)</td>
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
    <td>Configuración de aplicaciones de infraestructura y APM de New Relic</td>
    <td></td>
    <td>R</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Instalación de aplicaciones de infraestructura y APM de New Relic</td>
    <td>R</td>
    <td>I</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Compatibilidad con aplicaciones de infraestructura y APM de New Relic</td>
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
    <td>Obtención de un proveedor DNS (solo Pro)</td>
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
      <p><sup><strong>3</strong></sup> El comerciante es responsable de cualquier control Ngnix que configure para sus aplicaciones.</p>
      <p><sup><strong>4</strong></sup> Para PCI, los requisitos de prueba de penetración se comparten entre el Adobe y el comerciante.</p>
    </td>
  </tr>
</tfoot>
</table>

## Resumen de responsabilidades operativas

>[!BEGINSHADEBOX]

Las siguientes tablas de resumen aclaran las responsabilidades operativas de Adobe y Comerciantes a la hora de desarrollar, implementar, mantener y proteger Adobe Commerce en la infraestructura en la nube.

>[!ENDSHADEBOX]

### Codificación y desarrollo

#### Código principal de Adobe Commerce

|     | Adobe | Comerciante |
| --- | --- | --- |
| Publicación de actualizaciones y parches en Adobe Commerce Core | R |     |
| Disponibilidad y aplicación de parches al sistema de archivos | R |  |
| Publicación de actualizaciones y parches en ECE-Tools | R |     |
| Calidad de aplicación principal de Adobe Commerce | R |     |

{style="table-layout:auto"}

#### Repositorio de códigos

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad de repo.magento.com | R |     |
| Disponibilidad de Adobe Commerce en el servidor Git de Cloud | R |     |
| Otros repositorios de código seleccionados por el comerciante (GitHub, Bitbucket, servidor Git alojado) |     | R |

{style="table-layout:auto"}

#### Cloud Docker

|     | Adobe | Comerciante |
| --- | --- | --- |
| Hacer que los contenedores de Cloud Docker estén disponibles para descargar | R |   |
| Implementación y configuración de Cloud Docker (opcional) |     | R |
| Cualquier otra configuración de desarrollo local |     | R |

{style="table-layout:auto"}

#### CLI DE COMMERCE CLOUD

|     | Adobe | Comerciante |
| --- | --- | --- |
| Calidad y actualización continuas de las herramientas ECE | R |   |
| Instalación de la última versión de herramientas ECE |     | R |

{style="table-layout:auto"}

#### Personalizaciones

|  | Adobe | Comerciante |
| --- | --- | --- |
| Módulos y código personalizados de Adobe Commerce |     | R |
| Extensiones |     | R |
| Integraciones personalizadas |     | R |

{style="table-layout:auto"}

#### Implementaciones

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad de la infraestructura para generar e implementar el código | R |   |
| Calidad continua de la canalización de configuración de creación e implementación de infraestructura | R |   |
| Configuración de la compilación y la implementación de contenido estático |     | R |
| Creación y ejecución de un proceso de gobernanza de implementación: criterios y administración de cambios |     | R |
| Implementación en el entorno de ensayo |     | R |
| Implementación en el entorno de producción |     | R |
| Reversiones de producción |     | R |

{style="table-layout:auto"}

#### Sincronización de entornos

Los comerciantes son responsables de sincronizar datos entre entornos.

#### Parches

|     | Adobe | Comerciante |
| --- | --- | --- |
| Instalación de actualizaciones y parches en ECE-Tools |     | R |
| Instalación de actualizaciones y parches en Adobe Commerce Core |     | R |

#### Disponibilidad del sitio web

|  | Adobe | Comerciante |
| --- | --- | --- |
| Aplicación de Adobe Commerce personalizada y sitios web asociados |     | R |

#### Rendimiento

|     | Adobe | Comerciante |
| --- | --- | --- |
| Optimización y ajuste de aplicaciones principales | R |   |
| Optimización y ajuste del código personalizado |     | R |
| Código Adobe Commerce personalizado |     | R |
| Pruebas de carga |     | R |
| Pruebas de rendimiento |     | R |

{style="table-layout:auto"}


#### Registros y monitorización

|     | Adobe | Comerciante |
| --- | --- | --- |
| Rotación de registros | R |   |
| Aplicación de Adobe Commerce personalizada | | R |
| Disponibilidad de los servicios de New Relic:<br>aplicación APM e integración de agentes, aplicación de infraestructura,<br>Registro e integración | R |   |
| Configuración de alertas de New Relic |     | R |
| Implementación del agente de New Relic en servidores PaaS |     | R |

{style="table-layout:auto"}

#### Depuración y aislamiento de problemas

|     | Adobe | Comerciante |
| --- | --- | --- |
| Depuración y aislamiento de problemas | R | R |
| Compatibilidad oportuna con la depuración y el proceso de aislamiento de problemas |     | R |

{style="table-layout:auto"}

### Configuración de aplicaciones y servicios

#### aplicación de Commerce

|     | Adobe | Comerciante |
| --- | --- | --- |
| Configuración de aplicación |     | R |
| Adición de dominios a la aplicación de Adobe Commerce (URL base) |     | R |
| Configuración de PaaS para utilizar las versiones de servicios admitidas por la versión de Adobe Commerce implementada<br><br>Por ejemplo, diferentes versiones de Commerce son compatibles con versiones específicas de PHP, Redis, etc. |     | R |

{style="table-layout:auto"}

#### Programación de tareas con trabajos cron

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad de trabajos cron predeterminados | R | |
| Calidad continua de los trabajos personalizados de cron |  | R |

{style="table-layout:auto"}

#### Agente de mensajes para el marco de cola de mensajes

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad del servicio RabbitMQ | R |   |
| Configuración de los ajustes predeterminados de RabbitMQ | R |   |
| Calidad y parches continuos de RabbitMQ | R |   |
| Envíe una solicitud de servicio para instalar una versión de RabbitMQ compatible con la versión de Adobe Commerce instalada |   | R |

{style="table-layout:auto"}

#### servicio PHP

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad de PHP | R |   |
| Configuración de la configuración predeterminada de PHP | R |     |
| Configuración de ajustes personalizados de PHP |     | R |
| Configuración del archivo YAML para alinear las versiones de PHP compatibles con la versión de Adobe Commerce instalada |    | R |

{style="table-layout:auto"}

#### Database services

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad de los servicios de Galera y MariaDB | R | |
| Mantenimiento continuo de la configuración predeterminada de la base de datos<br><br>(indexación y optimización de tablas principales, optimización de la configuración predeterminada de sys-admin) | R |   |
| Mantenimiento continuo de los datos del comerciante y la configuración modificada<br><br>(configuración de tablas normalizadas y planas, indexación y optimización de tablas personalizadas y de terceros, archivado o eliminación de datos, configuración de la administración del sistema) |     | R |
| Configuración de Galera y MySQL | R |   |
| Calidad y parches continuos de Galera y MariaDB | R |   |
| Optimización de la infraestructura en curso | R |   |
| Identificación y corrección de consultas lentas |     | R |
| Envíe una solicitud de servicio para instalar una versión de MariaDB compatible con la versión de Adobe Commerce instalada |     | R |
| Establecer y mantener políticas de retención de datos específicas del comerciante (las políticas de retención de datos del Adobe se definen en el acuerdo del comerciante) |     | R |

{style="table-layout:auto"}

#### Servicio CDN

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad y calidad de CDN | R |   |
| Configuración del servicio rápida (mediante extensión/API) |     | R |
| Calidad de extensión de Fastly | R |   |
| Fragmentos VCL de integración rápida (incluidos en la extensión Fastly) Calidad | R |   |
| Optimización de caché de página |     | R |
| Adición de dominios a servicios, a CDN y a infraestructura | R |   |
| Fragmentos de VCL personalizados |     | R |
| Reglas WAF y WAF | R |   |

{style="table-layout:auto"}

#### Servicio de caché

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad del servicio Redis | R |   |
| Configuración de las opciones predeterminadas de Redis | R |   |
| Calidad continua y parches de Redis | R |   |
| Envíe una solicitud de servicio para instalar una versión de Redis compatible con la versión de Adobe Commerce instalada |     | R |

{style="table-layout:auto"}

#### Servicio de búsqueda

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad del Elasticsearch | R |   |
| Configuración de los ajustes de Elasticsearch predeterminados | R |   |
| Envíe una solicitud de servicio para instalar una versión de Elasticsearch compatible con la versión de Adobe Commerce instalada |  | R |

{style="table-layout:auto"}

#### Servicio de correo electrónico

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad del servicio de correo electrónico SendGrid y su integración | R |   |
| Monitorización del uso de SendGrid del comerciante con respecto a los límites | R |   |
| El comerciante es responsable de utilizar el servicio solo para correos electrónicos transaccionales salientes<br>El servicio no admite el envío de correos electrónicos de marketing. |     | R |
| Configuración de servicios de correo electrónico opcionales de terceros |     | R |

{style="table-layout:auto"}

#### Servicios de terceros

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad y calidad de servicios de terceros |     | R |

{style="table-layout:auto"}

### Extensiones de Commerce Services

#### Servicio de informes avanzados

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad del servicio de informes avanzados | R |   |
| La configuración de los informes avanzados cumple con los términos y condiciones de los informes avanzados |     | R |

{style="table-layout:auto"}

#### Inteligencia comercial

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad de los servicios de Business Intelligence de Adobe Commerce | R |   |
| Procesos de sincronización de datos MBI | R |   |
| Detectando problemas de sincronización de MBI | R |   |
| Configuración de la sincronización de datos de MBI para Adobe Commerce Cloud Pro, Starter, On-Premies o non-Adobe Commerce<br>(API, calidad de datos y formato, red de comerciantes,<br>Conexiones de BD dentro y fuera de Adobe Commerce Cloud DB, por encima de los umbrales de datos) |     | R |
| Configuración de la sincronización de datos de MBI para Adobe Commerce Cloud Pro<br>(Configuración de la base de datos Adobe Commerce Cloud) | R |   |

{style="table-layout:auto"}

#### Product Recommendations

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad del servicio Product Recommendations | R |   |

{style="table-layout:auto"}

### Servicios de red

#### Optimización de imagen

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad y calidad de la optimización de imágenes | R |  |
| Configuración de la optimización de imágenes |     | R |

{style="table-layout:auto"}

#### Certificados SSL

|     | Adobe | Comerciante |
| --- | --- | --- |
| Certificado dedicado SSL: caducidad | R |  |
| Aprovisionamiento de certificados SSL | R |  |
| Compras y mantenimiento de certificados SSL específicos/EV (distintos de los valores por defecto proporcionados) y proporcionar al Adobe |     | R |

{style="table-layout:auto"}

#### Firewall de aplicaciones web (WAF)

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad y configuración de WAF | R |  |
| Direccionamiento de falsos positivos para reglas WAF | R | |
| Informe de falsos positivos de regla WAF |     | R |
| Ajuste de reglas WAF (NO ADMITIDO) |     |     |
| Registros de WAF/CDN |     | R |

{style="table-layout:auto"}

#### DDOS

|     | Adobe | Comerciante |
| --- | --- | --- |
| Bloqueo proactivo de IP |     | R |
| Protección de bots |     | R |
| Detección de DDOS: capa 3-4 | R |   |
| Detección de DDOS: capa 7 |     | R |
| Respuesta de DDOS | R |   |
| Configuración de la limitación de velocidad de extensión rápida y protección para bots (limitada) |     | R |

{style="table-layout:auto"}

#### Vínculo privado

|     | Adobe | Comerciante |
| --- | --- | --- |
| Configuración y mantenimiento de conexiones PrivateLink (si se utilizan) con un VPC propiedad del Adobe | R |   |
| Configuración y mantenimiento de conexiones PrivateLink (si se utilizan) con un VPC de propiedad del comerciante |     | R |
| Disponibilidad de SSH (vínculo no privado) | R |   |
| Configuración de PrivateLink entrante al extremo del servicio Adobe Commerce Cloud | R |   |
| Aceptación de PrivateLink entrante al extremo del servicio Adobe Commerce Cloud |     | R |
| Configuración de PrivateLink entrante al extremo del servicio VPC del comerciante |     | R |
| Aceptación de PrivateLink entrante al punto final del servicio VPC del comerciante | R |   |
| Configuración de integraciones de PrivateLink (extremo a cuenta) |     | R |
| Configuración del VPC de propiedad del comerciante para el extremo PrivateLink<br><br> (incluidas las conexiones VPN) |     | R |

{style="table-layout:auto"}

### Sistema e infraestructura

#### Servidor de aplicaciones

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad de Nginx | R |   |
| Configuración de Nginx | R |   |
| Calidad continua y parches de Nginx | R |   |

{style="table-layout:auto"}

#### Sistema operativo

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad del sistema operativo | R |   |
| Calidad continua y parches del sistema operativo | R |   |

{style="table-layout:auto"}

#### Copia de seguridad, alta disponibilidad y failover

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad de la instantánea y proceso de copia de seguridad | R |   |
| Programación de copias de seguridad para entornos de ensayo y producción de Cloud Pro | R |   |
| Programación de copias de seguridad para entornos de integración de Cloud Starter y Pro |     | R |
| Disponibilidad de alta disponibilidad/failover | R |   |

{style="table-layout:auto"}

#### Servidores y escalado en la nube

|     | Adobe | Comerciante |
| --- | --- | --- |
| Disponibilidad de recursos de CPU, centro de datos, espacio en disco | R |   |
| Disponibilidad y ejecución de capacidad de sobretensión o de ampliación de emergencia | R |   |
| Solicitando capacidad de sobretensión |     | R |
| Monitorización del uso de vCPU con respecto a los límites | R |   |

{style="table-layout:auto"}
