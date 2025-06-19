---
title: 'ACSD-50858: rendimiento mejorado para cargar contenido de titulares'
description: Aplique el parche ACSD-50858 para corregir el problema de Adobe Commerce en el que el rendimiento del banner se ve afectado en la página del carro de compras/cierre de compra debido a consultas de base de datos excesivas y a un mayor tiempo de carga de la página.
feature: Page Content
role: Admin
exl-id: 1b46e51f-70ad-4450-b3a8-173c2e4b7925
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# ACSD-50858: rendimiento mejorado para cargar contenido de titulares

El parche ACSD-50858 corrige un problema de rendimiento del banner en la página de carrito/cierre de compra: *consultas de BD excesivas y tiempo de carga de página aumentado*. Esta revisión está disponible cuando está instalado [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.31. El ID del parche es ACSD-50858. Tenga en cuenta que el problema está programado para solucionarse en Adobe Commerce 2.4.7.

## Productos y versiones afectados

**El parche se ha creado para la versión de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.5-p1

**Compatible con versiones de Adobe Commerce:**

* Adobe Commerce (todos los métodos de implementación) 2.4.4 - 2.4.6

>[!NOTE]
>
>El parche podría ser aplicable a otras versiones con las nuevas versiones de [!DNL Quality Patches Tool]. Para comprobar si el parche es compatible con su versión de Adobe Commerce, actualice el paquete `magento/quality-patches` a la última versión y compruebe la compatibilidad en la página [[!DNL Quality Patches Tool]: buscar parches ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es). Utilice el ID de parche como palabra clave de búsqueda para localizar el parche.

## Problema

El rendimiento del banner se ve afectado en la página del carro de compras/cierre de compra debido a *consultas de BD excesivas y tiempo de carga de la página aumentado*.

Esto se solucionó refactorizando la forma en que se cargan los contenidos de los banners, lo que redujo el número de consultas de DB en un 99,99 % y el tiempo de carga de la página en ~99 %.

<u>Pasos a seguir</u>:

1. Inicie sesión en Admin y cree un producto sencillo.
1. Cree un cliente, ya sea desde Administración o desde el front-end, y añada una dirección de envío para él.
1. Mueva banners.php a la carpeta `magento_root/pub/`.
1. Genere titulares utilizando el comando `php pub/banners.php`. Generará 10.000 banners simples y 1.000 banners con reglas de venta.
1. Inicie sesión en el cliente creado anteriormente en el front-end.
1. Añadir el producto creado anteriormente al carro de compras.
1. Vaya a la página de cierre de compra (cierre de compra/carro).
1. Supervisar el tiempo de carga de la solicitud `banner/ajax/load`:

   * Sin `bin/magento dev:query-log:enable`
   * Con `bin/magento dev:query-log:enable`

     ```
     grep 'magento_banner_content' var/debug/db.log  | wc -l
     ```

<u>Resultados esperados</u>:

Disminución en el número de consultas de BD para `magento_banner_content` y el tiempo de carga de la página de carrito/cierre de compra.

<u>Resultados reales</u>:

Aumento en el número de consultas de BD para `magento_banner_content` y el tiempo de carga de la página del carro de compras/cierre de compra.

## Aplicar el parche

Para aplicar parches individuales, utilice los siguientes vínculos según el método de implementación:

* Adobe Commerce o Magento Open Source local: [[!DNL Quality Patches Tool] > Uso](/help/tools/quality-patches-tool/usage.md) en la guía [!DNL Quality Patches Tool].
* Adobe Commerce en la infraestructura de la nube: [Actualizaciones y parches > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=es) en la guía Commerce en la infraestructura de la nube.

## Más información

<u>banners.php content</u>:

```php
\Banner::class);
    $banner->setIsEnabled(
        \Magento\Banner\Model\Banner::STATUS_ENABLED
    )->setName(
        'Test Dynamic Block '.$i
    )->setTypes(
        ''
    )->setStoreContents(
        [0 => 'Dynamic Block Content '.$i]
    )->save();
}

$objectManager = \Magento\Framework\App\ObjectManager::getInstance();

/** @var \Magento\SalesRule\Model\Rule $salesRule */
$salesRule = $objectManager->create(\Magento\SalesRule\Model\Rule::class);
$salesRule->setData(
    [
        'name' => '50% Off ',
        'is_active' => 1,
        'customer_group_ids' => [\Magento\Customer\Model\GroupManagement::NOT_LOGGED_IN_ID],
        'coupon_type' => \Magento\SalesRule\Model\Rule::COUPON_TYPE_NO_COUPON,
        'conditions' => [
            [
                'type' => \Magento\SalesRule\Model\Rule\Condition\Address::class,
                'attribute' => 'base_subtotal',
                'operator' => '>',
                'value' => 0
            ]
        ],
        'simple_action' => 'by_percent',
        'discount_amount' => 50,
        'discount_step' => 0,
        'stop_rules_processing' => 1,
        'website_ids' => [
           1
        ]
    ]
);
$salesRule->save();

for ($i = 0; $i < 1000; $i++) {

    $banner = $objectManager->create(\Magento\Banner\Model\Banner::class);
    $banner->setData(
        [
            'name' => 'Get 50% Off ',
            'is_enabled' => \Magento\Banner\Model\Banner::STATUS_ENABLED,
            'types' => [], /*Any Banner Type*/
            'store_contents' => ['<img src="http://example.com/banner_40_percent_off.png" />'],
            'banner_sales_rules' => [$salesRule->getId()],
        ]
    );
    $banner->save();
}
```

## Lectura relacionada

Para obtener más información sobre [!DNL Quality Patches Tool], consulte:

* [[!DNL Quality Patches Tool] publicado: nueva herramienta para autodistribuir parches de calidad](https://experienceleague.adobe.com/es/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) en la base de conocimiento de soporte.
* [Compruebe si el parche está disponible para su problema de Adobe Commerce usando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) en la guía [!UICONTROL Quality Patches Tool].


Para obtener información sobre otros parches disponibles en QPT, consulte [[!DNL Quality Patches Tool]: Buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=es) en la guía [!DNL Quality Patches Tool].
