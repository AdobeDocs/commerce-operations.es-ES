---
title: Uso
description: Aprenda a utilizar la variable [!DNL Quality Patches Tool].
source-git-commit: 9e719cdf888caa3fa34f6416650e62bbf1b81175
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---

# Uso

La variable [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) ofrece parches individuales desarrollados por Adobe y la comunidad de Magento Open Source. Permite aplicar, revertir y ver información general sobre todos los parches individuales disponibles para la versión instalada de Adobe Commerce o Magento Open Source. Puede aplicar parches a los proyectos de Adobe Commerce y Magento Open Source independientemente de quién desarrolló el parche. Por ejemplo, puede aplicar un parche desarrollado por la comunidad a los proyectos de Adobe Commerce.


Observe esto [vídeo técnico](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) y aprenda a utilizar la herramienta Parche de Calidad para Adobe Commerce y Magento Open Source.

>[!INFO]
>
>Consulte [Aplicar parches individuales](#apply-individual-patches) para obtener instrucciones sobre la aplicación de parches a sus proyectos de Adobe Commerce o Magento Open Source. Consulte [Parches disponibles](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) para revisar una lista completa de parches liberados.

>[!WARNING]
>
>No se recomienda usar la variable [!DNL Quality Patches Tool] para aplicar un gran número de parches porque aumenta la complejidad del código y dificulta la actualización a una nueva versión.

## Instalar

>[!INFO]
>
>Si aún no está instalado, debe instalar [[!DNL Git]](https://github.com/git-guides/install-git) o [Parche](https://man7.org/linux/man-pages/man1/patch.1.html) antes de instalar el [!DNL Quality Patches Tool]. Agregue la variable `magento/quality-patches` Paquete de compositor a su `composer.json` archivo:

```bash
composer require magento/quality-patches
```

## Ver parches individuales

Para ver la lista de parches individuales disponibles para su versión de Adobe Commerce o Magento Open Source:

```bash
./vendor/bin/magento-patches status
```

Verá un resultado similar al siguiente:

| Id | Título | Tipo | Estado | Detalles |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC se desactiva durante las implementaciones | Opcional | No se aplica | Componentes afectados:<br> - magento/module-page-cache |
| MCLOUD-5650 | Mantener configuración de implementación después de leer el archivo | Opcional | No se aplica | Componentes afectados:<br> - magento/framework |
| MCLOUD-5684 | La paginación no funciona - product_list_limit=all | Opcional | No se aplica | Componentes afectados: - magento/module-elasticsearch |
| MCLOUD-5837 | Solución del problema del equilibrador de carga | Obsoleto | Aplicado | Sustitución recomendada: MC-1 <br> Componentes afectados: - magento/framework |
| BUNDLE-2554 | Configurar error de información de pago | Opcional | No se aplica | Componentes afectados: <br>- amzn/amazon-pay-module |
| MC-1 | Correcciones del problema 1 | Opcional | Aplicado | Componentes afectados: <br> - magento/module-cms |
| MC-2 | Correcciones del problema 2 | Opcional | No se aplica | Componentes afectados: <br> - magento/module-cms |
| MC-3 | Correcciones del problema 3 | Opcional | No se aplica | parches necesarios:<br> - MC-2 <br>Componentes afectados: <br>- magento/module-cms |
| MC-3-V2 | Corrección actualizada para la versión 3, sustituye al parche MC-3 | Opcional | N/D | Componentes afectados:  <br>- magento/module-cms |

Adobe Commerce 2.3.5.

La tabla de estado incluye:

- **Tipo**:
   - `Optional` — Todos los parches de [!DNL Quality Patches Tool] y [Parches en la nube](https://devdocs.magento.com/cloud/project/project-patch.html) son opcionales para las instalaciones de Adobe Commerce y Magento Open Source.
   - `Deprecated` — el Adobe ha desaprobado el parche individual. Si ha aplicado el parche, le recomendamos que lo revierta. La operación revertir también elimina el parche de la tabla de estado.

- **Estado**:
   - `Applied` — Se ha aplicado el parche.
   - `Not applied` — No se ha aplicado el parche.
   - `N/A` — El estado del parche no se puede definir debido a conflictos.

- **Detalles**:
   - `Affected components` — La lista de módulos afectados.
   - `Required patches` — La lista de parches que deben aplicarse para que un parche indicado funcione correctamente (dependencias).
   - `Recommended replacement` — El parche que es un reemplazo recomendado para un parche en desuso.

>[!INFO]
>
>Después de actualizar a una nueva versión de Adobe Commerce o Magento Open Source, debe volver a aplicar los parches si no se incluyen en la nueva versión. Consulte [Volver a aplicar parches después de una actualización](#re-apply-patches-after-an-upgrade).

## Aplicar parches individuales {#apply-individual-patches}

>[!WARNING]
>
>Se recomienda probar todos los parches en un entorno de ensayo o desarrollo antes de implementarlos en producción. También se recomienda realizar una copia de seguridad de los datos antes de aplicar un parche. Consulte [Hacer una copia de seguridad y revertir el sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

Para aplicar un solo parche, ejecute el siguiente comando donde `MAGETWO-XXXX` es el ID de parche especificado en la tabla de estado:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

También puede aplicar varios parches al mismo tiempo separando cada ID de parche adicional con un espacio:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

Debe limpiar la caché después de aplicar parches para ver los cambios en la aplicación Adobe Commerce:

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>Considere la posibilidad de mantener una lista de parches aplicados en una ubicación diferente. Es posible que deba volver a aplicar algunos de ellos después de actualizar a una nueva versión de Adobe Commerce o Magento Open Source. Consulte [Volver a aplicar parches después de una actualización](#re-apply-patches-after-an-upgrade).

## Revertir parches individuales

>[!WARNING]
>
>Se recomienda probar todos los parches en un entorno de ensayo o desarrollo antes de implementarlos en producción. También se recomienda realizar una copia de seguridad de los datos antes de aplicar un parche. Consulte [Hacer una copia de seguridad y revertir el sistema de archivos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

Para revertir un solo parche, ejecute el siguiente comando donde `MAGETWO-XXXX` es el ID de parche especificado en la tabla de estado:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

Además, puede revertir varios parches al mismo tiempo separando cada ID de parche adicional con un espacio:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

Para revertir todos los parches aplicados:

```bash
./vendor/bin/magento-patches revert --all
```

Debe limpiar la caché después de revertir los parches para ver los cambios en la aplicación Adobe Commerce:

```bash
./bin/magento cache:clean
```

## Obtener actualizaciones

Adobe Commerce publica periódicamente nuevos parches individuales. Debe actualizar el [!DNL Quality Patches Tool] para obtener nuevos parches individuales:

```bash
composer update magento/quality-patches
```

Vea los parches añadidos:

>[!TIP]
>
>Se muestran nuevos parches en la parte inferior de la tabla.

```bash
./vendor/bin/magento-patches status
```

## Volver a aplicar parches después de una actualización {#re-apply-patches-after-an-upgrade}

Al actualizar a una nueva versión de Adobe Commerce o Magento Open Source, debe volver a aplicar los parches si no se incluyen en la nueva versión.

Para volver a aplicar parches:

1. Actualice el [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. Abra la lista de parches aplicados anteriormente, que se recomienda en [Aplicar parches individuales](#apply-individual-patches).

1. Aplique los parches:

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   La práctica recomendada es aplicar parches de uno en uno.

1. Limpie la caché:

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >Al ejecutar el `status` , los parches incluidos en la nueva versión ya no se muestran en la tabla de parches disponibles.

## Registro

La variable [!DNL Quality Patches Tool] registra todas las operaciones en el `<Magento_root>/var/log/patch.log` archivo.
