---
title: Directiva de ciclo vital de software
description: Obtenga información sobre las fechas clave de fin de compatibilidad de software para las versiones de Adobe Commerce.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 5a45f2b0ad2485014abd3b807a5797f9fc82388b
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 3%

---


# directiva de ciclo vital de Adobe Commerce

Para Adobe Commerce 2.4.4 y versiones posteriores:

- Para optimizar la política del ciclo vital de Adobe Commerce y satisfacer las necesidades esenciales de los clientes, Adobe amplió el período de asistencia a tres años desde la fecha de Disponibilidad general (GA) para Adobe Commerce 2.4.4 y versiones posteriores. Adobe proporciona correcciones de calidad a la versión 2.4.4 y posteriores para un periodo de compatibilidad de tres años. Los clientes pueden acceder a las correcciones de calidad poniéndose en contacto con el [Soporte técnico de Adobe Commerce](https://experienceleague.adobe.com/es/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) o a través del autoservicio [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) si su versión sigue siendo elegible para el soporte de calidad. En la tabla siguiente se describen las fechas de fin de compatibilidad de software para las líneas de versión de Adobe Commerce.

- Adobe proporciona correcciones de seguridad mediante una versión de parche de seguridad para el periodo de compatibilidad de tres años.

- Para problemas de seguridad críticos, como vulnerabilidades de día cero, Adobe proporciona [revisiones](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) para todos los clientes en una versión compatible, incluso si no se encuentran en la última versión de revisión o parche de seguridad. Tenga en cuenta que una revisión no es exhaustiva y no aborda todos los problemas de seguridad que se resolverían al actualizar a la última versión.

- Adobe no proporciona correcciones de seguridad y calidad para servicios de terceros y dependencias de software (como PHP y MySQL) que pueden llegar al final de su vida útil mientras los clientes están en el período de soporte de tres años para Adobe Commerce. Consulte los [requisitos del sistema](../installation/system-requirements.md) para obtener una lista completa de las tecnologías de terceros probadas y admitidas.

- Para los clientes de Adobe Commerce en la nube que utilizan las versiones 2.4.4 y 2.4.5, Adobe aplica automáticamente correcciones de seguridad de duración de PHP 8.1 a la infraestructura, por lo que estos clientes no se ven afectados por el fin de soporte de PHP 8.1. Los clientes locales que utilicen Adobe Commerce 2.4.4 y 2.4.5 deben ponerse en contacto con el servicio de asistencia de Adobe para solicitar los parches de seguridad de duración de PHP 8.1 si es necesario.

- Adobe proporciona compatibilidad con servicios de terceros y dependencias de software mientras los clientes están en el período de compatibilidad de tres años para Adobe Commerce en el ámbito de las versiones de parches solo de seguridad, pero solo cuando es posible hacerlo sin introducir cambios incompatibles con versiones anteriores.

## Compatibilidad ampliada

Adobe recomienda a los clientes que se actualicen lo antes posible. Sin embargo, para proporcionar una mayor flexibilidad para alinearse con los planes de actualización y las necesidades comerciales, Adobe ofrece una extensión de soporte de un año sin coste adicional para los clientes de Adobe Commerce en las versiones 2.4.4 y 2.4.5. La extensión de soporte incluye parches de calidad y seguridad para la aplicación principal durante un año.

>[!NOTE]
>
>La compatibilidad ampliada solo está disponible para los clientes de Adobe Commerce. No está disponible para el código base de Magento Open Source.

## Fin del soporte de software

| Versión | Disponibilidad general | Fin del soporte técnico regular<sup>1</sup> | Fin de la compatibilidad ampliada | Versión de PHP dependiente | Versión de MariaDB dependiente |
|----------------------|----------------------|------------------------------------|-------------------------|-----------------------|---------------------------|
| Adobe Commerce 2.4.8 | 8 de abril de 2025 | 11 de abril de 2028 | N/D | 8.3 y 8.4 | 11,4 |
| Adobe Commerce 2.4.7 | 9 de abril de 2024 | 9 de abril de 2027 | N/D | 8.2 y 8.3 | 10.11<sup>3</sup> |
| Adobe Commerce 2.4.6 | 14 de marzo de 2023 | 11 de agosto de 2026<sup>2</sup> | N/D | 8.1 y 8.2 | 10.11<sup>4</sup> |
| Adobe Commerce 2.4.5 | 9 de agosto de 2022 | 9 de agosto de 2025 | 11 de agosto de 2026 | 8,1 | 10,6<sup>5</sup> |
| Adobe Commerce 2.4.4 | 12 de abril de 2022 | 12 de abril de 2025 | 14 de abril de 2026 | 8,1 | 10,6<sup>6</sup> |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> El fin de la compatibilidad con software incluye tanto el fin de las correcciones de calidad como el fin de las correcciones de seguridad.
>- <sup>2</sup> se ha actualizado para alinearse con el final de la compatibilidad ampliada para 2.4.5.
>- <sup>3</sup> a partir de la revisión de seguridad 2.4.7-p6.
>- <sup>4</sup> a partir del parche de seguridad 2.4.6-p11.
>- <sup>5</sup> a partir del parche de seguridad 2.4.5-p11.
>- <sup>6</sup> a partir del parche de seguridad 2.4.4-p12.
>- Consulte [Política de ciclo de vida de software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

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
  </tr>
  <tr>
    <td>2.4.4</td>
    <td></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.7</td>
    <td colspan="9"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="6"></td>
  </tr>
  <tr>
    <td>2.4.8</td>
    <td colspan="13"></td>
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
 </tbody>
</table>
