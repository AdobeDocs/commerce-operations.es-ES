---
title: Directiva de ciclo vital de software
description: Obtenga información sobre las fechas clave de fin de compatibilidad de software para las versiones de Adobe Commerce.
exl-id: 9ee4ecc8-d893-412a-a605-5a8606a1b9a9
source-git-commit: 3bf3c4261073ab649376bb5c7fb84ea591a09869
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 2%

---


# directiva de ciclo vital de Adobe Commerce

Para optimizar la política del ciclo vital de Adobe Commerce y satisfacer las necesidades esenciales de los clientes, Adobe ofrece un período de soporte de tres años a partir de la fecha de Disponibilidad general (GA) para cada versión y publica correcciones de calidad durante este período. Para ver las fechas y los detalles sobre el fin de la compatibilidad de software en cada versión, consulte la tabla [Fin de la compatibilidad de software](#end-of-software-support).

Durante el periodo de soporte de tres años, el cliente tiene acceso a:

- **Correcciones de calidad**: los clientes pueden obtener acceso a las correcciones de calidad poniéndose en contacto con el [Soporte técnico de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) o a través del servicio de autoservicio [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). En la tabla siguiente se describen las fechas de fin de compatibilidad de software para las líneas de versión de Adobe Commerce.

- **Correcciones de seguridad**: Adobe proporciona correcciones de seguridad mediante parches de seguridad acumulativos y [archivos de parches de seguridad aislados](versioning-policy.md#isolated-security-fixes) no acumulativos durante el período de compatibilidad de tres años.

- **Revisiones**: para problemas de seguridad críticos, como vulnerabilidades de día cero, Adobe proporciona [revisiones](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) para todos los clientes en una versión compatible, incluso si no se encuentran en la última versión de revisión o parche de seguridad. Tenga en cuenta que una revisión no es exhaustiva y no aborda todos los problemas de seguridad que se resolverían al actualizar a la última versión.

Adobe no proporciona correcciones de seguridad y calidad para servicios de terceros y dependencias de software (como PHP y MySQL) que pueden llegar al final de su vida útil mientras los clientes están en el período de soporte de tres años o ampliado para Adobe Commerce. Consulte los [requisitos del sistema](../installation/system-requirements.md) para obtener una lista completa de las tecnologías de terceros probadas y admitidas.

## Compatibilidad ampliada

Adobe recomienda a los clientes que se actualicen lo antes posible. Sin embargo, para proporcionar una mayor flexibilidad para alinearse con los planes de actualización y las necesidades comerciales, Adobe ofrece una extensión de soporte de un año sin coste adicional para los clientes de Adobe Commerce en las versiones 2.4.6. La extensión de soporte incluye parches de calidad y seguridad para la aplicación principal durante un año. La compatibilidad ampliada para las versiones de Adobe Commerce 2.4.4 y 2.4.5 finaliza en abril y agosto de 2026, según lo planificado.

>[!NOTE]
>
>La compatibilidad ampliada solo está disponible para los clientes de Adobe Commerce. No está disponible para el código base de Magento Open Source.

## Fin del soporte de software

| Versión | Disponibilidad general | Fin del soporte técnico regular<sup>1</sup> | Fin de la compatibilidad ampliada |
|----------------------|----------------------|------------------------------------|-------------------------|
| Adobe Commerce 2.4.8 | 8 de abril de 2025 | 31 de mayo de 2028 | TBD |
| Adobe Commerce 2.4.7 | 9 de abril de 2024 | 31 de mayo de 2027 | TBD |
| Adobe Commerce 2.4.6 | 14 de marzo de 2023 | 11 de agosto de 2026 | 30 de agosto de 2027 |
| Adobe Commerce 2.4.5 | 9 de agosto de 2022 | 12 de agosto de 2025 | 11 de agosto de 2026 |
| Adobe Commerce 2.4.4 | 12 de abril de 2022 | 12 de abril de 2025 | 14 de abril de 2026 |

{style="table-layout:auto"}

>[!NOTE]
>
>- <sup>1</sup> Si es cliente de Adobe Commerce, puede seguir recibiendo correcciones de seguridad y calidad durante un año adicional a través del período de soporte extendido.
>- Consulte [Política de ciclo de vida de software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

>[!IMPORTANT]
>
>No se puede garantizar el cumplimiento de PCI para los comerciantes que ejecutan la versión 2.4.6 y siguen usando PHP 8.1, que llegó al [fin de la compatibilidad en 2025](https://www.php.net/eol.php). Del mismo modo, PHP 8.2 llega al [final de su vida útil a finales de 2026](https://www.php.net/supported-versions.php), lo que crea el mismo riesgo de conformidad con PCI para los comerciantes que siguen usándolo en 2027.

## Aprovisionamiento de correcciones de seguridad adicionales para Adobe Commerce 2.4.4 y 2.4.5

Como excepción única, Adobe proporciona un período de aprovisionamiento de correcciones de seguridad ampliado para las versiones 2.4.4 y 2.4.5 de Adobe Commerce a fin de que los clientes tengan más tiempo para migrar a Adobe Commerce as a Cloud Service o actualizar a una línea de versión compatible.

Durante este período de aprovisionamiento de correcciones de seguridad, tenga en cuenta lo siguiente:

- **Solo archivo de parches de seguridad aislado**: se lanzará un archivo de parches de seguridad aislado para estas versiones según la programación de versiones. No se proporcionarán revisiones de seguridad (no se proporcionarán nuevas versiones -p) durante este período.

  Para aplicar un archivo de parches de seguridad aislado, los clientes deben estar en la última versión de parches de solo seguridad (la última versión -p) para su línea de versiones admitida, ya que las correcciones de seguridad aisladas se prueban exclusivamente en esa versión.

- **No se proporcionarán correcciones de calidad ni asistencia de ingeniería**-No se proporcionarán correcciones de errores, actualizaciones de calidad ([Herramienta Parches de calidad](../tools/quality-patches-tool/usage.md)) ni asistencia de ingeniería ([Soporte de Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)) para las versiones 2.4.4 o 2.4.5 durante este período.

- **No se garantiza el cumplimiento de PCI:**-Debido a que 2.4.4 y 2.4.5 utilizan versiones de PHP que han llegado al final de su vida útil, no se puede garantizar el cumplimiento de PCI para los comerciantes en esas versiones. Si continúa ejecutando estas versiones, puede poner en riesgo la conformidad con PCI.

Para mantener una cobertura de seguridad completa y asegurar el cumplimiento de PCI, los clientes deben actualizar a una versión compatible de Adobe Commerce lo antes posible o migrar a [Adobe Commerce as a Cloud Service](https://experienceleague.adobe.com/en/docs/commerce/cloud-service/overview).

| Versión | Disponibilidad general | Fin de la compatibilidad ampliada | Fin del aprovisionamiento de correcciones de seguridad |
|----------------------|----------------------|-------------------------|------------------------------------|
| Adobe Commerce 2.4.5 | 9 de agosto de 2022 | 11 de agosto de 2026 | Mayo de 2027 |
| Adobe Commerce 2.4.4 | 12 de abril de 2022 | 14 de abril de 2026 | Mayo de 2027 |

{style="table-layout:auto"}

>[!NOTE]
>
>Las correcciones de seguridad adicionales solo están disponibles para los clientes de Adobe Commerce y no para la base de código de Magento Open Source.


## Cronología de soporte

La cronología de soporte mapea los periodos de soporte trimestre a trimestre para cada línea de versión de Adobe Commerce. Utilice las tablas proporcionadas anteriormente en este tema para las fechas de finalización exactas.

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
    <td colspan="5" style="background-color:#FFBF00"></td>
    <td colspan="10"></td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="13" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
    <td colspan="4" style="background-color:#FFBF00"></td>
    <td colspan="9"></td>
  </tr>
  <tr>
    <td>2.4.6</td>
    <td colspan="4"></td>
    <td colspan="15" style="background-color:#67ac68;"></td>
    <td colspan="4" style="background-color:#ffd700;"></td>
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
    <tr>
   <td style="background-color:#FFBF00;"> </td>
   <td>Correcciones de seguridad extendidas</td>
  </tr>
 </tbody>
</table>
