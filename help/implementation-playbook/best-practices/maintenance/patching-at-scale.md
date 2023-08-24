---
title: Prácticas recomendadas para distribuir parches a escala
description: Descubra cómo la aplicación centralizada de parches para Adobe Commerce puede ayudarle a administrar proyectos empresariales.
role: Developer
feature: Best Practices
badge: label="Colaboró Anton Evers, arquitecto técnico senior, Adobe" type="Informative" url="https://www.linkedin.com/in/anton-evers/" tooltip="Colaboró Anton Evers"
source-git-commit: d8ee656b4b1741b39f2eef1f5628a299377e774c
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 0%

---


# Prácticas recomendadas para distribuir parches de Adobe Commerce a escala

Si administra varias instalaciones de Adobe Commerce, [remiendo](../../../upgrade/patches/apply.md) puede ser un proceso complejo. _Parches centralizados_ es una parte esencial de [arquitectura de referencia global](../../architecture/global-reference.md) y una práctica recomendada para las empresas. Le ayuda a aplicar los parches adecuados en todas las instalaciones de Adobe Commerce. En este tema se explica cómo lograr la distribución centralizada de parches para todos los tipos de Adobe Commerce [parches](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>El siguiente contenido se publicó originalmente en el [Distribución de parches de Adobe Commerce a escala](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) Publicación en el Adobe Tech Blog. Se ha modificado para centrarse en los pasos y ejemplos de código para implementar una estrategia centralizada de aplicación de parches. Consulte la publicación original para obtener más detalles sobre los distintos tipos de parches que se describen aquí.

## Productos y versiones afectados

[Todas las versiones compatibles](../../../release/versions.md) de:

- Adobe Commerce en la infraestructura en la nube
- Adobe Commerce local

## Estrategia

Dado que hay muchos tipos diferentes de parches y muchas maneras de aplicarlos, ¿cómo sabe qué parche se aplica primero? Cuantos más parches tenga, mayores serán las posibilidades de que se apliquen al mismo archivo o a la misma línea de código. Los parches se aplican en el siguiente orden:

1. **Parches de seguridad** forman parte de la base de código estático de una versión de Adobe Commerce.
1. **Parches del Compositor** mediante `composer install` y `composer update` complementos como [cweagans/composer-patch](https://packagist.org/packages/cweagans/composer-patches).
1. Todo **parches necesarios** incluido en el [Parches de nube para Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html) paquete.
1. Seleccionado **parches de calidad** incluido en el [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md).
1. **Parches personalizados** y los parches de Soporte de Adobe Commerce en `/m2-hotfixes` en orden alfabético por nombre de parche.

   >[!IMPORTANT]
   >
   >Cuantos más parches aplique, más complejo se volverá su código. El código complejo puede dificultar la actualización a una nueva versión de comercio de Adobe y aumentar el coste total de propiedad.

Si es responsable de mantener varias instalaciones de Adobe Commerce, garantizar que todas las instancias tengan el mismo conjunto de parches instalados puede ser complicado. Cada instalación tiene su propio repositorio de Git, `/m2-hotfixes` directorio, y `composer.json` archivo. La única garantía que tiene es que la **parches de seguridad** y **parches necesarios** para usuarios en la nube se instalan como parte de su versión principal de Adobe Commerce.

En la actualidad, no existe una solución centralizada para este problema, pero Composer ofrece una forma de salvar la brecha. El [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) El paquete de permite [aplicación de parches desde dependencias](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). Puede crear un paquete Composer que instale todos sus parches y luego requerir ese paquete en todos sus proyectos.

Eso cubre **parches de seguridad**, **parches necesarios**, y **Parches del Compositor**, pero ¿qué pasa con los parches de calidad y el contenido de la `/m2-hotfixes` directorio?

## Aplicar parches y revisiones de calidad

Puede instalar parches de calidad tanto en la infraestructura en la nube como en las instalaciones locales utilizando `vendor/bin/magento-patches apply` comando. Debe asegurarse de que la variable `vendor/bin/magento-patches apply` El comando se ejecuta después de `composer install` operaciones.

>[!NOTE]
>
>En la infraestructura en la nube, también puede instalar parches de calidad enumerándolos en el `.magento.env.yaml` archivo. El ejemplo descrito aquí requiere el uso de `vendor/bin/magento-patches apply` comando.

Puede especificar los parches que desea aplicar en la `composer.json` de un paquete de componentes del Compositor personalizado y, a continuación, cree un paquete de complementos que ejecute el comando después de que `composer install` operaciones.

En resumen, este ejemplo de aplicación centralizada de parches requiere la creación de dos paquetes personalizados de Composer:

- **Paquete de componentes:** `centralized-patcher`

   - Define la lista de parches de calidad y `m2-hotfixes` para instalar
   - Requiere el `centralized-patcher-composer-plugin` paquete, que ejecuta el `vendor/bin/magento-patches apply` comando después `composer install` operaciones

- **Paquete de complemento:** `centralized-patcher-composer-plugin`

   - Define una `CentralizedPatcher` Clase PHP que lee la lista de parches de calidad de la `centralized-patcher` paquete
   - Ejecuta el `vendor/bin/magento-patches apply` para instalar la lista de parches de calidad después de `composer install` operaciones

### `centralized-patcher`

Puede crear un paquete de componentes Composer (`centralized-patcher`) para gestionar de forma centralizada todos los parches de calidad y `/m2-hotfixes` en todas las instalaciones de Adobe Commerce.

El paquete de componentes debe:

- Copie el contenido del `/m2-hotfixes` en todas las instalaciones durante la implementación.
- Defina la lista de parches de calidad que desea instalar.
- Ejecute el `vendor/bin/magento-patches` para instalar la misma lista de parches de calidad en todas las instalaciones (utilizando el comando [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) paquete de complemento como dependencia).

Para crear el `centralized-patcher` paquete de componentes:

1. Crear un `composer.json` archivo con el siguiente contenido:

   >[!NOTE]
   >
   >El `require` en el ejemplo siguiente muestra un atributo `require` dependencia del [paquete de complemento](#centralized-patcher-composer-plugin) que debe crear más adelante en este ejemplo.

   ```json
   {
    "name": "magento-services/centralized-patcher",
    "version": "0.0.1",
    "description": "Centralized patcher for patching multiple web stores from a central place",
    "type": "magento2-component",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "magento-services/centralized-patcher-composer-plugin": "~0.0.1"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "extra": {
        "map": [
        ],
   }
   ```

1. Crear un `/m2-hotfixes` dentro del paquete y agréguelo al `map` en su `composer.json` archivo. El `map` contiene archivos para copiar de este paquete en la raíz del proyecto de destino al que desea aplicar el parche.

   ```json
   {
    ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
   }
   ```

   >[!NOTE]
   >
   >El `centralized-patcher` copia el contenido del paquete `/m2-hotfixes` en el directorio m2-hotfixes del proyecto de target en `composer install`.  Dado que los scripts de implementación en la nube aplican revisiones m2 después de `composer install`, todas las revisiones se instalan mediante el mecanismo de implementación.

1. Defina los parches de calidad que desea instalar en `quality-patches` atributo.

   ```json
   {
   ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
        "quality-patches": [
            "MDVA-30106",
            "MDVA-12304"
        ]
   }
   ```


El `quality-patches` en el ejemplo de código anterior contiene dos parches de la variable [lista completa de parches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) como ejemplo.  Estos parches de calidad se instalan en todos los proyectos que requieren la `centralized-patcher` paquete con el `vendor/bin/magento-patches apply` comando.

Para realizar pruebas, puede crear un parche de ejemplo (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`).

>[!NOTE]
>
>Debe colocar sus propios parches en la `m2-hotfixes` junto con los parches que recibe directamente del Soporte de Adobe Commerce.

Un archivo de parche de ejemplo (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`):

```diff
diff --git a/vendor/magento/framework/Mview/View/Subscription.php b/vendor/magento/framework/Mview/View/Subscription.php
index 03a3bf9..681e0b0 100644
--- a/vendor/magento/framework/Mview/View/Subscription.php
+++ b/vendor/magento/framework/Mview/View/Subscription.php
@@ -16,6 +16,7 @@ use Magento\Framework\Mview\ViewInterface;
 
 /**
  * Mview subscription.
+ * Test Patch File
  */
 class Subscription implements SubscriptionInterface
 {
```

### `centralized-patcher-composer-plugin`

Dado que este ejemplo utiliza el método local para instalar parches de calidad, debe asegurarse de que la variable `vendor/bin/magento-patches apply` El comando se ejecuta después de `composer install` operaciones. Este complemento se activa después de `composer install` operaciones, que ejecuta el `vendor/bin/magento-patches apply` comando.

Para crear el `centralized-patcher-compose-plugin` paquete de componentes:

1. Crear un `composer.json` archivo con el siguiente contenido:

   ```json
   {
    "name": "magento-services/centralized-patcher-composer-plugin",
    "version": "0.0.1",
    "description": "Centralized patcher composer plugin to apply quality patches from the centralized patcher",
    "type": "composer-plugin",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "symfony/process": "^4.1 || ^5.1",
        "magento/magento-cloud-patches": "~1.0.20",
        "magento/framework": "~103.0.5-p1",
        "composer-plugin-api": "^2.0"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "suggest": {
        "magento-services/centralized-patcher": "~0.0.1"
    },
    "autoload": {
        "psr-4": {
            "MagentoServices\\CentralizedPatcherComposerPlugin\\": ""
        }
    },
    "extra": {
        "class": "MagentoServices\\CentralizedPatcherComposerPlugin\\Patcher"
    }
   }
   ```

1. Cree un archivo PHP y defina un `CentralizedPatcher` para leer la lista de parches de calidad del [`centralized-patcher`](#centralized-patcher) paquete de componentes e instálelos inmediatamente después de cada `composer install` operación.

   ```php
   <?php
   declare(strict_types=1);
   
   namespace MagentoServices\CentralizedPatcherComposerPlugin;
   
   use Composer\Composer;
   use Composer\EventDispatcher\EventSubscriberInterface;
   use Composer\IO\IOInterface;
   use Composer\Plugin\PluginInterface;
   use Composer\Script\ScriptEvents;
   use Symfony\Component\Process\Exception\ProcessFailedException;
   use Symfony\Component\Process\Process;
   
   class Patcher implements PluginInterface, EventSubscriberInterface
   {
    /**
     * @var Composer $composer
     */
    protected $composer;
   
    /**
     * @var IOInterface $io
     */
    protected $io;
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function activate(Composer $composer, IOInterface $io)
    {
        $this->composer = $composer;
        $this->io = $io;
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function deactivate(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function uninstall(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @return string[]
     */
    public static function getSubscribedEvents()
    {
        return [
            ScriptEvents::POST_UPDATE_CMD => 'installPatches',
            ScriptEvents::POST_INSTALL_CMD => 'installPatches',
        ];
    }
   
    /**
     * Apply patches from magento-services/centralized-patcher
     *
     * @param \Composer\Script\Event $event
     * @return void
     */
    public function installPatches(\Composer\Script\Event $event)
    {
        $patches = [];
        $this->io->write('Applying centralized quality patches');
        $packages = $this->composer->getLocker()->getLockData()['packages'];
        foreach ($packages as $package) {
            if ($package['name'] !== 'magento-services/centralized-patcher') {
                continue;
            }
            $patches = $package['extra']['quality-patches'] ?? [];
        }
        if (empty($patches)) {
            $this->io->error("No centralized quality patches to install");
            exit(0);
        }
        $command = array_merge(
            ['php','./vendor/bin/magento-patches','apply','--no-interaction'],
             $patches
        );
        $process = new Process($command);
        try {
            $this->io->debug($process->getCommandLine());
            $process->mustRun();
            $this->io->write(
                str_replace("\n\n", "\n", trim($process->getErrorOutput() ?: $process->getOutput(), "\n"))
            );
        } catch (ProcessFailedException $e) {
            $process = $e->getProcess();
            $error = sprintf(
                'The command "%s" failed. %s',
                $process->getCommandLine(),
                trim($process->getErrorOutput() ?: $process->getOutput(), "\n")
            );
            throw new \RuntimeException($error, $process->getExitCode());
        }
    }
   }
   ```

>[!TIP]
>
>Consulte la [ejemplos de código](#code-examples) para ver los dos paquetes descritos en este ejemplo en acción.


## Qué hacer con los parches específicos del proyecto

Es posible que tenga un escenario en el que solo se requiera el 95% de los parches en todos los proyectos, mientras que algunos parches se aplican solo a una instancia específica. La forma habitual de aplicar parches sigue funcionando. Puede mantener parches específicos del proyecto en la variable `/m2-hotfixes` e instale parches de calidad por proyecto.

Si utiliza este método, **no** confirme cualquier parche en el `/m2-hotfixes` que ha copiado en su proyecto el `centralized-patcher` paquete de componentes. Puede evitar confirmaciones accidentales añadiendo `/m2-hotfixes` a su `.gitignore` archivo. Después de actualizar el `.gitignore` , recuerde que cualquier proyecto específico de `/m2-hotfixes` debe añadirse utilizando la variable `git add –force` comando.

## Ejecución de diferentes versiones de Adobe Commerce

Asegúrese de establecer la dependencia correcta en la variable `centralized-patcher` paquete de componentes. Por ejemplo, puede que necesite Adobe Commerce 2.4.5-p2 para una versión específica del paquete, que solo proporciona parches compatibles con Adobe Commerce 2.4.5-p2. Puede tener otra versión de este paquete compatible con Adobe Commerce 2.4.4.

## Comprensión del resultado

Al igual que con Adobe Commerce en la infraestructura en la nube, este artículo supone que el proceso de implementación utiliza la variable `composer install` comando y no `composer update` o `git pull` para implementar código nuevo en los servidores. El flujo de instalación centralizada de parches tendrá el siguiente aspecto:

1. Instalación del Compositor

   - Instala Adobe Commerce, incluidos los parches funcionales y de seguridad -p1 o -p2
   - Combinaciones centralizadas `/m2-hotfixes` y admite parches con características específicas del proyecto `/m2-hotfixes` y parches de asistencia
   - Aplica los parches instalados con el `cweagans/composer-patches` Paquete Composer

1. Después `composer install`

   - El complemento Composer instala parches de calidad centralizados

1. Implementación

   - Los parches necesarios y los parches de calidad específicos del proyecto se instalan en función de la `.magento.env.yaml` (solo proyectos de infraestructura de Adobe Commerce en la nube).
   - Parches personalizados y parches de asistencia de `/m2-hotfixes` Los directorios de se instalan en orden alfabético por nombre de parche.

De este modo, puede gestionar de forma centralizada todos sus parches para todas sus instalaciones y garantizar mejor la seguridad y estabilidad de sus tiendas Adobe Commerce. Utilice los siguientes métodos para comprobar el estado del parche:

- [Proyectos de infraestructura en nube](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [Proyectos locales](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## Ejemplos de código

- [Parches centralizados en Magento Open Source](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Revisiones centralizadas en Adobe Commerce en la infraestructura en la nube](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Complemento Compositor de parches centralizado](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [Componente de parche centralizado](https://github.com/AntonEvers/centralized-patcher)
