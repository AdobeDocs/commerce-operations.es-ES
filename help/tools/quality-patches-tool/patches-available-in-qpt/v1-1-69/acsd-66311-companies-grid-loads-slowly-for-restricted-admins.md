---
title: 'ACSD-66311: la cuadrícula de las compañías se carga lentamente para los usuarios administradores restringidos'
description: Aplique el parche ACSD-66311 para corregir el problema de Adobe Commerce en el que la cuadrícula de las empresas se carga lentamente para los usuarios administradores con acceso restringido a sitios web.
role: Admin, Developer
feature: B2B
type: Troubleshooting
source-git-commit: 841e660136354800dd9758d8c10e86c966be3a1e
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 2%

---


# ACSD-66311: la cuadrícula de las compañías se carga lentamente para los usuarios administradores restringidos

El parche ACSD-66311 corrige el problema en el que la cuadrícula de las compañías se carga lentamente para los usuarios administradores con acceso restringido al sitio web. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. El ID del parche es ACSD-66311. Este problema está programado para solucionarse en Adobe Commerce 2.4.9.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p4

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.7-p4 - 2.4.8-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

La cuadrícula de compañías se carga lentamente para los usuarios administradores con acceso restringido al sitio web.

<u>Pasos a seguir</u>:

1. Instale Adobe Commerce con **[!UICONTROL B2B features]**.
1. Cree 2 sitios web adicionales (además del sitio web principal) con tiendas/vistas:
   * Sitio web principal (creado durante la instalación)
   * Sitio web 2 → Store 2 → StoreView 2
   * Sitio web 3 → Store 3 → StoreView 3
1. Crear la función de usuario **[!UICONTROL Admins in Scope]**:
   * Ámbito: solo dos tiendas: *Sitio web principal* + *Sitio web 3/Tienda 3*.
   * Recursos: solo *Panel* + *Compañías*.
1. Cree un usuario administrador con un rol **[!UICONTROL Admins in Scope]**, por ejemplo, **administrador**.
1. Generar datos distribuidos específicos de clientes y empresas:
   1. **Clientes asignados a sitios web**

      | ID del sitio web | Número de clientes |
      |------------|---------------------|
      | 1 | 600.000 |
      | 2 | 1.500 |
      | 3 | 500 |


   1. Ejecute la siguiente consulta para comprobar la distribución:

      ```
           SELECT website_id, COUNT(*) 
           FROM customer_entity 
           GROUP BY website_id; 
      ```

   1. **Clientes asignados a empresas**

      | Número de clientes | Número de empresas |
      |---------------------|---------------------|
      | 1 | 4.500 |
      | 2 | ~1.000 |
      | ~595k | 1 |

   1. Ejecute la siguiente consulta para comprobar la distribución:

      ```
            SELECT customer_count, COUNT(*) AS number_of_companies
            FROM (
      
            SELECT id_empresa, COUNT(customer_id) AS customer_count
            DESDE empresa_avanzada_cliente_entidad
            GROUP BY id_empresa
) como subconsulta
GROUP BY customer_count
ORDER BY customer_count;
&quot;

1. Reindexe todos los datos para generar entradas en **customer_grid_plain**.
1. Inicie sesión como **administrador**.
1. Ir a **[!UICONTROL Customers]** > **[!UICONTROL Companies]**.

<u>Resultados esperados</u>:

La página se carga en menos de 1 segundo.

<u>Resultados reales</u>:

La página tarda más de 14 minutos en cargarse.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool]: herramienta de autoservicio para parches de calidad](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) en la guía Herramientas.
