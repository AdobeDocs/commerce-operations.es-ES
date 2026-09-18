---
title: Política de parches de seguridad aislada mensual
description: Obtenga información sobre los parches de seguridad aislados mensuales de Adobe Commerce, entregados el martes de parches para proporcionar correcciones CVE específicas entre versiones de parches de seguridad.
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
    internal-label: Commerce on Cloud
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: f2261633-201d-46c5-8a66-999e70527a83
    internal-label: PCI
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 66d7c9fd19785e791635d8e8bdf3d6ff3aa27a20
workflow-type: tm+mt
source-wordcount: '1553'
ht-degree: 0%
---
# Política de parches de seguridad aislada mensual

Para ayudar a los clientes de Adobe Commerce a aplicar correcciones de seguridad críticas antes, Adobe Commerce ahora ofrece parches de seguridad aislados mensuales el martes de parches (el segundo martes del mes). Consulte la [programación de versiones de Adobe Commerce](schedule.md) para ver las fechas. Estos parches están disponibles para Adobe Commerce en la nube, Adobe Commerce en línea e instalaciones de Magento Open Source.

Un archivo de revisión de seguridad aislado contiene únicamente el código necesario para resolver una o más vulnerabilidades de seguridad específicas, que se entrega como un archivo de comparación de códigos de ámbito limitado en lugar de como un paquete Compositor completo. Debido a que los cambios son específicos de las vulnerabilidades de seguridad, se pueden revisar, probar y aplicar más rápido que una versión de parche de seguridad, sin activar la resolución de dependencias más amplia y las pruebas de regresión que requiere una actualización de versión de parche de seguridad. Cada archivo de revisión de seguridad aislada mensual se incorpora a la siguiente versión completa de revisión de seguridad, de modo que los clientes puedan obtener todos los archivos de revisión aislada publicados a través de la siguiente versión de revisión de seguridad (`-pN`).

## Cómo encajan los parches aislados con otros tipos de parches

Los parches de seguridad aislados son uno de los varios tipos de parches que proporciona Adobe Commerce para mantener a los clientes seguros y actualizados.

| **Tipo de parche** | **Propósito** | **Comportamiento acumulativo** | **Envío típico** | **Rol** |
| --- | --- | --- | --- | --- |
| Versión del parche de seguridad (-pN) | Actualización de seguridad y cumplimiento para una línea de versión compatible | Acumulativo: establece la línea base de seguridad actual | Paquete Composer | Línea base de seguridad admitida principal |
| Archivo de parche de seguridad aislado | Corrección dirigida para una o más CVE | No acumulado: aplicar en secuencia | Archivo de parche independiente, normalmente un ZIP. También se pueden incluir algunas correcciones en los parches de Cloud para Commerce | Corrección provisional más rápida entre las versiones de parches de seguridad |
| Parches de nube para Commerce | Correcciones necesarias, críticas (incluidas las correcciones de seguridad) y cambios específicos de la nube | Versión del paquete dependiente | Parches de nube para el paquete de Commerce administrados mediante ECE-Tools | Se aplica automáticamente durante la implementación de Cloud |
| Parche de la herramienta Parches de calidad (QPT) | Corrección de compatibilidad o calidad opcional y específica para un problema específico | Parche dependiente de la cadena | paquete QPT | Ofrece correcciones de calidad específicas |
| Revisión | Corrección urgente y de ámbito estrecho (por ejemplo, un día cero) | Caso específico | ZIP/diff o paquete independiente mediante QPT | Problemas urgentes y de alto impacto |

Los dos tipos de parches de seguridad desempeñan funciones diferentes:

* **Los parches aislados** solo contienen correcciones de vulnerabilidades y no son acumulativos. No agrupan archivos de parches aislados publicados anteriormente. Los comerciantes deben aplicar los parches en orden, ya que cada nuevo parche supone que ya existen otros más antiguos. Para aplicar una revisión de seguridad aislada, la instalación debe estar en la última versión de revisión de solo seguridad para su línea admitida, ya que las correcciones aisladas se prueban exclusivamente con esa versión.

* **Los parches de seguridad (`-pN`)** se lanzan anualmente para todas las líneas de versión admitidas y se implementan mediante Composer. Incluyen todas las revisiones de seguridad, cumplimiento y calidad publicadas anteriormente. Adobe puede lanzar parches de seguridad adicionales si es necesario.

## Ventajas del parche aislado mensual

El descubrimiento de vulnerabilidades se ha acelerado en toda la industria. Las herramientas de análisis asistidas por IA ahora pueden analizar grandes códigos base y defectos superficiales mucho más rápido que la revisión manual, reduciendo la ventana entre la divulgación y la explotación. Una cadencia de parche aislada mensual cierra esta brecha al proporcionar correcciones tan pronto como estén listas, en lugar de esperar a la próxima versión programada del parche de seguridad.

El objetivo es la velocidad sin sobrecargas innecesarias. Una corrección rápida no se pone en cola hasta la próxima versión del parche de seguridad, y los comerciantes no aplican parches más a menudo de lo necesario. Los archivos de parches de seguridad aislados resuelven esa tensión: cada uno es una diferencia estrecha de solo seguridad, mucho más fácil de revisar y aplicar que una versión de parches de seguridad, ya que su ámbito está deliberadamente limitado.

Este método funciona porque los parches de un solo uso omiten la resolución de dependencias y las pruebas de regresión completas necesarias para las versiones de Composer, lo que permite crearlos, validarlos con una línea de base conocida y enviarlos rápidamente. En la infraestructura en la nube, estas correcciones se incluyen en Parches en la nube para Commerce, un paquete que los comerciantes actualizan como parte de su Compositor y flujo de trabajo de implementación. Una vez actualizada, la corrección se aplica automáticamente durante la implementación sin que haya ningún archivo de parche independiente para localizar o aplicar. El flujo de trabajo manual del archivo de parches descrito en los boletines de seguridad es para instalaciones locales y de Magento Open Source que no ejecutan la canalización en la nube.

## Aplicar parches aislados mensuales

Para aplicar el archivo de parches de seguridad aislado mensual y mantenerse al día con las últimas correcciones, siga el proceso a continuación:

1. **Compruebe la [programación de versiones](schedule.md).**

   Los nuevos archivos de parches aislados mensuales se envían según la programación de versiones. Revise el boletín de seguridad correspondiente para ver los componentes y CVE afectados. Cada boletín se vincula a las notas de la versión con instrucciones paso a paso para instalar el archivo de parches aislado de ese mes.

1. **Compruebe el estado de seguridad de la instalación de Commerce mediante la [herramienta Commerce Version](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/commerce-version-tool/intro).**

   La herramienta informa de qué parches mensuales están instalados actualmente, cuáles faltan y a qué CVE permanece expuesta la instalación. Esto proporciona una evaluación definitiva de qué acción es necesaria, en lugar de depender solo del número de versión.

1. **Confirmar la versión de línea de base.**

   Los parches aislados solo se comprueban con la última versión de solo seguridad `-p` para su línea. Si está atrasado en esa línea de base, aplíquelo primero.

1. **Aplicar todas las revisiones que faltan en orden.**

   Como no son acumulativos, no puede saltar al archivo más reciente.

   >[!NOTE]
   >
   >**Clientes de la nube:** Primero compruebe los parches de nube instalados para Commerce [versión](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest). Es posible que la corrección ya se haya incluido y aplicarla manualmente puede crear un conflicto o duplicar la corrección.

1. **Hacer coincidir archivos con los componentes instalados.**

   Aplique únicamente el archivo que corresponda a su CE, EE, B2B u otra versión del componente.

1. **Vuelva a ejecutar la herramienta Versión de Commerce para confirmar.**

   Compruebe que el nuevo parche se muestra como instalado y que los CVE relevantes ahora informan como protegidos.

1. **Probar e implementar.**

   Realice la validación en el entorno de ensayo antes de pasar a producción, según el proceso de cambio normal.

Los clientes de la nube también pueden usar [Adobe Commerce Patching Automation](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/caps-tool/intro) para aplicar o revertir parches a través del Panel de administración en lugar de los pasos manuales de Git y Compositor anteriores.

## Acciones de parche por tipo de implementación

| **Usted ejecuta...** | **Cambios** |
| --- | --- |
| Adobe Commerce en la nube | Parches de nube para Commerce, entregados a través de ECE-Tools, aplican las correcciones necesarias automáticamente durante su próxima implementación. Sigue controlando los pasos de bifurcación, combinación y validación, y debe comprobar las notas de la versión de Cloud Patches para Commerce antes de aplicar manualmente la misma corrección. |
| Adobe Commerce local | Confirme la versión de línea de base `-p`, descargue el archivo que coincida con cada componente instalado, aplique la secuencia y verifique con la herramienta Versión de Commerce. |

## FAQ

Los parches de seguridad aislados mensualmente son una nueva directiva de versión. Las siguientes preguntas abordan problemas comunes.

### ¿Necesito que se apliquen todos los parches aislados anteriores o solo la última versión de parches de seguridad?

Necesitas ambas cosas. Antes de aplicar un parche aislado, actualice a la línea de base de la versión `-p` de solo seguridad más reciente. Cada parche se prueba únicamente respecto a esa línea de base. Los parches aislados no son acumulativos, así que aplique los parches perdidos en secuencia.

Por ejemplo, si se encuentra en la línea de base de la versión actual `-p`, pero se perdió los parches aislados de julio y agosto, aplique julio, agosto y septiembre. La siguiente versión completa de `-p` restablece la secuencia porque incluye todas las correcciones aisladas emitidas anteriormente.

### ¿Por qué no enviar un solo paquete Composer en lugar de archivos de parche independientes?

En una instalación con varios componentes (CE, EE, B2B y Page Builder), una versión mensual puede requerir archivos de parche independientes, ya que cada archivo se dirige a una versión de componente instalada específica. Combinar todas las correcciones en un paquete de Composer reintroduciría los problemas de resolución de dependencias y requeriría pruebas de regresión de superficie completa, los riesgos que los parches aislados están diseñados para evitar. Los clientes de la nube no necesitan aplicar parches manualmente. Parches de nube para Commerce ofrece las mismas correcciones a través de la canalización de implementación existente.

### Con parches en capas en los parches, ¿cómo sé en qué estado de seguridad se encuentra mi instalación?

Con el lanzamiento de los parches de seguridad mensuales, Adobe Commerce presentó [Commerce Version Tool](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/commerce-version-tool/intro), una utilidad independiente que informa sobre qué parches están instalados o faltan y contra qué CVE está protegida su instalación. En lugar de depender de los números de versión, la herramienta lee los metadatos de los parches y proporciona resultados legibles por el equipo para la creación de informes y la integración continua (CI).

### ¿Significa esto que Adobe se ha alejado de las versiones acumulativas de las versiones de seguridad?

No. La versión anual de `-p` sigue siendo el punto de comprobación de seguridad principal y acumulativo. Los parches aislados complementan esa cadencia en el caso de las ECV que no pueden esperarlo de forma segura. No reemplazan las versiones de `-p`. Si aplica el lanzamiento del parche de seguridad programado para su línea cada año, permanecerá en una ruta totalmente compatible y recibirá todas las correcciones que se hayan emitido como un archivo aislado intermedio.

### ¿El envío de correcciones fuera de Composer no hace que una instalación predeterminada sea menos segura?

No. El mecanismo de envío no afecta al resultado de seguridad de la corrección. Una revisión aislada aplica el mismo cambio de código que se incluye posteriormente en una versión de revisión completa (`-p`). El hecho de que la corrección se entregue como un paquete Composer o como un archivo independiente no afecta a su eficacia. Los comerciantes que no apliquen el parche permanecerán en su línea de base de seguridad existente hasta la próxima versión de seguridad programada. La aplicación de parches aislados puede reducir la exposición al proporcionar correcciones antes, en lugar de esperar a un ciclo de lanzamiento completo.

## Más ayuda sobre este tema

>[!MORELIKETHIS]
>
>* [Directiva de ciclo de vida de software](lifecycle-policy.md)
>* [Directiva de versión](versioning-policy.md)
>* [Programación de publicación de parches](schedule.md)
>* [Herramienta Versión de Commerce](../tools/commerce-version-tool/intro.md)
>* [Avisos y boletines de seguridad de Adobe](https://helpx.adobe.com/security/security-bulletin.html)
