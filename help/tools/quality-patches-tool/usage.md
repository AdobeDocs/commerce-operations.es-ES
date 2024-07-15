---
title: Uso
description: Aprenda a utilizar  [!DNL Quality Patches Tool].
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 0%

---

# Uso

[[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) ofrece parches individuales desarrollados por el Adobe y la comunidad de Magento Open Source. Permite aplicar, revertir y ver información general sobre todos los parches individuales disponibles para la versión instalada de Adobe Commerce. Puede aplicar parches a proyectos de Adobe Commerce independientemente de quién lo haya desarrollado. Por ejemplo, puede aplicar un parche desarrollado por la comunidad a proyectos de Adobe Commerce.

Vea este [vídeo técnico](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) y aprenda a utilizar la herramienta Parches de calidad para Adobe Commerce.

>[!INFO]
>
>Consulte [Aplicar parches individuales](#apply-individual-patches) para obtener instrucciones sobre cómo aplicar parches a sus proyectos de Adobe Commerce. Ver [[!DNL Quality Patches Tool]: buscar parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) para revisar una lista completa de parches publicados.

>[!WARNING]
>
>No se recomienda usar [!DNL Quality Patches Tool] para aplicar una gran cantidad de revisiones porque aumenta la complejidad del código y dificulta la actualización a una nueva versión.

## Instalar

>[!INFO]
>
>Si aún no está instalado, debe instalar [[!DNL Git]](https://github.com/git-guides/install-git) o [Patch](https://man7.org/linux/man-pages/man1/patch.1.html) antes de instalar [!DNL Quality Patches Tool]. Agregue el paquete Compositor `magento/quality-patches` a su archivo `composer.json`:

```bash
composer require magento/quality-patches
```

## Ver parches individuales

Para ver la lista de parches individuales disponibles para su versión de Adobe Commerce:

```bash
./vendor/bin/magento-patches status
```

Verá un resultado similar al siguiente:

| Id | Título | Tipo | Estado | Detalles |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC se desactiva durante las implementaciones | Opcional | No aplicado | Componentes afectados: <br> - magento/module-page-cache |
| MCLOUD-5650 | Mantener la configuración de implementación después de leer el archivo | Opcional | No aplicado | Componentes afectados: <br> - magento/framework |
| MCLOUD-5684 | La paginación no funciona - product_list_limit=all | Opcional | No aplicado | Componentes afectados: - magento/module-elasticsearch |
| MCLOUD-5837 | Corregir problema del equilibrador de carga | Obsoleto | Aplicado | Reemplazo recomendado: MC-1 <br> Componentes afectados: - magento/framework |
| PAQUETE-2554 | Establecer error de información de pago | Opcional | No aplicado | Componentes afectados: <br>- amzn/amazon-pay-module |
| MC-1 | Soluciona el problema 1 | Opcional | Aplicado | Componentes afectados: <br> - magento/module-cms |
| MC-2 | Soluciona el problema 2 | Opcional | No aplicado | Componentes afectados: <br> - magento/module-cms |
| MC-3 | Correcciones del problema 3 | Opcional | No aplicado | Revisiones necesarias: <br> - MC-2 <br>Componentes afectados: <br>- magento/module-cms |
| MC-3-V2 | Se ha actualizado la corrección del problema 3, que sustituye al parche de MC-3 | Opcional | N/D | Componentes afectados: <br>- magento/module-cms |

Adobe Commerce 2.3.5.

La tabla de estado incluye:

- **Tipo**:
   - `Optional`: todos los parches del paquete [!DNL Quality Patches Tool] y [Commerce en la guía de infraestructura en la nube > Aplicar parches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) son opcionales para las instalaciones de Adobe Commerce.
   - `Deprecated`: el Adobe ha desaprobado el parche individual. Si ha aplicado el parche, le recomendamos que lo revierta. La operación de reversión también elimina el parche de la tabla de estado.

- **Estado**:
   - `Applied`: se ha aplicado el parche.
   - `Not applied`: no se ha aplicado el parche.
   - `N/A`: el estado del parche no se puede definir debido a varios conflictos.

- **Detalles**:
   - `Affected components`: la lista de módulos afectados.
   - `Required patches`: la lista de parches que se deben aplicar para que un parche indicado funcione correctamente (dependencias).
   - `Recommended replacement`: el parche que se recomienda para reemplazar un parche obsoleto.

>[!INFO]
>
>Después de actualizar a una nueva versión de Adobe Commerce, debe volver a aplicar los parches si estos no están incluidos en la nueva versión. Ver [Volver a aplicar parches después de una actualización](#re-apply-patches-after-an-upgrade).

## Aplicar parches individuales {#apply-individual-patches}

>[!WARNING]
>
>Se recomienda probar todos los parches en un entorno de ensayo o desarrollo antes de implementarlos en producción. También se recomienda realizar una copia de seguridad de los datos antes de aplicar un parche. Consulte [Copia de seguridad y reversión del sistema de archivos, medios y base de datos](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Para aplicar un solo parche, ejecute el siguiente comando donde `MAGETWO-XXXX` es el ID de parche especificado en la tabla de estado:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

También puede aplicar varios parches al mismo tiempo separando cada ID de parche adicional con un espacio:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

Debe limpiar la caché después de aplicar los parches para ver los cambios en la aplicación de Adobe Commerce:

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>Considere la posibilidad de mantener una lista de parches aplicados en una ubicación diferente. Es posible que tenga que volver a aplicar algunos de ellos después de actualizar a una nueva versión de Adobe Commerce. Ver [Volver a aplicar parches después de una actualización](#re-apply-patches-after-an-upgrade).

## Reversión de parches individuales

>[!WARNING]
>
>Se recomienda probar todos los parches en un entorno de ensayo o desarrollo antes de implementarlos en producción. También se recomienda realizar una copia de seguridad de los datos antes de aplicar un parche. Consulte [Copia de seguridad y reversión del sistema de archivos, medios y base de datos](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Para revertir una única revisión, ejecute el siguiente comando donde `MAGETWO-XXXX` es el identificador de revisión especificado en la tabla de estado:

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

Debe limpiar la caché después de revertir los parches para ver los cambios en la aplicación de Adobe Commerce:

```bash
./bin/magento cache:clean
```

## Obtener actualizaciones

Adobe Commerce publica periódicamente nuevos parches individuales. Debe actualizar [!DNL Quality Patches Tool] para obtener nuevos parches individuales:

```bash
composer update magento/quality-patches
```

Ver los parches añadidos:

>[!TIP]
>
>Los nuevos parches de adición se muestran en la parte inferior de la tabla.

```bash
./vendor/bin/magento-patches status
```

## Volver a aplicar parches después de una actualización {#re-apply-patches-after-an-upgrade}

Al actualizar a una nueva versión de Adobe Commerce, debe volver a aplicar los parches si estos no se incluyen en la nueva versión.

Para volver a aplicar parches:

1. Actualizar [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. Abra la lista de parches aplicados anteriormente, que se recomendó en [Aplicar parches individuales](#apply-individual-patches).

1. Aplique los parches:

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   La práctica recomendada es aplicar los parches de uno en uno.

1. Limpie la caché:

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >Cuando ejecute el comando `status`, las revisiones incluidas en la nueva versión ya no se mostrarán en la tabla de revisiones disponibles.

## Registro

El [!DNL Quality Patches Tool] registra todas las operaciones en el archivo `<Magento_root>/var/log/patch.log`.
