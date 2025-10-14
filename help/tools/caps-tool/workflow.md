---
title: Cómo funciona  [!DNL Cloud Automation Patching Service (CAPS)] flujo de trabajo
description: Obtenga información acerca del proceso de  [!DNL Cloud Automation Patching Service (CAPS)] flujo de trabajo, incluida la terminología, las fases de flujo de trabajo y las operaciones para la administración automatizada de parches.
hide: true
hidefromtoc: true
source-git-commit: eff8c0ae9e1d9db6b46ba7cfbb915685ab5b194d
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 0%

---

# Funcionamiento del flujo de trabajo [!DNL Cloud Automation Patching Service (CAPS)]

Este tema proporciona información general de alto nivel sobre cómo funcionan las operaciones de revisión con [!DNL CAPS (Cloud Automation Patching Service)].

## Terminología

* **Operaciones** - las acciones principales realizadas por [!DNL CAPS]:
   * Aplicar
   * Revertir
* **Fases**: las tres fases del flujo de trabajo:
   * Comprobación preliminar
   * Parches
   * Validación
* **Entorno**: el entorno de Adobe Commerce Cloud en el que se aplican los parches.

## Operaciones

[!DNL CAPS] admite dos *operaciones* principales para administrar parches en el entorno de Adobe Commerce Cloud:

* **Aplicar operación**: agrega cambios de revisión a la base de código mediante un proceso seguro y validado. Los parches se aplican colocando los archivos de parches en la carpeta &quot;m2-hotfixes&quot;.

* **Operación de reversión**: elimina los parches aplicados anteriormente de la base de código al eliminar los archivos de parche de la carpeta &#39;m2-hotfixes&#39;.

>[!IMPORTANT]
>
>Las operaciones de reversión sólo están disponibles para parches que se aplicaron originalmente a través de [!DNL CAPS]. Los parches aplicados manualmente o mediante otros métodos no se pueden revertir con este servicio.

## Fases

El flujo de trabajo [!DNL CAPS] utiliza tres *fases* que siempre se ejecutan en este orden para garantizar que los parches se apliquen de forma segura y fiable:

* **Comprobación preliminar**: valida la compatibilidad de parches y la preparación del entorno.
* **Parche**: aplica o revierte el parche en un entorno de integración.
* **Validación**: valida la aplicación de revisión y realiza comprobaciones de estado.

## Detalles de fase

### Fase 1: Comprobación preliminar

La fase de comprobación preliminar valida que el parche se pueda aplicar de forma segura a su entorno.

**Qué sucede:**

* **Salvaguardias del entorno de producción** (solo entornos de producción):
   * Comprueba si el almacén está en modo de mantenimiento
   * Comprueba que los trabajos cron estén deshabilitados
   * Bloques de aplicación de parches si no se cumplen las condiciones
   * Muestra el cuadro de diálogo de confirmación si se cumplen las condiciones
* **Validación de revisión** - comprueba que el archivo de revisión es válido y compatible
* **Evaluación del entorno**: comprueba la preparación y los recursos del entorno
* **Detección de conflictos** - identifica posibles conflictos con el código existente
* **Comprobación de dependencias**: valida la compatibilidad de la versión de Adobe Commerce

### Fase 2: aplicación de parches

La fase de aplicación de parches aplica o revierte el parche en un entorno de integración temporal para realizar pruebas. Durante esta fase, [!DNL CAPS] crea un entorno de prueba temporal para aplicar y probar el parche de forma segura antes de realizar cambios en el entorno real.

Este enfoque proporciona lo siguiente:

* **Seguridad**: mantiene el entorno de destino intacto hasta que se valida el parche
* **Pruebas**: en un entorno real antes de afectar a la producción
* **Capacidad de reversión** - si se detectan problemas
* **Aislamiento** - para cada operación de parche

#### Fase 2a: Creación del entorno de integración

**Creación de rama** - [!DNL CAPS] crea una rama de entorno de integración temporal llamada `{target-environment}-CAPS-{patch-id}`

**Configuración del entorno**: el entorno de integración se crea como elemento secundario del entorno de destino

**Sincronización de código**: el entorno de integración hereda el estado exacto del entorno de destino

**Requisitos de recursos** - [!DNL CAPS] crea un entorno temporal con la base de código del entorno de destino. Según la documentación de Adobe Commerce Cloud, cada entorno (incluidos los entornos de integración) tiene una asignación de almacenamiento independiente en función de su plan de almacenamiento contratado. La cantidad de almacenamiento que contrató representa el almacenamiento total para cada entorno. En la mayoría de los casos, no tendrá problemas con las limitaciones de recursos. Si encuentra algún error con limitaciones de recursos, compruebe el tamaño de su aplicación y el almacenamiento contratado en su plan.

#### Fase 2b: aplicación de parches en el entorno de integración

**Pruebas seguras**: el parche se aplica al entorno de integración, no directamente al entorno de destino

**Administración de archivos** - Los archivos de revisión se colocan en el directorio `m2-hotfixes/`

**Operaciones de Git**: los cambios se confirman y se insertan en la rama del entorno de integración

**Activación del entorno**: el entorno de integración está activado para implementar el código al que se aplicó el parche

#### Fase 2c: volver a combinar con el entorno de destino

**Cierre de compra del entorno** - [!DNL CAPS] cierra su entorno de destino localmente

**Operación de combinación**: la rama del entorno de integración se combina con el entorno de destino

**Resolución de conflictos**: si se produce algún conflicto, se resuelve automáticamente siempre que sea posible

**Implementación**: los cambios combinados se implementan en el entorno de destino

**Verificación** - [!DNL CAPS] verifica que la combinación se realizó correctamente y que los entornos están sincronizados

**Limpieza del entorno**: el entorno de integración temporal se ha eliminado para liberar recursos

## Ciclo del entorno de integración

Los entornos de integración tienen un ciclo de vida específico durante la fase de aplicación de parches:

* **Creación** - Creada al inicio de la fase de aplicación de parches
* **Período activo** - Permanecer activo durante la aplicación y prueba del parche
* **Limpieza**: eliminada automáticamente después de la combinación correcta o si la operación falla

### Fase 3: Validación

La fase de validación garantiza que la aplicación a la que se han aplicado parches funcione correctamente y realice comprobaciones de estado.

**Qué sucede:**

* **Comprobación del estado de la aplicación**: verifica que la aplicación se inicie y se ejecute correctamente
* **Limpieza**: elimina el entorno temporal, actualiza los registros y notifica la finalización.

## Indicadores de éxito

**Aplicar operación:**

* &quot;Trabajo completado correctamente&quot;: parche aplicado sin problemas
* &quot;Se ha aplicado el parche&quot;: el parche ya estaba presente (no se necesita ninguna acción)
* El archivo de parche se ha colocado correctamente en la carpeta &quot;m2-hotfixes&quot;
* Todas las comprobaciones de validación se superan
* Comprobaciones de estado de aplicación correctas

**Operación de reversión:**

* &quot;Trabajo completado correctamente&quot;: parche revertido sin problemas
* &quot;Se ha revertido el parche&quot;: el parche ya se ha revertido (no se necesita ninguna acción)
* El archivo de parche se ha eliminado correctamente de la carpeta &quot;m2-hotfixes&quot;
* Todas las comprobaciones de validación se superan
* Comprobaciones de estado de aplicación correctas

## Salvaguardias del entorno de producción

[!DNL CAPS] incluye protecciones específicas para entornos de producción a fin de evitar interrupciones accidentales y garantizar que los parches se validen de antemano de forma segura.

### Condiciones previas para la aplicación de parches de producción

Antes de aplicar parches a entornos de producción, [!DNL CAPS] comprueba dos condiciones críticas:

* **Modo de mantenimiento** - El almacén debe estar en modo de mantenimiento
* **Trabajos Cron deshabilitados** - Los trabajos Cron deben deshabilitarse

Si no se cumple alguna de las condiciones, la aplicación de parche se bloquea y se notifica al usuario.

## Temas relacionados

* [Introducción a CAPS](intro.md)
* [Cómo acceder a](access.md)
* [Prácticas recomendadas](best-practices.md)
* [Resolución de problemas](troubleshooting.md)
