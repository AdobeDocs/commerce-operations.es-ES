---
title: Resumen del flujo de trabajo [!DNL Adobe Commerce Patching Automation]
description: Obtenga información acerca del proceso de  [!DNL Adobe Commerce Patching Automation] flujo de trabajo, incluida la terminología, las fases de flujo de trabajo y las operaciones para la administración automatizada de parches.
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 0%

---

# Resumen de flujo de trabajo [!DNL Adobe Commerce Patching Automation]

Este tema proporciona información general de alto nivel sobre cómo funcionan las operaciones de revisión con [!DNL Adobe Commerce Patching Automation].

## Terminología

* **Operaciones**: las acciones principales realizadas por el servicio:
  * Aplicar
  * Revertir
* **Fases**: las tres fases del flujo de trabajo:
  * Comprobación preliminar
  * Parches
  * Validación
* **Entorno**: el entorno de Adobe Commerce Cloud en el que se aplican los parches.

## Operaciones

[!DNL Patching Automation] admite dos *operaciones* principales para administrar parches en el entorno de Adobe Commerce Cloud:

* **Aplicar operación**: agrega cambios de revisión a la base de código mediante un proceso seguro y validado. Los parches se aplican colocando los archivos de parches en la carpeta `m2-hotfixes`.

* **Operación de reversión**: elimina las revisiones aplicadas anteriormente de la base de código al eliminar los archivos de revisión de la carpeta `m2-hotfixes`.

>[!IMPORTANT]
>
>Las operaciones de reversión sólo están disponibles para parches que se aplicaron originalmente a través de [!DNL Patching Automation]. Los parches aplicados manualmente o mediante otros métodos no se pueden revertir con este servicio.

## Fases

El flujo de trabajo [!DNL Patching Automation] utiliza tres *fases* que siempre se ejecutan en este orden para garantizar que los parches se apliquen de forma segura y fiable:

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

La fase de aplicación de parches aplica o revierte el parche en un entorno de integración temporal. Durante esta fase, el servicio crea un entorno de integración temporal para aplicar de forma segura el parche, confirmar que se implementa correctamente y verificar que pasa una comprobación de estado antes de realizar cualquier cambio en el entorno real.

Este enfoque proporciona lo siguiente:

* **Seguridad**: mantiene su entorno de destino intacto hasta que el entorno de integración se implemente correctamente y pase su comprobación de estado
* **Capacidad de reversión** - si se detectan problemas
* **Aislamiento** - para cada operación de parche

#### Fase 2a: Creación del entorno de integración

**Creación de rama** - [!DNL Patching Automation] crea una rama de entorno de integración temporal llamada `{target-environment}-CAPS-{patch-id}`

**Configuración del entorno**: el entorno de integración se crea como elemento secundario del entorno de destino

**Sincronización de código**: el entorno de integración hereda el estado de código exacto del entorno de destino (el mismo código base)

**Sin clonación de datos**: el entorno de integración no recibe una copia de los datos del entorno de destino (base de datos, medios u otro contenido almacenado); solo se usa el código base para aplicar y comprobar el parche

**Requisitos de recursos**: la capacidad de almacenamiento total del proyecto de Cloud está definida en el contrato. (Consulte a través de la página de su cuenta o `magento-cloud subscription:info`). La asignación de disco de cada entorno se configura por separado mediante la propiedad `disk` en `.magento.app.yaml`/`.magento/services.yaml`. Consulte [Administrar espacio en disco](https://experienceleague.adobe.com/es/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space) para obtener más información. Si falla una operación de revisión debido a limitaciones de almacenamiento, compare el uso de disco del entorno de integración (`magento-cloud db:size` / `magento-cloud mount:size`) con la asignación configurada.

#### Fase 2b: aplicación de parches en el entorno de integración

**Pruebas seguras**: el parche se aplica al entorno de integración, no directamente al entorno de destino

**Administración de archivos** - Los archivos de revisión se colocan en la carpeta `m2-hotfixes`

**Operaciones de Git**: los cambios se confirman y se insertan en la rama del entorno de integración

**Activación del entorno**: el entorno de integración está activado para implementar el código al que se aplicó el parche

**Comprobación de estado**: una vez activado, [!DNL Patching Automation] confirma lo siguiente antes de continuar con la combinación: el entorno de integración se implementó correctamente y está en buen estado, la aplicación se inicia y se puede acceder a sus conexiones de caché y base de datos.

>[!NOTE]
>
>Si el proyecto usa un repositorio externo de GitHub, el servicio administra la autenticación automáticamente mediante la [[!DNL Patching Automation] aplicación de GitHub](github-integration.md). No se requieren credenciales adicionales más allá de la instalación de la aplicación.

#### Fase 2c: volver a combinar con el entorno de destino

**Comprobación de sincronización**: antes de la combinación, el servicio confirma que el entorno de integración sigue activo, sincronizado con el entorno de destino y en buen estado. Si el destino ha cambiado durante el parche, la operación se detiene aquí en lugar de combinarse

**Cierre de seguridad del entorno**: el servicio cierra el entorno de destino localmente

**Operación de combinación**: la rama del entorno de integración se combina con el entorno de destino

**Control de conflictos**: si se produce un conflicto de combinación, la operación falla y se notifica como un error, no se resuelve automáticamente

**Implementación**: los cambios combinados se implementan en el entorno de destino

**Verificación**: el servicio comprueba que la combinación se realizó correctamente y que los entornos están sincronizados

### Ciclo del entorno de integración

Los entornos de integración tienen un ciclo de vida específico durante la fase de aplicación de parches:

* **Creación** - Creada al inicio de la fase de aplicación de parches
* **Período activo** - Permanecer activo durante la aplicación y prueba del parche
* **Limpieza**: se elimina inmediatamente si la operación falla durante la fase de aplicación de parches, antes de la combinación. Eliminado de otro modo durante la fase de validación, después de la combinación, independientemente de si se aprueba o no la validación

### Fase 3: Validación

La fase de validación confirma que la aplicación a la que se han aplicado parches se inicia correctamente y pasa una comprobación de estado.

**Qué sucede:**

* **Comprobación del estado de la aplicación**: comprueba que la aplicación se inicia y ejecuta correctamente y que se puede acceder a las conexiones de caché y base de datos
* **Limpieza**: elimina el entorno de integración temporal y actualiza el estado del trabajo para reflejar la finalización. La actividad del entorno permanece visible en la fuente de actividades del proyecto.

>[!IMPORTANT]
>
>A diferencia de las fases 1 y 2, esta comprobación de estado se ejecuta *después* de que el parche ya se haya combinado en el entorno de destino. Si se produce un error, la combinación no se revierte automáticamente. El entorno de destino se puede dejar en un estado roto y se requiere una intervención manual (como revertir el parche) para restaurarlo. Consulte [Solución de problemas](troubleshooting.md) para saber qué hacer si esto sucede.

## Indicadores de éxito

**Aplicar operación:**

* &quot;Trabajo completado correctamente&quot;: parche aplicado sin problemas
* &quot;Se ha aplicado el parche&quot;: el parche ya estaba presente (no se necesita ninguna acción)
* El archivo de revisión se colocó correctamente en la carpeta `m2-hotfixes`
* Todas las comprobaciones de validación se superan
* Comprobaciones de estado de aplicación correctas

**Operación de reversión:**

* &quot;Trabajo completado correctamente&quot;: parche revertido sin problemas
* &quot;Se ha revertido el parche&quot;: el parche ya se ha revertido (no se necesita ninguna acción)
* El archivo de revisión se quitó correctamente de la carpeta `m2-hotfixes`
* Todas las comprobaciones de validación se superan
* Comprobaciones de estado de aplicación correctas

## Salvaguardias del entorno de producción

La aplicación o reversión de parches en un entorno de producción conlleva más riesgo que en otros entornos, por lo que [!DNL Patching Automation] incluye dos protecciones específicas de la producción.

### Confirmación antes de iniciar

Antes de iniciar una operación de aplicación o reversión en un entorno de producción, se le pedirá que confirme la operación en un cuadro de diálogo. Este paso de confirmación protege contra el inicio accidental de un trabajo en producción.

### Condiciones previas recomendadas

Adobe recomienda habilitar el modo de mantenimiento y deshabilitar los trabajos cron antes de aplicar parches a un entorno de producción. De manera predeterminada, [!DNL Patching Automation] comprueba que se cumplen ambas condiciones y bloquea la operación con una notificación si no se cumple alguna de las condiciones. Si comprende los riesgos de continuar sin modo de mantenimiento o con los trabajos cron habilitados, seleccione la casilla de verificación de anulación en la interfaz de usuario para omitir esta comprobación.

* **Modo de mantenimiento** - Se recomienda habilitar
* **Trabajos cron** - Se recomienda deshabilitarlos

## Temas relacionados

* [Introducción a la automatización de parches](intro.md)
* [Cómo acceder a](access.md)
* [Integración de GitHub](github-integration.md)
* [Prácticas recomendadas](best-practices.md)
* [Resolución de problemas](troubleshooting.md)
