---
title: Acuerdos de nivel de servicio
description: Obtenga información sobre los acuerdos de nivel de servicio y cómo utilizarlos para admitir la implementación de Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 1%

---


# Acuerdos de nivel de servicio (SLA)

El acuerdo de nivel de servicio (SLA) define el nivel de servicio que espera un cliente del proveedor de servicios, con métricas sencillas mediante las cuales se mide dicho servicio, así como los remedios o penalizaciones, si los hubiera, en caso de que no se alcancen los niveles de servicio acordados.

Se pueden contratar, mantener y medir los SLAs para diferentes tipos de criticidad de incidentes. Además, el tipo de respuesta puede tener múltiples estándares (Gold, Platinum), según el nivel de servicio requerido por el cliente.

En la tabla siguiente se describe un desglose de métrica de SLA típico con varios niveles de servicio:

<table>
<thead>
  <tr>
    <th>Tipo de problema</th>
    <th>Impacto</th>
    <th>Ejemplo</th>
    <th colspan="2">Tiempo de respuesta/restauración durante el horario laboral admitido</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="3"></td>
    <td>Gold</td>
    <td>Platino</td>
  </tr>
  <tr>
    <td>P1</td>
    <td>Impacto crítico</td>
    <td>Servicio inactivo o inutilizable</td>
    <td>1 hora/4 horas</td>
    <td>1 hora / 4 horas</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>El servicio no está disponible</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>El servicio no se puede utilizar en toda la base de usuarios finales</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P2</td>
    <td>Impacto alto</td>
    <td>Servicio gravemente afectado</td>
    <td>2 horas / 12 horas</td>
    <td>2 horas / 8 horas</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>El rendimiento del servicio está degradado</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Servicio disponible, pero que produce mensajes de error significativos</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>P3</td>
    <td>Impacto medio</td>
    <td>Servicio parcialmente deteriorado</td>
    <td>8 horas / 16 horas</td>
    <td>8 horas / 12 horas</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Mensajes de error generados, sin impacto visible en el usuario final</td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Preguntas sobre las funciones utilizadas en el lanzamiento de clientes</td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>

## Opciones de cobertura

Las opciones de cobertura para los SLAs comprometidos varían según los diferentes tipos de oferta. Normalmente, el alcance de los servicios de soporte Gold y Platinum se parece a lo siguiente:

![Infografía que muestra las opciones de cobertura de SLA](../../assets/playbooks/sla-coverage-options.svg)
