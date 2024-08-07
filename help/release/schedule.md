---
title: Programación de versiones
description: Descubra cuándo Adobe tiene previsto anunciar lanzar nuevas funciones de Adobe Commerce.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: e9ef167f5425407f6b1850f0dd913d5d3e2bd628
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 2%

---

# Programación de versiones

El Adobe se esfuerza continuamente por encontrar el equilibrio adecuado entre hacer que las actualizaciones de productos sean sencillas y predecibles, al tiempo que ofrece mejoras y nuevas características a los usuarios que las adoptaron por primera vez más rápido (consulte [directiva de versiones](versioning-policy.md)). El propósito de esta programación es proporcionar fechas para cuándo Adobe planea anunciar el lanzamiento de nuevas funciones sustanciales. Estas características pueden variar a lo largo del año. Sin embargo, Adobe publica de forma regular y continua mejoras para las herramientas de extensibilidad, la infraestructura y los productos SaaS (servicios) entre las fechas especificadas en esta página.

Versiones de Adobe [parches](versioning-policy.md#patch-release) para cada línea de versión compatible de la aplicación principal de Adobe Commerce PHP. Las versiones de parches son oportunidades para actualizar la base de código principal a fin de mantener la seguridad, la fiabilidad y el rendimiento de su plataforma. Las características son independientes del código base y están disponibles a través de [módulo, extensión, herramienta o servicio web externo](versioning-policy.md#extensibility-infrastructure-and-services-release).

>[!NOTE]
>
>A partir de 2024, Adobe ya no proporciona acceso previo al lanzamiento a los parches. En su lugar, para 2.4.7 y versiones posteriores, los clientes de Adobe Commerce pueden utilizar [versiones beta](beta.md) para acceder al código de disponibilidad general previo con fines de prueba y desarrollo.

La siguiente tabla proporciona las fechas de los lanzamientos programados (las fechas están sujetas a cambios):

<table>
<thead>
  <tr>
    <th>Disponibilidad general</th>
    <th>Funciones</th>
    <th>PHP Core</th>
  </tr>
</thead>
<tfoot>
   <tr>
      <td colspan="3"><strong>Leyenda</strong>
         <ul>
           <li><strong><img alt="Icono de función B2B" src="../assets/icons/enterprise.svg"></img> B2B</strong>: nuevas funciones, mejoras y correcciones de errores para la extensión B2B para Adobe Commerce. Para obtener más información sobre las versiones de la extensión B2B, consulte las <a href="https://experienceleague.adobe.com/docs/commerce-admin/b2b/release-notes.html">Notas de la versión B2B</a>.</li>
            <li><strong><img alt="Icono de función de extensibilidad" src="../assets/icons/brackets.svg"></img> Extensibility</strong>: nuevas herramientas y servicios para desarrolladores para la extensibilidad fuera de proceso que se entregan independientemente de las versiones de parches. Por ejemplo, el SDK de la IU de administración, los eventos de Adobe I/O para Commerce y la malla de la API.</li>
            <li><strong><img alt="Icono de función Infraestructura" src="../assets/icons/servers.svg"></img> Infrastructure</strong>: nuevas funciones y mejoras en Adobe Commerce en la infraestructura en la nube y en los paquetes de Cloud Tools Suite para Commerce, diseñados para implementar y administrar las instalaciones y actualizaciones de Adobe Commerce en la plataforma en la nube.</li>
            <li><strong><img alt="Icono de revisión" src="../assets/icons/file-code.svg"></img> parches</strong>: actualizaciones de la aplicación principal de Adobe Commerce PHP que incluyen correcciones de seguridad, conformidad, rendimiento y calidad de alta prioridad.</li>
            <li><strong><img alt="Icono de funcionalidad Servicios" src="../assets/icons/feature.svg"></img> Services</strong>: nuevas funciones de SaaS que se entregan independientemente de las versiones de parches. Por ejemplo, Servicio de catálogo, Live Search y Recommendations de producto.</li>
         </ul>
      </td>
   </tr>
</tfoot>
<tbody>
  <tr>
    <td>13 de febrero de 2024</td>
    <td><img alt="Icono de función de extensibilidad" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Extensibilidad</a><br><img alt="Icono de función Infraestructura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infraestructura</a><br><img alt="Icono de funcionalidad Servicios" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Servicios</a></td>
    <td><img alt="Icono de revisión" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Parches de seguridad</a>: 2.4.6-p4, 2.4.5-p6, 2.4.4-p7</td>
  </tr>
  <tr>
    <td>12 de marzo de 2024</td>
    <td>—</td>
    <td><img alt="Icono de revisión" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">parche de Beta</a>: 2.4.7-beta3</td>
  </tr>
  <tr>
    <td>9 de abril de 2024</td>
    <td><img alt="Icono de función de extensibilidad" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Extensibilidad</a><br><img alt="Icono de función Infraestructura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infraestructura</a><br><img alt="Icono de funcionalidad Servicios" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Servicios</a></td>
    <td><img alt="Icono de revisión" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md"><strong>Adobe Commerce 2.4.7</a></strong>:<ul><li>Mejoras de rendimiento</li><li>Mejoras de calidad</li><li>Mejoras de seguridad</li><li>Actualizaciones de dependencias de terceros</li></ul><img alt="Icono de revisión" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Parches de seguridad</a>: 2.4.6-p5, 2.4.5-p7, 2.4.4-p8</td>
  </tr>
  <tr>
    <td>11 de junio de 2024</td>
    <td><img alt="Icono de función de extensibilidad" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Extensibilidad</a><br><img alt="Icono de función Infraestructura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infraestructura</a><br><img alt="Icono de funcionalidad Servicios" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Servicios</a></td>
    <td><img alt="Icono de revisión" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Parches de seguridad</a>: 2.4.7-p1, 2.4.6-p6, 2.4.5-p8, 2.4.4-p9</td>
  </tr>
  <tr>
    <td>13 de agosto de 2024</td>
    <td><img alt="Icono de función de extensibilidad" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Extensibilidad</a><br><img alt="Icono de función Infraestructura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infraestructura</a><br><img alt="Icono de funcionalidad Servicios" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Servicios</a></td>
    <td><img alt="Icono de revisión" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Parches de seguridad</a>: 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10</td>
  </tr>
  <tr>
    <td>8 de octubre de 2024</td>
    <td><img alt="Icono de función de extensibilidad" src="../assets/icons/brackets.svg"></img> <a href="https://developer.adobe.com/commerce/extensibility/">Extensibilidad</a><br><img alt="Icono de función Infraestructura" src="../assets/icons/servers.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-tools-suite.html">Infraestructura</a><br><img alt="Icono de funcionalidad Servicios" src="../assets/icons/feature.svg"></img> <a href="https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/release-information/release-notes-all.html">Servicios</a></td>
    <td><img alt="Icono de revisión" src="../assets/icons/file-code.svg"></img> <a href="release-notes/commerce/overview.md">parche de Beta</a>: 2.4.8-beta1<br><img alt="Icono de revisión" src="../assets/icons/file-code.svg"></img> <a href="release-notes/security/overview.md">Parches de seguridad</a>: 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11</td>
  </tr>
</tbody>
</table>
