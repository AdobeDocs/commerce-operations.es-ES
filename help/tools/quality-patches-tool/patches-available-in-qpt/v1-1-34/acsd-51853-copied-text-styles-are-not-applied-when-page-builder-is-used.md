---
title: 'ACSD-51853: los estilos de texto copiados no se aplican mediante el generador de páginas'
description: Aplique el parche ACSD-51853 para solucionar el problema de Adobe Commerce donde los estilos de texto copiados no se aplican cuando se utiliza page builder.
feature: Page Builder
role: Admin
exl-id: fda5ba6e-4786-473c-a3a2-7356aa20f5ae
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-51853: los estilos de texto copiados no se aplican mediante el generador de páginas

El parche ACSD-51853 corrige el problema de que los estilos de texto copiados no se aplican cuando se utiliza el generador de páginas. Esta revisión está disponible cuando está instalado [!DNL Quality Patches Tool (QPT)] 1.1.34. El ID del parche es ACSD-51853. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p2

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

Los estilos de texto copiados no se aplican cuando se utiliza Page Builder

<u>Pasos a seguir</u>:

1. Inicie sesión en Admin.
1. Vaya a > **contenido** > **páginas** > **Abrir cualquier página** > **Editar con el Page Builder**.
1. Arrastrar fila y *texto* de **[!UICONTROL Elements]**.
1. Copie **contenido enriquecido**, pegue ese texto en **[!UICONTROL Page Builder]**.

<u>Resultados esperados</u>

El texto copiado se pega con todos los estilos.

<u>Resultados reales</u>

El texto copiado se pega como texto sin formato y se pierden todos los estilos.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
