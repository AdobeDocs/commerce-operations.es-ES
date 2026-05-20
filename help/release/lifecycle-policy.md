---
title: directiva de ciclo vital de Adobe Commerce
description: Obtenga información acerca de los periodos de compatibilidad de Adobe Commerce, las fechas de fin de compatibilidad y de aplicación en la nube, las disposiciones transitorias y las rutas a una versión admitida.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 620523021580a9dba44e0e2041d8100761b8bce1
workflow-type: tm+mt
source-wordcount: '1526'
ht-degree: 0%

---


# directiva de ciclo vital de Adobe Commerce

Adobe Commerce sigue una política de ciclo de vida del software definida para garantizar que los clientes se ejecuten en versiones seguras y compatibles. Si se encuentra en una línea de versión anterior, es fundamental comprender en qué parte de este ciclo vital se encuentra y actuar antes de los plazos de aplicación. Este tema cubre las definiciones del nivel de soporte, las fechas de finalización de la asistencia y de aplicación, las disposiciones transitorias para versiones que se acercan al final de su vida útil y las rutas para permanecer en una versión admitida.

>[!IMPORTANT]
>
>Adobe presenta una directiva de actualización de versiones aplicada para Adobe Commerce en la nube (PaaS). A partir del **1 de junio de 2027**, Adobe dejará de mantener los entornos de nube que ejecutan versiones de Commerce no compatibles y se reserva el derecho de desactivarlos. Si ejecuta en la nube (PaaS), debe pasar a una versión de Adobe Commerce compatible o migrar a [!DNL Adobe Commerce as a Cloud Service] antes de la fecha publicada [fin de la compatibilidad extendida](lifecycle-policy.md#end-of-support-dates) para la línea de lanzamiento. Consulte [Directiva de aplicación de actualización de versiones en la nube](version-upgrade-enforcement-policy.md) para ver las fechas de aplicación y las versiones afectadas, así como lo que sucede si permanece en una versión no compatible.

## Explicación de los niveles de soporte

Adobe Commerce define tres niveles de compatibilidad para las líneas de versión. Las secciones siguientes describen cada nivel.

### Soporte regular

El periodo de soporte estándar de tres años a partir de la fecha de disponibilidad general (GA). El soporte regular incluye correcciones de calidad, parches de seguridad y soporte completo de Adobe Commerce on-call.

- **Correcciones de calidad**: los clientes pueden obtener acceso a las correcciones de calidad poniéndose en contacto con el [Soporte técnico de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) o a través del servicio de autoservicio [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).

- **Correcciones de seguridad**: Adobe proporciona correcciones de seguridad mediante parches de seguridad acumulativos y [archivos de parches de seguridad aislados](versioning-policy.md#isolated-security-patch-file) no acumulativos durante el período de compatibilidad de tres años.

- **Revisiones**: para problemas de seguridad críticos, como vulnerabilidades de día cero, Adobe proporciona [revisiones](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) para todos los clientes en una versión compatible, incluso si no se encuentran en la última versión de revisión o parche de seguridad. Tenga en cuenta que una revisión no es exhaustiva y no aborda todos los problemas de seguridad que se resolverían al actualizar a la última versión.

### Compatibilidad ampliada

Una extensión de soporte de un año disponible para líneas de versión específicas que van más allá del soporte regular. Incluye parches de calidad y seguridad. Disponible solo para clientes de Adobe Commerce; no está disponible para Magento Open Source.

### Período transitorio solo de seguridad

Un período transitorio único y limitado en el tiempo disponible para versiones específicas cuya compatibilidad ampliada finalizó en 2025 o 2026. El período transitorio solo de seguridad proporciona correcciones de seguridad aisladas limitadas. No se incluye la compatibilidad de Adobe Commerce on-call. Este período no equivale a una ayuda regular o ampliada y no se prorrogará más. Trátelo como un período de migración, no como un nivel de asistencia a largo plazo. Consulte [Disposiciones transitorias de solo seguridad](#security-only-transitional-provisions).

## Fechas de fin de soporte

La siguiente tabla muestra el ciclo de vida completo para cada versión de Adobe Commerce, incluidas las fechas de aplicación de actualización de la nueva versión para los entornos de Adobe Commerce en la nube (PaaS).

| Versión | Disponibilidad general | Fin del soporte regular | Fin de la compatibilidad ampliada | Fin del período de solo seguridad | [Fecha de aplicación de actualización de la versión (solo en la nube)](version-upgrade-enforcement-policy.md) |
|---------|----------------------|------------------------|-------------------------|-----------------------------|-----------------------------------------------|
| Adobe Commerce 2.4.9 | 12 de mayo de 2026 | 31 de mayo de 2029 | TBD | N/D | TBD |
| Adobe Commerce 2.4.8 | 8 de abril de 2025 | 31 de mayo de 2028 | TBD | N/D | TBD |
| Adobe Commerce 2.4.7 | 9 de abril de 2024 | 31 de mayo de 2027 | 31 de mayo de 2028 | N/D | 1 de junio de 2028 |
| Adobe Commerce 2.4.6 | 14 de marzo de 2023 | 11 de agosto de 2026 | 30 de agosto de 2027 | 31 de mayo de 2028 | 1 de junio de 2028 |
| Adobe Commerce 2.4.5 | 9 de agosto de 2022 | 12 de agosto de 2025 | 12 de agosto de 2026 | 31 de mayo de 2027 | 1 de junio de 2027 |
| Adobe Commerce 2.4.4 | 12 de abril de 2022 | 12 de abril de 2025 | 14 de abril de 2026 | 31 de mayo de 2027 | 1 de junio de 2027 |

{style="table-layout:auto"}

Si la línea de lanzamiento se acerca a estas fechas o las supera, consulte [Opciones de actualización y migración](#upgrade-and-migration-options). Para obtener detalles de aplicación en la nube, consulte [Directiva de aplicación de actualización de versiones en la nube](version-upgrade-enforcement-policy.md).

### Calendario de asistencia por trimestre

Utilice este gráfico para ver las ventanas de soporte superpuestas en todas las líneas de versión. Para ver las fechas de finalización exactas, consulte las tablas anteriores. La compatibilidad ampliada para 2.4.8 y 2.4.9 es por determinar y no se muestra.

<table style="table-layout:auto">
<thead>
  <tr>
    <th colspan="1"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
    <th colspan="4">2025</th>
    <th colspan="4">2026</th>
    <th colspan="4">2027</th>
    <th colspan="4">2028</th>
    <th colspan="4">2029</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Commerce</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
    <td>T1</td>
    <td>T2</td>
    <td>T3</td>
    <td>T4</td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="3" style="background-color:#FFBF00;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="3" style="background-color:#FFBF00;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.9</td>
    <td colspan="17"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="2"></td>
  </tr>
</tbody>
</table>

**Clave**

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td style="background-color:#67ac68;"></td>
   <td>Soporte regular</td>
  </tr>
  <tr>
   <td style="background-color:#ffd700;"></td>
   <td>Compatibilidad ampliada</td>
  </tr>
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>Período transitorio solo de seguridad</td>
  </tr>
 </tbody>
</table>

## Disposiciones transitorias de sólo seguridad {#security-only-transitional-provisions}

Como medida única para las versiones 2.4.4, 2.4.5 y 2.4.6 con compatibilidad ampliada que ya finalizó en 2025 y 2026, Adobe proporciona las siguientes disposiciones transitorias para darle tiempo adicional para planificar y ejecutar la migración o actualización. Estas disposiciones no reemplazan la [aplicación de actualización de la versión en la nube](version-upgrade-enforcement-policy.md) para entornos PaaS. Aún debe actualizar o migrar antes de la fecha de aplicación publicada.

| Versión | Disposición transitoria | Periodo | Qué se incluye | Qué no se incluye |
|---------|------------------------|--------|------------------|----------------------|
| 2.4.4 y 2.4.5 | Período transitorio solo de seguridad | Hasta el 31 de mayo de 2027 | Correcciones de seguridad aisladas limitadas caso por caso | Compatibilidad con Adobe Commerce on-call, correcciones de calidad, actualizaciones de dependencia de la plataforma |
| 2.4.6 | Asistencia ampliada + período transitorio solo de seguridad | Compatibilidad ampliada hasta el 30 de agosto de 2027. Período solo de seguridad hasta el 31 de mayo de 2028. | Ampliación del periodo de soporte: parches de calidad y seguridad. Período de solo seguridad: correcciones de seguridad aisladas limitadas. | Durante el período de solo seguridad: compatibilidad con Adobe Commerce de guardia, correcciones de calidad, actualizaciones de dependencia de la plataforma |

{style="table-layout:auto"}

>[!IMPORTANT]
>
>El período transitorio de solo seguridad es una excepción única. No se ampliará más allá de las fechas de publicación. Trate el período de solo seguridad como un tiempo de migración, no como un nivel de soporte a largo plazo.

## Dependencias de plataforma

Permanecer en una versión de Commerce compatible también requiere dependencias de plataforma compatibles. Adobe no proporciona correcciones de seguridad y calidad para servicios de terceros y dependencias de software, como PHP, MariaDB, OpenSearch, Redis, Valkey, RabbitMQ y otros, que pueden llegar al final de su vida útil mientras está en el período de soporte de tres años o ampliado para Adobe Commerce.

Usted es responsable de mantener todas las dependencias de terceros y los servicios de plataforma en versiones compatibles de forma activa. Consulte [Requisitos del sistema](../installation/system-requirements.md) para obtener la lista completa de tecnologías de terceros probadas y admitidas.

Adobe no proporciona soporte de seguridad ni asistencia para implementaciones que ejecutan versiones de dependencia no admitidas. Consulte [Modelo operativo y de seguridad de responsabilidad compartida](../security-and-compliance/shared-responsibility.md) para obtener más información.

>[!IMPORTANT]
>
>La ejecución de versiones de dependencia no admitidas puede provocar una vulnerabilidad de seguridad en la instancia de Cloud que Adobe no puede resolver. En estos casos, Adobe se reserva el derecho de aplicar una actualización de la dependencia de software afectada o de desactivar el servicio si no es posible realizar una actualización, independientemente del estado de compatibilidad con la versión de Adobe Commerce.

## Fin de vida útil de PHP y cumplimiento de PCI

Usted es responsable de monitorear el estado de soporte de las versiones de PHP usadas en sus entornos.

Las siguientes versiones de PHP usadas por las líneas de versiones de Commerce más antiguas han llegado o llegarán al final de su vida útil, lo que tiene implicaciones directas para el cumplimiento de PCI.

| Versión de PHP | Fecha de finalización de la vida útil | Versiones de Commerce afectadas | Impacto del cumplimiento de PCI |
|-------------|------------------|----------------------------|------------------------|
| PHP 8.1 | 31 de diciembre de 2025 | 2.4.4, 2.4.5 y 2.4.6 (donde se utiliza PHP 8.1) | El cumplimiento de PCI está en riesgo: ejecutar PHP 8.1 más allá de la fecha de fin de vida útil significa que las vulnerabilidades de seguridad en PHP pueden no recibir correcciones, lo que pone en riesgo el cumplimiento de PCI. Evalúe el estado de cumplimiento y dé prioridad a la actualización. |
| PHP 8.2 | 31 de diciembre de 2026 | 2.4.6 (donde se utiliza PHP 8.2) | Conformidad con PCI en riesgo desde finales de 2026: planee la actualización o migración antes de finales de 2026 para mantener la conformidad con PCI. |

{style="table-layout:auto"}

### Aviso de cumplimiento de PCI

El cumplimiento de PCI es responsabilidad del comerciante para evaluar. Adobe recomienda encarecidamente que los comerciantes de las versiones afectadas consulten con su asesor de seguridad cualificado y den prioridad a la migración a una versión de Commerce compatible y a una versión de PHP compatible lo antes posible. Para ver las cronologías de compatibilidad con PHP, consulte [Versiones compatibles con PHP](https://www.php.net/supported-versions.php) y [Fin de vida útil de PHP](https://www.php.net/eol.php).

## Opciones de actualización y migración

Si su versión se acerca a las fechas de fin de soporte o las supera, actúe ahora. Si permanece en una versión no admitida, su tienda corre el riesgo de sufrir vulnerabilidades de seguridad, problemas de cumplimiento y pérdida de compatibilidad. Adobe proporciona las siguientes rutas para pasar a una versión compatible.

### Ruta recomendada: migrar a Adobe Commerce as a Cloud Service (ACCS)

[!DNL Adobe Commerce as a Cloud Service] es la plataforma de comercio alojada de próxima generación de Adobe y el destino a largo plazo recomendado por Adobe para todos los clientes de Adobe Commerce en la nube.

- Adobe administra automáticamente toda la infraestructura, los parches y las actualizaciones.
- Siempre está en una infraestructura compatible y compatible: la situación de fin de vida útil no se repite.
- Tendrá acceso a las funciones más recientes de Adobe: comercialización con tecnología de IA, arquitectura de escaparate componible e integraciones nativas de Adobe Experience Cloud.
- Se eliminan los ciclos de actualización recurrentes.

Póngase en contacto con el equipo de su cuenta de Adobe para comenzar una evaluación de la migración. Consulte [Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview) para obtener información general del producto.

### Ruta alternativa: actualización a una versión compatible de Adobe Commerce en la nube o local

Si no puede migrar a [!DNL Adobe Commerce as a Cloud Service] inmediatamente, puede actualizar a la versión local o en la nube de Adobe Commerce más reciente que admita actualmente. Esto le lleva a una pila de infraestructura moderna y totalmente compatible, al tiempo que conserva su modelo de implementación de PaaS existente.

Tenga en cuenta que esta ruta no elimina las futuras obligaciones de actualización. Los clientes de PaaS deben seguir actualizando a medida que las líneas de versión alcanzan sus fechas de aplicación de actualización de versiones.
