---
title: Política de ciclo de vida del software
description: Obtenga información sobre las fechas clave para el fin de la compatibilidad con software para las versiones de Adobe Commerce.
source-git-commit: ffa8b957828833d2c3f9bc79c31dc3fa2c6035a5
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 5%

---


# Política del ciclo vital de Adobe Commerce

Para Adobe Commerce 2.4 y versiones posteriores:

- Para optimizar mejor nuestra política de ciclo vital, Adobe proporciona correcciones de calidad a la línea de versiones 2.4 hasta el final de la fecha de soporte de la versión PHP en la que se basa. Un cliente puede acceder a las correcciones de calidad poniéndose en contacto con [Asistencia de Adobe Commerce](https://developer.adobe.com/commerce/contributor/community/support/) o a través del autoservicio [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target=&quot;_blank&quot;} si su versión sigue siendo compatible con la calidad. Consulte la siguiente tabla para ver las fechas de fin de soporte de software para las líneas de versión de Adobe Commerce.

- Adobe proporciona correcciones de seguridad solo a través del último parche o parche de seguridad, incluso si la versión de un cliente sigue siendo apta para asistencia de calidad. A diferencia de las correcciones de calidad, las correcciones de seguridad no se pueden portar de versiones anteriores menores ni de versiones anteriores de parches dentro de versiones menores admitidas.

- Para problemas de seguridad críticos, como vulnerabilidades de cero días, el Adobe proporciona [correcciones](https://support.magento.com/hc/en-us/sections/360003869892-Known-issues-patches-attached-) para todos los clientes con una versión compatible, aunque no estén en el último parche o parche de seguridad. Es importante tener en cuenta que una corrección no es un captador global y no aborda todos los problemas de seguridad que se solucionarían actualizando a la última versión.

## Fin de la asistencia de software

| Versión | Fecha de versión | Fin de la asistencia de software<sup>1</sup> | Versión de PHP dependiente |
| -------------------------------- | ----------------- | ----------------------------------- | --------------------------- |
| Adobe Commerce 2.3 | 28 de noviembre de 2018 | 8 de septiembre de 2022<sup>2</sup> | PHP 7.3 y 7.4<sup>3</sup> |
| Adobe Commerce 2.4.0-2.4.3 | 28 de julio de 2020 | 28 de noviembre de 2022 | PHP 7.4 |
| Adobe Commerce 2.4.4-2.4.6 | 12 de abril de 2022 | 25 de noviembre de 2024 | PHP 8.1 |

<sup>1 El fin del soporte de software incluye tanto correcciones de fin de calidad como correcciones de fin de seguridad.</sup><br>
<sup>2 La fecha de finalización del soporte de software para 2.3 se ha ampliado hasta el 8 de septiembre de 2022 para permitir que los clientes tengan más tiempo de actualizar a la versión 2.4.4 que estará disponible para el público general el 8 de marzo de 2022.</sup><br>
<sup>3 2.3.0-2.3.6 dependen de PHP 7.3; 2.3.7 depende de PHP 7.4.</sup>

>[!NOTE]
>
>Consulte [Política de ciclo de vida del software](https://www.adobe.com/content/dam/cc/en/legal/terms/enterprise/pdfs/Adobe-Commerce-Software-Lifecycle-Policy.pdf).

<table>
<thead>
  <tr>
    <th colspan="2"></th>
    <th colspan="4">2022</th>
    <th colspan="4">2023</th>
    <th colspan="4">2024</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Comercio</td>
    <td>PHP</td>
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
    <td>2.4.0 - 2.4.3</td>
    <td style="text-align:center">7,4</td>
    <td colspan="3" style="background-color:#67ac68;"></td>
    <td style="background-color:#cd3c3c;">Nov</td>
    <td colspan="8" ></td>
  </tr>
  <tr>
    <td>2.4.4</td>
    <td rowspan="2" style="text-align:center">8,1</td>
    <td></td>
    <td colspan="10" style="background-color:#67ac68;">Mar</td>
    <td rowspan="2" style="background-color:#cd3c3c;">Nov</td>
  </tr>
  <tr>
    <td>2.4.5</td>
    <td colspan="2"></td>
    <td colspan="9" style="background-color:#67ac68;">Ago</td>
  </tr>
</tbody>
</table>

## Clave

<table>
  <thead>
   <tr>
    <th></th>
    <th></th>
   </tr>
  </thead>
 <tbody>
  <tr>
   <td style="background-color:#67ac68;">Admitido</td>
   <td>Versión totalmente probada por Adobe y compatible.</td>
  </tr>
  <tr>
   <td style="background-color:#cd3c3c;">Fin de la asistencia de software</td>
   <td>Versión que ha llegado al final de la asistencia de software.</td>
  </tr>
 </tbody>
</table>
